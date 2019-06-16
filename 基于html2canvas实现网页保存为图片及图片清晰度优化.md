# ����html2canvasʵ����ҳ����ΪͼƬ��ͼƬ�������Ż�
> ���μ���������Դ��H5��Ŀ�е�һ����Ҫ��������ʵ��΢�ų�����ҳ����Ϊ��ͼ��<br/>
�����и����ӣ�����΢�Ŵ򿪣�����ͼƬ���ɱ��棩��3����̽�����֪ʶ�߽�<br/>
��������ҳ����ΪͼƬ��һ��ʮ����Ȥ�Ĺ��ܣ�������H5�ҳ�Ľ�βҳ��������������Ŀ�е��кͲȿӵ�һЩС��ͻ��ܡ�

## һ��ʵ��HTMLҳ�汣��ΪͼƬ

### 1.1 ��֪���з���

������֪�ܹ�ʵ����ҳ����ΪͼƬ�ķ���������

- ����1����DOM��дΪcanvas��Ȼ������canvas��toDataURL����ʵ�ֽ�DOM���Ϊ����ͼƬչʾ��data URI
- ����2��ʹ��html2canvas.jsʵ�֣���ѡ����Canvas2Image.jsʵ����ҳ����ΪͼƬ��
- ����3��ʹ��rasterizeHTML.jsʵ��

### 1.2 ���������ѡ��

- **����1**����Ҫ�ֶ�����ÿ��DOMԪ�ص�Computed Style��Ȼ����Ҫ�����Ԫ����canvas�Ĵ�Сλ�õ����ԡ�
**����1�ѵ�**��
1. �൱����ȫ��д������ҳ��Ĳ�����ʽ�������˹�������
2. ����canvas��û�еĶ���������Ԫ�طḻ�����ָ��ӵ�ҳ�棬�����ع���
3. ����DOMԪ�ظ�д��canvas�����һЩ���ѣ����磺����֧����Ӧʽ��ͼƬԪ�������Ȳ��Ѻ����ֵ������ʶ������ȡ�
- **����2**�����๦����Github��stars���(��������ά��)��Stack Overflow���зḻ�����ۡ�ֻ��򵥵���html2canvas�������趨������ɡ�
- **����3**���÷��������ƽ϶࣬Ŀǰ��֧��3���תΪcanvas��Ŀ���ʽ: ҳ��url��html�ַ�����document����
**С��**: html2canvas��Ŀǰʵ����ҳ����ΪͼƬ���ܵ��ۺ����ѡ��

### 1.3 html2canvas��ʹ�÷���

> https://github.com/niklasvh/html2canvas

�����������html2canvas�汾��0.5.0-beta4

#### 1.3.1 ʵ�ֱ���ΪͼƬ�ĵ�һ����htmlתΪcanvas
����html2canvas.js�ɽ�һ��Ԫ����ȾΪcanvas��ֻ��Ҫ�򵥵ĵ���html2canvas(element[, options]);���ɡ�����html2canvas�����᷵��һ��������<canvas>Ԫ�ص�promise��
```
html2canvas(document.body).then(function(canvas) {
    document.body.appendChild(canvas);
});
```
#### 1.3.2 ʵ�ֱ���ΪͼƬ�ĵڶ�����canvasתimage
��һ�����ɵ�canvas��Ϊ����Ŀ��Ԫ�ص�<canvas>Ԫ�ض���ʵ�ֱ���ͼƬ��Ŀ��ֻ��Ҫ��canvasתimage���ɡ�

�����ת��������2�֣�

- **����1**������ԭ��canvas��toDataURL������canvas���Ϊdata: URI���͵�ͼƬ��ַ���ٽ���ͼƬ��ַ��ֵ��<image>Ԫ�ص�src���Լ���
- **����2**��ʹ�õ�������Canvas2Image.js��������convertToImage�������ɣ�GitHub��
ʵ���ϣ�Canvas2Image.jsҲ�ǻ���canvas.toDataURL�ķ�װ�����ԭ����canvas API����תΪͼƬ�Ĺ����Ͽ��Ǹ�Ϊ����(δѹ���İ���СΪ7.4KB)���ʺ���Ŀʹ�á�

## ��������ͼƬ���������Ż�����
### 2.1 �������������Ż�����
> ����ͼƬ��������ȡ���ڵ�һ����htmlת���ɵ�canvas�������ȡ�

**���н�������ο���**

> html5 canvas�ڸ߱����±�ģ���Ĵ���취<br/>
html5 canvas����ͼƬģ��������
**�����ԭ��Ϊ��**
��canvas������width��height���ԷŴ�Ϊ2������������ΪdevicePixelRatio���������canvas��CSS��ʽwidth��height����Ϊԭ��1���Ĵ�С��

**����**��ϣ����html��ʵ����ʾ��<canvas>��߷ֱ�Ϊ160px,90px�������������
```
<canvas width="320" height="180" style="width:160px;height:90px;"></canvas>
```
�ο������ĵ������ʹ�ð������£�
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
### 2.2 ���׵��������Ż�����
> �������ÿ��Խ��ͨ�������ͼƬ�����������⣬����̽����û�н�����

ʵ�������ǵ���Ŀ�У���ʹ����2.1�ڵ����ú󣬴����һ�����Ⱦ�����Ȼ���Ρ�

**����ֱ�Ӹ���3����һ�����Ż����ԣ�**

1. ���İٷֱȲ���Ϊpx���֣����ԭ���ǰٷֱȲ��ֵĻ���
2. �ر�canvasĬ�ϵĿ��������
3. ����ģ��Ԫ�ص�width��heightΪ�ز�ԭ�п�ߣ�Ȼ��ͨ��transform: scale�������š�����scale����ֵ�ɾ������������
**����ԭ��**

1. ���ԭ��ʹ�ðٷֱ�����Ԫ�ؿ�ߣ������ΪpxΪ��λ�Ŀ�ߣ�������ʽ���μ��㵼�µ�ģ��
2. Ĭ������£�canvas�Ŀ�����ǿ����ģ���Ҫ�رտ������ʵ��ͼ�����(MDN: imageSmoothingEnabled )
3. ����canvas����ͨ������2�����Ȼ��������ԭ�п������������ȣ�����DOM��������Ԫ��Ҳ����ʹ��css��ʽ��scale��ʵ��ͬ��������
**��: html2canvas����**
```
convert2canvas() {
 
    var cntElem = $('#j-sec-end')[0];
 
    var shareContent = cntElem;//��Ҫ��ͼ�İ����ģ�ԭ���ģ�DOM ����
    var width = shareContent.offsetWidth; //��ȡdom ���
    var height = shareContent.offsetHeight; //��ȡdom �߶�
    var canvas = document.createElement("canvas"); //����һ��canvas�ڵ�
    var scale = 2; //��������Ŵ��� ֧��С��
    canvas.width = width * scale; //����canvas ��� * ����
    canvas.height = height * scale; //����canvas�߶� *����
    canvas.getContext("2d").scale(scale, scale); //��ȡcontext,����scale 
    var opts = {
        scale: scale, // ��ӵ�scale ����
        canvas: canvas, //�Զ��� canvas
        // logging: true, //��־���أ����ڲ鿴html2canvas���ڲ�ִ������
        width: width, //dom ԭʼ���
        height: height,
        useCORS: true // ����Ҫ��������������
    };
 
    html2canvas(shareContent, opts).then(function (canvas) {
 
        var context = canvas.getContext('2d');
        // ����Ҫ���رտ����
        context.mozImageSmoothingEnabled = false;
        context.webkitImageSmoothingEnabled = false;
        context.msImageSmoothingEnabled = false;
        context.imageSmoothingEnabled = false;
        
        // ����Ҫ��Ĭ��ת���ĸ�ʽΪpng,Ҳ������Ϊ������ʽ
        var img = Canvas2Image.convertToJPEG(canvas, canvas.width, canvas.height);
 
        document.body.appendChild(img);
 
        $(img).css({
            "width": canvas.width / 2 + "px",
            "height": canvas.height / 2 + "px",
        }).addClass('f-full');
 
    });
}
```
**��: DOMԪ����ʽ��?**
```
.targetElem {width: 54px;height: 142px;margin-top:2px;margin-left:17px;transform: scale(0.5)}
```

