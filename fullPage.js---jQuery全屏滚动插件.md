# jQueryȫ���������fullPage.js

## ʹ��˵��

### 1�������ļ�

������������jQuery�������㻹��Ҫ����jQuery��������Fullpage���֮ǰ���롣
```
<link rel="stylesheet" type="text/css" href="/fullpage/jquery.fullPage.css" />
<script src="/fullpage/jquery.min.js"></script>
<script type="text/javascript" src="/fullpage/jquery.fullPage.js"></script>
```

�������Ҫ�Զ���ҳ�������Ч��������Ҫ����jquery.easings.min.js�ļ����ж��ַ�������ʵ��ҳ��Ч�������ֺ�벿���н���

```
<script src="/fullpage/jquery.easings.min.js"></script>
```

�������ݱȽ϶��ҳ�棬���������Ҳ�Ĺ�����������Ĭ��������޷�����������Ҫjquery.slimscroll.min.js�ļ����Զ��廬������Ч����

```
<script type="text/javascript" src="/fullpage/jquery.slimscroll.min.js"></script>
```

### 2��Ҫ��HTML�ṹ

ÿ������ζ���Ϊ����section���Ԫ�ء� ��һ���������Ϊ��ҳ����Ĭ�ϼ�����롣 �����Ӧ���з�װ����<div id="fullpage"> ���� ��װ������bodyԪ�ء�

```
<div id="fullpage'">
<div class="section">Some section</div>
<div class="section">Some section</div>
<div class="section">Some section</div>
<div class="section">Some section</div>
</div>
```

��������Ҫ��ĳһ��section��Ϊ��ҳ�ĵ�һ��չʾ����ֻ��Ҫ�����section���һ��active���࣬Fullpage���Զ�����չʾ�����Ļ�����綨������Ĵ��룺

```
<div class="section active">Some section</div>
```

Fullpage�Դ����һ����Ļõ�Ƭ��ֻ��Ҫ��section�����DIVԪ�أ����Ҹ�DIVԪ�����slide�࣬FUllpage���Զ����ɻõ�Ƭ��Ч����������Ĵ��룺

```
<div class="section">
<div class="slide"> Slide 1 </div>
<div class="slide"> Slide 2 </div>
<div class="slide"> Slide 3 </div>
<div class="slide"> Slide 4 </div>
</div>
```

### 3����ʼ��Fullpage

ʹ��jQuery���ĵ���������Ժ�ִ�к�������ʼ��Fullpage�����

```
$(document).ready(function() {
$('#fullpage').fullpage();
});
```

���е�ѡ�����ø����ӵĳ�ʼ�����ܿ�������������

```
$(document).ready(function() {
	$('#fullpage').fullpage({
		//Navigation
		menu: false,//�󶨲˵����趨�����������anchors��ֵ��Ӧ�󣬲˵����Կ��ƹ�����Ĭ��Ϊfalse��
		anchors:['firstPage', 'secondPage'],//anchors����ê���ӣ�Ĭ��Ϊ[]
		lockAnchors: false,//�Ƿ�����ê���ӣ�Ĭ��Ϊfalse,��Ϊtrue�����ӵ�ַ����ı�
		navigation: false,//�Ƿ���ʾ������Ĭ��Ϊfalse
		navigationPosition: 'right',//����СԲ���λ��
		navigationTooltips: ['firstSlide', 'secondSlide'],//����СԲ�����ʾ
		showActiveTooltip: false,//�Ƿ���ʾ��ǰҳ���tooltip��Ϣ
		slidesNavigation: true,//�Ƿ���ʾ����õ�Ƭ�ĵ�����Ĭ��Ϊfalse
		slidesNavPosition: 'bottom',//���򵼺���λ�ã�Ĭ��Ϊbottom����������Ϊtop��bottom
		 
		//Scrolling
		css3: true,//�Ƿ�ʹ��CSS3 transforms��ʵ�ֹ���Ч����Ĭ��Ϊtrue
		scrollingSpeed: 700,//���ù����ٶȣ���λ���룬Ĭ��700
		autoScrolling: true,//�Ƿ�ʹ�ò���Ĺ�����ʽ��Ĭ��Ϊtrue,��Ϊfalse������������Դ�������
		fitToSection: true,//�����Ƿ�����Ӧ�������ڵĿռ䣬Ĭ��ֵ��true
		scrollBar: false,//�Ƿ������������Ĭ��Ϊfalse,��Ϊtrue������Դ�����������
		easing: 'easeInOutCubic',//����ҳ��section�����Ķ�����ʽ�����޸Ĵ���������jquery.easing���
		easingcss3: 'ease',//����ҳ��section�����Ĺ���Ч�������޸Ĵ�����������������
		loopBottom: false,//��������Ͳ����Ƿ�����������������Ĭ��Ϊfalse
		loopTop: false,//������������Ƿ������������ײ���Ĭ��Ϊfalse
		loopHorizontal: true,//����slide�õ�Ƭ�Ƿ�ѭ��������Ĭ��Ϊtrue
		continuousVertical: false,//�Ƿ�ѭ��������������loopTop��loopBottomѡ��
		normalScrollElements: '#element1, .element2',//�����Զ�����������ʱ��һЩԪ�أ�����ٶȵ�ͼ
		scrollOverflow: false,//���ݳ����������Ƿ���ʾ��������true����ʾ����������������鿴���ݻ���Ҫjquery.slimscroll��������
		touchSensitivity: 15,//���ƶ��豸�л���ҳ��������ԣ�Ĭ��Ϊ5���100��Խ��Խ�ѻ���
		normalScrollElementTouchThreshold: 5,
		 
		//Accessibility
		keyboardScrolling: true,//�Ƿ����ʹ�ü��̷����������Ĭ��Ϊtrue
		animateAnchor: true,//ê�����Ƿ���Կ��ƹ���������Ĭ��Ϊtrue,��Ϊfalse��ê���Ӷ�λʧЧ
		recordHistory: true,//�Ƿ��¼��ʷ��Ĭ��Ϊtrue,�������ǰ�����˿ɵ�������autoScrolling:false,��ô������Խ����ر�
		 
		//Design
		controlArrows: true,//�����Ƿ�ͨ����ͷ������slide,Ĭ��true
		verticalCentered: true,//����ÿһҳ�������Ƿ�ֱ���У�Ĭ��true
		resize : false,//�����Ƿ��洰�����Ŷ����ţ�Ĭ��false
		sectionsColor : ['#ccc', '#fff'],//Ϊÿ��section����background-color����
		paddingTop: '3em',����ÿһ��section������padding,Ĭ��Ϊ0
		paddingBottom: '10px',����ÿһ��section�ײ���padding,Ĭ��Ϊ0
		fixedElements: '#header, .footer',�̶�Ԫ�أ�Ĭ��Ϊnull,��Ҫ����һ��jqueryѡ��������ҳ�����ʱ��fixElements���õ�Ԫ�ز�����
		responsiveWidth: 0,
		responsiveHeight: 0,
		 
		//Custom selectors
		sectionSelector: '.section',//sectionѡ������Ĭ��Ϊ.section
		slideSelector: '.slide',//slideѡ������Ĭ��Ϊ.slide
		 
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

## �Զ������Ч������ͨ���������ַ�ʽʵ��

fullpageҳ��ṹ

```
<div id="fullpage">
    <div class="section section1">
        <h3>��һ��</h3>
        <p id="p1">fullPage.js �� �ص�������ʾ</p>
    </div>
    <div class="section section2">
        <h3>�ڶ���</h3>
        <p id="p2">�������ڶ�����Ļص�����ִ�е�Ч��</p>
    </div>
    <div class="section section3">
        <h3>������</h3>
        <p id="p3">��������������Ļص�����ִ�е�Ч��</p>
    </div>
    <div class="section section4">
        <h3>������</h3>
        <p id="p4">��������������Ļص�����ִ�е�Ч��</p>
    </div>
