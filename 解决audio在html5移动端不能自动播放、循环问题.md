
```
<div id="music">
    <div class="zhizhen"></div>
    <div id="audioBox" class="rotation" style="">
        <audio id="audio" autoplay="autoplay" src="8.mp3"></audio>
    </div>
</div>
```

```
<style>
#music{position: absolute; top: 2rem; right: 2rem; z-index: 99; }
#audioBox {width: 4rem; height: 4rem;border-radius: 50%;
    background-color: rgba(0, 0, 0, .5); background-repeat: no-repeat; background-image: url("../images/music.png");
    background-size: 100% 100%; }
.zhizhen{width: 1.2rem;height: 2rem;background-repeat: no-repeat; background-image: url("../images/music-1.png");
    background-size: 100% 100%;position: absolute; left: 3rem; z-index: 99;}
@-webkit-keyframes rotation {
    0%{transform: rotate(0deg); -webkit-transform: rotate(0deg); -moz-transform: rotate(0deg); -o-transform: rotate(0deg);}
    18%{transform: rotate(60deg); -webkit-transform: rotate(60deg); -moz-transform: rotate(60deg); -o-transform: rotate(60deg);}
    50%{transform: rotate(180deg); -webkit-transform: rotate(180deg); -moz-transform: rotate(180deg); -o-transform: rotate(180deg);}
    82%{transform: rotate(300deg); -webkit-transform: rotate(300deg); -moz-transform: rotate(300deg); -o-transform: rotate(300deg);}
    100%{transform: rotate(360deg); -webkit-transform: rotate(360deg); -moz-transform: rotate(360deg); -o-transform: rotate(360deg);}
}
@keyframes rotation {
    0%{transform: rotate(0deg); -webkit-transform: rotate(0deg); -moz-transform: rotate(0deg); -o-transform: rotate(0deg);}
    20%{transform: rotate(60deg); -webkit-transform: rotate(60deg); -moz-transform: rotate(60deg); -o-transform: rotate(60deg);}
    50%{transform: rotate(180deg); -webkit-transform: rotate(180deg); -moz-transform: rotate(180deg); -o-transform: rotate(180deg);}
    80%{transform: rotate(300deg); -webkit-transform: rotate(300deg); -moz-transform: rotate(300deg); -o-transform: rotate(300deg);}
    100%{transform: rotate(360deg); -webkit-transform: rotate(360deg); -moz-transform: rotate(360deg); -o-transform: rotate(360deg);}
}
.rotation {
    transform: rotate(360deg);-webkit-transform: rotate(360deg); -moz-transform: rotate(360deg);-o-transform: rotate(360deg);
    animation: rotation 3s linear infinite; -moz-animation: rotation 3s linear infinite;
    -webkit-animation: rotation 3s linear infinite; -o-animation: rotation 3s linear infinite; }
</style>
```


```
<script>
    $(window).load(function () {
        var $music = $('#music');
        var $forbid = $music.find('#audioBox');
        var audio = document.getElementById('audio');

//      ����°汾�������֧��audio�Զ����� �ڴ�����addEventListener�����¼���������
//      touchstart�ظ�ִ��Ӱ�����ֲ���  {once: true}����ִֻ��һ��
        function audioAutoPlay(audio) {
            document.addEventListener('touchstart', function () {
                audio.play();
            }, {once: true});
//            ����΢��API�ӿ�
            document.addEventListener("WeixinJSBridgeReady", function () {
                audio.play();
            }, false);
            document.addEventListener('YixinJSBridgeReady', function () {
                audio.play();
            }, false);
        }
        audioAutoPlay(audio);

        $music.on('click', function () {
            if ($forbid.hasClass('rotation')) {
                $forbid.removeClass('rotation');
            } else {
                $forbid.addClass('rotation');
            }
            if (audio.paused) {
                audio.play();
                return false;
            }
            audio.pause();
        });
//      ���iOS����ѭ����������
        audio.onended = function () {
            audio.load();
            audio.play();
        }
    })
</script>

```

## �ܽ�

1.�󲿷��°������������audio�Զ����Ź���  ��Ҫ��Ӽ���touchstart�¼�����audio����
2.����΢��API�ӿ�
3.�����ƶ���������޷�ѭ������ ʹ�����½ű�
```
audio.onended = function () {
            audio.load();
            audio.play();
        }
```
4.js����ý��
play()����
pause()��ͣ
load()���¼���