## �������п���ͼƬ������
����canvas����ͼƬ��Դ��ͬԴ���ƣ���������а��������ͼƬ��Դ�����Ⱦ�������������ͼƬ��ʽ���һ���html2canvas������ִ�е����⡣

������Ҫ���**��������ͼƬ��Դ**�����������ù�CORS��CDN�е�ͼƬ��Դ��΢���û�ͷ��ͼƬ��Դ��

### 3.1 ���CDN�е�ͼƬ������
1. Ҫ��CDN��ͼƬ���ú�CORS��CDN���úú�ͨ��chrome�����߹��߿��Կ�����Ӧͷ��Ӧ����Access-Control-Allow-Origin���ֶΡ�
2. ����html2canvas��useCORS����������������ã�
```?
var opts = {useCORS: true};
 
html2canvas(element, opts);
```
*ע�⣺*
���û�п���html2canvas��useCORS�����html2canvas������ִ���Ҳ��ᱨ�����ǲ��������Ӧ��CDNͼƬ
���Ѳ���ͬʱ����CDN��ͼƬ�ͱ���ͼƬ����Դ��ҳ�棬����ֻ�б���ͼƬ�ܹ���������Ⱦ������

### 3.2 ���΢���û�ͷ�������
�����Ҫ��΢��ƽ̨�е��û�ͷ��һ������ΪͼƬ��3.1�ķ�������Ϊ������ͨ�����÷���˴���ת��(forward)ʵ�֣��˴���׸����

### ����ע������
1. margin���ڵ�����
΢���У�������������ͼƬ�Ĳ˵�Ҫ�󳤰��Ķ���ֱ����<image>Ԫ�أ����<image>Ԫ���Ϸ������ڵ����򲻻ỽ���˵���
����ʵ�ϣ������ڵ��Ĳ���ֻ�Ƿ�<image>Ԫ�أ���������margin���ԡ����磺����ҳ��ײ�����һ�����Զ�λ��Ԫ����������ֵ�ܴ��margin-top����margin-top���漰�����򣬾��޷����������˵��������������margin-top����Ϊtop���ɡ�

2. ��׿��΢�ű���ͼƬʧ�ܵ�����
canvas2imgĬ�ϱ���ͼƬ�ĸ�ʽΪpng�����ڰ�׿��΢���������ɵ�ͼƬ�����ܳ�����������ͼƬ�Ĳ˵��������޷���ȷ���浽������ᡣ �������������canvas2img������ͼƬ��ʽ������Ϊjpeg���ɡ�

3. JPEG�ĺ�������
����canvas2img�����ʽΪjpeg������һ�����ʵ������ɵ�ͼƬ���������ĺ�ɫ�顣���ܵĽ����������������ͼƬԪ�ص�����ͳߴ��С��

4. ���ܱ�����Ч
��ͼƬ��ת��ǰ������ֹͣ����ɾ����Ч�������ȷ��Ⱦ��ͼƬ���������ɵ�ͼƬ�����ѵġ�

## �ο�����
[CanvasRenderingContext2D.drawImage()](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/drawImage)
[Add dpi/scale options for custom resolution](https://github.com/niklasvh/html2canvas/pull/1087)
[HTMLCanvasElement.toDataURL()](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL)
[html5 canvas�ڸ߱����±�ģ���Ĵ���취](https://yq.aliyun.com/ziliao/4416)
[Canvasʵ�ֱ���ͼƬ������](http://blog.csdn.net/sophia1010/article/details/52945542)
[html2canvas��ͼ��ν�����������](https://yq.aliyun.com/wenzhang/show_27647)














