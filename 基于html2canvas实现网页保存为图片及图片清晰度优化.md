# 基于html2canvas实现网页保存为图片及图片清晰度优化
> 本次技术调研来源于H5项目中的一个重要功能需求：实现微信长按网页保存为截图。<br/>
这里有个栗子（请用微信打开，长按图片即可保存）：3分钟探索你的知识边界<br/>
将整个网页保存为图片是一个十分有趣的功能，常见于H5活动页的结尾页分享。以下则是项目中调研和踩坑的一些小结和汇总。

## 一、实现HTML页面保存为图片

### 1.1 已知可行方案

现有已知能够实现网页保存为图片的方案包括：

- 方案1：将DOM改写为canvas，然后利用canvas的toDataURL方法实现将DOM输出为包含图片展示的data URI
- 方案2：使用html2canvas.js实现（可选搭配Canvas2Image.js实现网页保存为图片）
- 方案3：使用rasterizeHTML.js实现

### 1.2 解决方案的选择

- **方案1**：需要手动计算每个DOM元素的Computed Style，然后需要计算好元素在canvas的大小位置等属性。
**方案1难点**：
1. 相当于完全重写了整个页面的布局样式，增加了工作量。
2. 由于canvas中没有的对象概念，对于元素丰富、布局复杂的页面，不易重构。
3. 所有DOM元素改写进canvas会带来一些困难，例如：难以支持响应式，图片元素清晰度不佳和文字点击区域识别问题等。
- **方案2**：该类功能中Github上stars最多(至今仍在维护)，Stack Overflow亦有丰富的讨论。只需简单调用html2canvas方法并设定配置项即可。
- **方案3**：该方案的限制较多，目前仅支持3类可转为canvas的目标格式: 页面url，html字符串和document对象。
**小结**: html2canvas是目前实现网页保存为图片功能的综合最佳选择。

### 1.3 html2canvas的使用方法

> https://github.com/niklasvh/html2canvas

以下描述针对html2canvas版本是0.5.0-beta4

#### 1.3.1 实现保存为图片的第一步：html转为canvas
基于html2canvas.js可将一个元素渲染为canvas，只需要简单的调用html2canvas(element[, options]);即可。下列html2canvas方法会返回一个包含有<canvas>元素的promise：
```
html2canvas(document.body).then(function(canvas) {
    document.body.appendChild(canvas);
});
```
#### 1.3.2 实现保存为图片的第二步：canvas转image
上一步生成的canvas即为包含目标元素的<canvas>元素对象。实现保存图片的目标只需要将canvas转image即可。

这里的转换方案有2种：

- **方案1**：基于原生canvas的toDataURL方法将canvas输出为data: URI类型的图片地址，再将该图片地址赋值给<image>元素的src属性即可
- **方案2**：使用第三方库Canvas2Image.js，调用其convertToImage方法即可（GitHub）
实际上，Canvas2Image.js也是基于canvas.toDataURL的封装，相比原生的canvas API对于转为图片的功能上考虑更为具体(未压缩的包大小为7.4KB)，适合项目使用。

## 二、生成图片的清晰度优化方案
### 2.1 基础的清晰度优化方案
> 最终图片的清晰度取决于第一步中html转换成的canvas的清晰度。

**现有解决方案参考；**

> html5 canvas在高倍屏下变模糊的处理办法<br/>
html5 canvas绘制图片模糊的问题
**其基本原理为：**
将canvas的属性width和height属性放大为2倍（或者设置为devicePixelRatio倍），最后将canvas的CSS样式width和height设置为原先1倍的大小。

**例如**：希望在html中实际显示的<canvas>宽高分别为160px,90px则可作如下设置
```
<canvas width="320" height="180" style="width:160px;height:90px;"></canvas>
```
参考上述文档具体的使用案例如下；
```
convert2canvas() {
 
    var shareContent = YourTargetElem; 
    var width = shareContent.offsetWidth; 
    var height = shareContent.offsetHeight; 
    var canvas = document.createElement("canvas"); 
    var scale = 2; 
 
    canvas.width = width * scale; 
    canvas.height = height * scale; 
    canvas.getContext("2d").scale(scale, scale); 
 
    var opts = {
        scale: scale, 
        canvas: canvas, 
        logging: true, 
        width: width, 
        height: height 
    };
    html2canvas(shareContent, opts).then(function (canvas) {
        var context = canvas.getContext('2d');
 
        var img = Canvas2Image.convertToImage(canvas, canvas.width, canvas.height);
 
        document.body.appendChild(img);
        $(img).css({
            "width": canvas.width / 2 + "px",
            "height": canvas.height / 2 + "px",
        })
    });
}
```
### 2.2 进阶的清晰度优化方案
> 上述设置可以解决通常情况下图片不清晰的问题，不过探索并没有结束。

实际在我们的项目中，即使作出2.1节的设置后，大果粒一般的渲染结果依然尴尬。

**下面直接给出3条进一步的优化策略：**

1. 更改百分比布局为px布局（如果原先是百分比布局的话）
2. 关闭canvas默认的抗锯齿设置
3. 设置模糊元素的width和height为素材原有宽高，然后通过transform: scale进行缩放。这里scale的数值由具体需求决定。
**基本原理**

