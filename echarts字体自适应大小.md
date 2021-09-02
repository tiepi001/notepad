# 1.echarts字体自适应大小
来源：[https://www.jb51.net/article/165254.htm](https://www.jb51.net/article/165254.htm)

> 用echarts做大屏可视化的时候会遇到不是用电脑投屏而是直接在大屏打开的情况，这时候大屏幕下固定的px为单位的字体就会显得很小。有一种解决方法就是采用rem为单位，根据屏幕的宽度调整html的font-size.

###获取屏幕宽度并计算比例

```
function fontSize(res){
  let docEl = document.documentElement,
    clientWidth = window.innerWidth||document.documentElement.clientWidth||document.body.clientWidth;
  if (!clientWidth) return;
  let fontSize = 100 * (clientWidth / 1920);
  return res*fontSize;
}
```

> 在需要设置字体的地方可以这样写，
如在1920屏宽下字体设置为12px,就可以传入0.12给fontSize fontSize(0.12)

```
tooltip : {
   trigger: 'axis',
   axisPointer : {      // 坐标轴指示器，坐标轴触发有效
      type : 'shadow'    // 默认为直线，可选为：'line' |  'shadow'
   },
   textStyle:{
      fontSize: fontSize(0.12),
   }
},
```




# 2.图表的自适应chart.resize()

### 单图表情况下使用 

> 需要添加定时  否则不起作用

```
myChart.setOption(option);
setTimeout(function (){
    window.onresize = function () {
    	myChart.resize();
    }
},200)
```

### 多图表情况下使用
来源：[https://www.cnblogs.com/goloving/p/9008165.html](https://www.cnblogs.com/goloving/p/9008165.html)

> 分别给单个组件添加时间监听

```
myChart.setOption(option);
window.addEventListener("resize", () => { myChart.resize();});
```

> 多个图表可以使用addEventListener

```
window.addEventListener("resize", () => { 
    this.myChart.resize();  
    this.myChart2.resize();  
    this.myChart3.resize();
});
```