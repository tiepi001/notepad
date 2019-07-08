# jQuery全屏滚动插件fullPage.js

## 使用说明

### 1、包含文件

这个插件依赖于jQuery，所以你还需要下载jQuery，并且在Fullpage插件之前引入。
```
<link rel="stylesheet" type="text/css" href="/fullpage/jquery.fullPage.css" />
<script src="/fullpage/jquery.min.js"></script>
<script type="text/javascript" src="/fullpage/jquery.fullPage.js"></script>
```

如果你需要自定义页面滚动的效果，你需要引入jquery.easings.min.js文件。有多种方法可以实现页面效果，文字后半部门有介绍

```
<script src="/fullpage/jquery.easings.min.js"></script>
```

对于内容比较多的页面，可以设置右侧的滚动条，但是默认情况下无法滚动，你需要jquery.slimscroll.min.js文件来自定义滑条滚动效果。

```
<script type="text/javascript" src="/fullpage/jquery.slimscroll.min.js"></script>
```

### 2、要求HTML结构

每个代码段定义为包含section类的元素。 第一个代码段作为主页，是默认激活代码。 代码段应进行封装（即<div id="fullpage"> ）。 封装不能是body元素。

```
<div id="fullpage'">
<div class="section">Some section</div>
<div class="section">Some section</div>
<div class="section">Some section</div>
<div class="section">Some section</div>
</div>
```

假如你需要让某一个section作为首页的第一屏展示，你只需要给这个section添加一个active的类，Fullpage会自动优先展示这个屏幕，例如定义下面的代码：

```
<div class="section active">Some section</div>
```

Fullpage自带左右滑动的幻灯片，只需要在section中添加DIV元素，并且给DIV元素添加slide类，FUllpage会自动生成幻灯片特效，例如下面的代码：

```
<div class="section">
<div class="slide"> Slide 1 </div>
<div class="slide"> Slide 2 </div>
<div class="slide"> Slide 3 </div>
<div class="slide"> Slide 4 </div>
</div>
```

### 3、初始化Fullpage

使用jQuery的文档加载完毕以后执行函数，初始化Fullpage插件。

```
$(document).ready(function() {
$('#fullpage').fullpage();
});
```

所有的选项设置更复杂的初始化可能看起来像这样：

```
$(document).ready(function() {
	$('#fullpage').fullpage({
		//Navigation
		menu: false,//绑定菜单，设定的相关属性与anchors的值对应后，菜单可以控制滚动，默认为false。
		anchors:['firstPage', 'secondPage'],//anchors定义锚链接，默认为[]
		lockAnchors: false,//是否锁定锚链接，默认为false,设为true后链接地址不会改变
		navigation: false,//是否显示导航，默认为false
		navigationPosition: 'right',//导航小圆点的位置
		navigationTooltips: ['firstSlide', 'secondSlide'],//导航小圆点的提示
		showActiveTooltip: false,//是否显示当前页面的tooltip信息
		slidesNavigation: true,//是否显示横向幻灯片的导航，默认为false
		slidesNavPosition: 'bottom',//横向导航的位置，默认为bottom，可以设置为top或bottom
		 
		//Scrolling
		css3: true,//是否使用CSS3 transforms来实现滚动效果，默认为true
		scrollingSpeed: 700,//设置滚动速度，单位毫秒，默认700
		autoScrolling: true,//是否使用插件的滚动方式，默认为true,若为false则会出现浏览器自带滚动条
		fitToSection: true,//设置是否自适应整个窗口的空间，默认值：true
		scrollBar: false,//是否包含滚动条，默认为false,若为true浏览器自带滚动条出现
		easing: 'easeInOutCubic',//定义页面section滚动的动画方式，若修改此项需引入jquery.easing插件
		easingcss3: 'ease',//定义页面section滚动的过渡效果，若修改此项需引入第三方插件
		loopBottom: false,//滚动到最低部后是否连续滚动到顶部，默认为false
		loopTop: false,//滚动到最顶部后是否连续滚动到底部，默认为false
		loopHorizontal: true,//横向slide幻灯片是否循环滚动，默认为true
		continuousVertical: false,//是否循环滚动，不兼容loopTop和loopBottom选项
		normalScrollElements: '#element1, .element2',//避免自动滚动，滚动时的一些元素，例如百度地图
		scrollOverflow: false,//内容超过满屏后是否显示滚动条，true则显示滚动条，若需滚动查看内容还需要jquery.slimscroll插件的配合
		touchSensitivity: 15,//在移动设备中滑动页面的敏感性，默认为5最高100，越大越难滑动
		normalScrollElementTouchThreshold: 5,
		 
		//Accessibility
		keyboardScrolling: true,//是否可以使用键盘方向键导航，默认为true
		animateAnchor: true,//锚链接是否可以控制滚动动画，默认为true,若为false则锚链接定位失效
		recordHistory: true,//是否记录历史，默认为true,浏览器的前进后退可导航。若autoScrolling:false,那么这个属性将被关闭
		 
		//Design
		controlArrows: true,//定义是否通过箭头来控制slide,默认true
		verticalCentered: true,//定义每一页的内容是否垂直居中，默认true
		resize : false,//字体是否随窗口缩放而缩放，默认false
		sectionsColor : ['#ccc', '#fff'],//为每个section设置background-color属性
		paddingTop: '3em',设置每一个section顶部的padding,默认为0
		paddingBottom: '10px',设置每一个section底部的padding,默认为0
		fixedElements: '#header, .footer',固定元素，默认为null,需要配置一个jquery选择器，在页面滚动时，fixElements设置的元素不滚动
		responsiveWidth: 0,
		responsiveHeight: 0,
		 
		//Custom selectors
		sectionSelector: '.section',//section选择器。默认为.section
		slideSelector: '.slide',//slide选择器，默认为.slide
		 
		//events
		onLeave: function(index, nextIndex, direction){},
		afterLoad: function(anchorLink, index){},
		afterRender: function(){},
		afterResize: function(){},
		afterSlideLoad: function(anchorLink, index, slideAnchor, slideIndex){},
		onSlideLeave: function(anchorLink, index, slideIndex, direction, nextSlideIndex){}
	});
});
```

