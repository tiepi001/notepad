
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

//      大多新版本浏览器不支持audio自动播放 在此增加addEventListener交互事件触发播放
//      touchstart重复执行影响音乐播放  {once: true}控制只执行一次
        function audioAutoPlay(audio) {
            document.addEventListener('touchstart', function () {
                audio.play();
            }, {once: true});
//            引入微信API接口
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
//      解决iOS不能循环播放问题
        audio.onended = function () {
            audio.load();
            audio.play();
        }
    })
</script>

```

## 总结

1.大部分新版浏览器禁用了audio自动播放功能  需要添加监听touchstart事件触发audio播放
2.引入微信API接口
3.部分移动端浏览器无法循环播放 使用如下脚本
```
audio.onended = function () {
            audio.load();
            audio.play();
        }
```
4.js控制媒体
play()播放
pause()暂停
load()重新加载