1. 如果原来使用百分比设置元素宽高，请更改为px为单位的宽高，避免样式二次计算导致的模糊
2. 默认情况下，canvas的抗锯齿是开启的，需要关闭抗锯齿来实现图像的锐化(MDN: imageSmoothingEnabled )
3. 除了canvas可以通过扩大2倍宽高然后缩放至原有宽高来提高清晰度，对于DOM中其他的元素也可以使用css样式的scale来实现同样的缩放
**例: html2canvas配置**
```
convert2canvas() {
 
    var cntElem = $('#j-sec-end')[0];
 
    var shareContent = cntElem;//需要截图的包裹的（原生的）DOM 对象
    var width = shareContent.offsetWidth; //获取dom 宽度
    var height = shareContent.offsetHeight; //获取dom 高度
    var canvas = document.createElement("canvas"); //创建一个canvas节点
    var scale = 2; //定义任意放大倍数 支持小数
    canvas.width = width * scale; //定义canvas 宽度 * 缩放
    canvas.height = height * scale; //定义canvas高度 *缩放
    canvas.getContext("2d").scale(scale, scale); //获取context,设置scale 
    var opts = {
        scale: scale, // 添加的scale 参数
        canvas: canvas, //自定义 canvas
        // logging: true, //日志开关，便于查看html2canvas的内部执行流程
        width: width, //dom 原始宽度
        height: height,
        useCORS: true // 【重要】开启跨域配置
    };
 
    html2canvas(shareContent, opts).then(function (canvas) {
 
        var context = canvas.getContext('2d');
        // 【重要】关闭抗锯齿
        context.mozImageSmoothingEnabled = false;
        context.webkitImageSmoothingEnabled = false;
        context.msImageSmoothingEnabled = false;
        context.imageSmoothingEnabled = false;
        
        // 【重要】默认转化的格式为png,也可设置为其他格式
        var img = Canvas2Image.convertToJPEG(canvas, canvas.width, canvas.height);
 
        document.body.appendChild(img);
 
        $(img).css({
            "width": canvas.width / 2 + "px",
            "height": canvas.height / 2 + "px",
        }).addClass('f-full');
 
    });
}
```
**例: DOM元素样式：?**
```
.targetElem {width: 54px;height: 142px;margin-top:2px;margin-left:17px;transform: scale(0.5)}
```

## 三、含有跨域图片的配置
由于canvas对于图片资源的同源限制，如果画布中包含跨域的图片资源则会污染画布，造成生成图片样式混乱或者html2canvas方法不执行等问题。

以下主要解决**两类跨域的图片资源**：包括已配置过CORS的CDN中的图片资源和微信用户头像图片资源。

### 3.1 针对CDN中的图片的配置
1. 要求CDN的图片配置好CORS。CDN配置好后，通过chrome开发者工具可以看到响应头中应含有Access-Control-Allow-Origin的字段。
2. 开启html2canvas的useCORS配置项。即作如下设置：
```?
var opts = {useCORS: true};
 
html2canvas(element, opts);
```
*注意：*
如果没有开启html2canvas的useCORS配置项，html2canvas会正常执行且不会报错，但是不会输出对应的CDN图片
（已测试同时包含CDN的图片和本地图片的资源的页面，但是只有本地图片能够被正常渲染出来）

### 3.2 针对微信用户头像的配置
如果需要将微信平台中的用户头像一并保存为图片，3.1的方案无能为力。可通过配置服务端代理转发(forward)实现，此处不赘述。

### 其他注意事项
1. margin的遮挡问题
微信中，唤出长按保存图片的菜单要求长按的对象直接是<image>元素，如果<image>元素上方存在遮挡，则不会唤出菜单。
而事实上，引发遮挡的并不只是非<image>元素，还可能是margin属性。例如：若在页面底部，对一个绝对定位的元素设置了数值很大的margin-top，则margin-top所涉及的区域，均无法长按唤出菜单。解决方案：将margin-top改用为top即可。

2. 安卓版微信保存图片失败的问题
canvas2img默认保存图片的格式为png，而在安卓版微信中所生成的图片尽管能长按唤出保存图片的菜单，但是无法正确保存到本地相册。 解决方案：设置canvas2img的生成图片格式配置项为jpeg即可。

3. JPEG的黑屏问题
设置canvas2img输出格式为jpeg，会有一定几率导致生成的图片包含大量的黑色块。可能的解决方案：缩减部分图片元素的体积和尺寸大小。

4. 不能保留动效
在图片的转化前，必须停止或者删除动效后才能正确渲染出图片，否则生成的图片是破裂的。

## 参考文献
[CanvasRenderingContext2D.drawImage()](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/drawImage)
[Add dpi/scale options for custom resolution](https://github.com/niklasvh/html2canvas/pull/1087)
[HTMLCanvasElement.toDataURL()](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL)
[html5 canvas在高倍屏下变模糊的处理办法](https://yq.aliyun.com/ziliao/4416)
[Canvas实现保存图片到本地](http://blog.csdn.net/sophia1010/article/details/52945542)
[html2canvas截图如何解决跨域的问题](https://yq.aliyun.com/wenzhang/show_27647)