## 自定义滚动效果可以通过以下三种方式实现

fullpage页面结构

```
<div id="fullpage">
    <div class="section section1">
        <h3>第一屏</h3>
        <p id="p1">fullPage.js — 回调函数演示</p>
    </div>
    <div class="section section2">
        <h3>第二屏</h3>
        <p id="p2">滚动到第二屏后的回调函数执行的效果</p>
    </div>
    <div class="section section3">
        <h3>第三屏</h3>
        <p id="p3">滚动到第三屏后的回调函数执行的效果</p>
    </div>
    <div class="section section4">
        <h3>第四屏</h3>
        <p id="p4">滚动到第四屏后的回调函数执行的效果</p>
    </div>
</div>
```

### 1.引入jquery.easing.min.js  实现动画效果

```
$(function () {
        $('#fullpage').fullpage({
            sectionsColor: ['#1bbc9b', '#4BBFC3', '#7BAABE', '#f90'],
            anchors: ['page1', 'page2', 'page3', 'page4', 'page5'],
            //滚动到最底部后是否滚回顶部
            loopBottom: true,
            // 是否显示项目导航
            navigation: true,

            afterLoad: function (anchorLink, index) {
                if (index == 2) {
                    $('.section2').find('p').delay(500).animate({
                        left: '0'
                    }, 1500, 'easeOutExpo');
                }
                if (index == 3) {
                    $('.section3').find('p').delay(500).animate({
                        bottom: '0'
                    }, 1500, 'easeOutExpo');
                }
                if (index == 4) {
                    $('.section4').find('p').fadeIn(2000);
                }
            },
            onLeave: function (index, direction) {
                if (index == '2') {
                    $('.section2').find('p').delay(500).animate({
                        left: '-120%'
                    }, 1500, 'easeOutExpo');
                }
                if (index == '3') {
                    $('.section3').find('p').delay(500).animate({
                        bottom: '-120%'
                    }, 1500, 'easeOutExpo');
                }
                if (index == '4') {
                    $('.section4').find('p').fadeOut(2000);
                }
            }
        });
    });
```

### 2.引入animate.css 

```
$(function(){
            $('#fullpage').fullpage({
                sectionsColor: ['#1bbc9b', '#4BBFC3', '#7BAABE', '#f90'],
                anchors: ['page1', 'page2', 'page3', 'page4', 'page5'],
                //滚动到最底部后是否滚回顶部
                loopBottom: true,
                // 是否显示项目导航
                navigation: true,

                //滚动到某一屏后的回调函数，接收 anchorLink 和 index 两个参数，anchorLink 是锚链接的名称，index 是序号，从1开始计算
                afterLoad: function (anchorLink, index) {
                    if (index == 1) {
                        // 向ID为P1的元素添加class，animated是animate.css激活动画必须加的class,后面跟的是动画class
                        $('#p1').addClass('animated zoomIn');
                    }
                    if (index == 2) {
                        $('#p2').addClass('animated fadeInDown');
                    }
                    if (index == 3) {
                        $('#p3').addClass('animated lightSpeedIn');
                    }
                    if (index == 4) {
                        $('#p4').addClass('animated rotateIn');
                    }
                },
                //  滚动前的回调函数，index 是离开的“页面”的序号，从1开始计算；
                // nextIndex 是滚动到的“页面”的序号，从1开始计算；
                // direction 判断往上滚动还是往下滚动，值是 up 或 down。
                /*onLeave: function (index, direction) {
                    if (index == '1') {
                        // 向ID为P1的元素移除class
                        $('#p1').removeClass('animated zoomIn');
                    }
                    if (index == '2') {
                        $('#p2').removeClass('animated fadeInDown');
                    }
                    if (index == '3') {
                        $('#p3').removeClass('animated lightSpeedIn');
                    }
                    if (index == '4') {
                        $('#p4').removeClass('animated rotateIn');
                    }
                }
            });
        });
```

### 3.使用CSS3编写动画效果



## GitHub中文文档

https://github.com/alvarotrigo/fullPage.js/tree/master/lang/chinese#fullpagejs