</div>
```

1.����jquery.easing.min.js  ʵ�ֶ���Ч��

```
$(function(){
            $('#fullpage').fullpage({
                sectionsColor: ['#1bbc9b', '#4BBFC3', '#7BAABE', '#f90'],
                anchors: ['page1', 'page2', 'page3', 'page4', 'page5'],
                //��������ײ����Ƿ���ض���
                loopBottom: true,
                // �Ƿ���ʾ��Ŀ����
                navigation: true,
               
                afterLoad: function(anchorLink, index){
                 if(index == 2){
                 $('.section2').find('p').delay(500).animate({
                 left: '0'
                 }, 1500, 'easeOutExpo');
                 }
                 if(index == 3){
                 $('.section3').find('p').delay(500).animate({
                 bottom: '0'
                 }, 1500, 'easeOutExpo');
                 }
                 if(index == 4){
                 $('.section4').find('p').fadeIn(2000);
                 }
                 },
                 onLeave: function(index, direction){
                 if(index == '2'){
                 $('.section2').find('p').delay(500).animate({
                 left: '-120%'
                 }, 1500, 'easeOutExpo');
                 }
                 if(index == '3'){
                 $('.section3').find('p').delay(500).animate({
                 bottom: '-120%'
                 }, 1500, 'easeOutExpo');
                 }
                 if(index == '4'){
                 $('.section4').find('p').fadeOut(2000);
                 }
                 }
            });
        });
```

2.����animate.css 

```
$(function(){
            $('#fullpage').fullpage({
                sectionsColor: ['#1bbc9b', '#4BBFC3', '#7BAABE', '#f90'],
                anchors: ['page1', 'page2', 'page3', 'page4', 'page5'],
                //��������ײ����Ƿ���ض���
                loopBottom: true,
                // �Ƿ���ʾ��Ŀ����
                navigation: true,

                //������ĳһ����Ļص����������� anchorLink �� index ����������anchorLink ��ê���ӵ����ƣ�index ����ţ���1��ʼ����
                afterLoad: function (anchorLink, index) {
                    if (index == 1) {
                        // ��IDΪP1��Ԫ�����class��animated��animate.css���������ӵ�class,��������Ƕ���class
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
                //  ����ǰ�Ļص�������index ���뿪�ġ�ҳ�桱����ţ���1��ʼ���㣻
                // nextIndex �ǹ������ġ�ҳ�桱����ţ���1��ʼ���㣻
                // direction �ж����Ϲ����������¹�����ֵ�� up �� down��
                /*onLeave: function (index, direction) {
                    if (index == '1') {
                        // ��IDΪP1��Ԫ���Ƴ�class
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

3.ʹ��CSS3��д����Ч��



## GitHub�����ĵ�

https://github.com/alvarotrigo/fullPage.js/tree/master/lang/chinese#fullpagejs



