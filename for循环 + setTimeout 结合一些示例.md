# for循环 + setTimeout 结合一些示例

## setTimeout 和 setInterval 的执行机制

在日常编码中，你会发现，给 setTimeout 和 setInterval 设定延迟时间往往并不准，或者干脆 setTimeout(function(){xxx},0) 也不是立马执行（特别是有耗时代码在前），这是因为 js 是单线程的，有一个事件队列机制，setTimeout 和 setInterval 的回调会到了延迟时间塞入事件队列中，排队执行。

setTimeout ：延时 delay 毫秒之后，啥也不管，直接将回调函数加入事件队列。
setTimeout的异步方式，当执行到setTimeout时，此任务先暂停并保存，继续执行后续任务，当条件满足时，再将setTimeout的执行任务放回任务队列的后面，等待执行

setInterval ：延时 delay 毫秒之后，先看看事件队列中是否存在还没有执行的回调函数（ setInterval 的回调函数），如果存在，就不要再往事件队列里加入回调函数了。

**看下面示例：**

```
for (var i = 0; i < 5; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

*结果：1 秒之后，同时输出 5 个 5。*

> 因为 for 循环会先执行完（同步优先于异步优先于回调），这时五个 setTimeout 的回调全部塞入了事件队列中，然后 1 秒后一起执行了。

## 正文

**接下来就是那道经典的代码：**

```
for (var i = 0; i < 5; i++) { 
  setTimeout(function (){
    console.log(i); 
   },1000); 
}
```

**结果：**5 5 5 5 5

为什么不是 1 2 3 4 5，问题出在作用域上。

因为 setTimeout 的 console.log(i); 的i是 var 定义的，所以是函数级的作用域，不属于 for 循环体，属于 global。等到 for 循环结束，i 已经等于 5 了，这个时候再执行 setTimeout 的五个回调函数（参考上面对事件机制的阐述），里面的 console.log(i); 的 i 去向上找作用域，只能找到 global下 的 i，即 5。所以输出都是 5。

**解决办法：人为给 console.log(i); 创造作用域，保存i的值。**

**解决办法一**
```
for (var i = 0; i < 5; i++) { 
  (function(i){   //立刻执行函数
    setTimeout(function (){
      console.log(i); 
     },1000); 
  })(i); 
}
```
这里用到立刻执行函数。这样 console.log(i); 中的i就保存在每一次循环生成的立刻执行函数中的作用域里了。

**解决办法二**
```
for (let i = 0; i < 5; i++) {   //let 代替 var
  setTimeout(function (){
    console.log(i); 
   },1000); 
}
```
let 为代码块的作用域，所以每一次 for 循环，console.log(i); 都引用到 for 代码块作用域下的i，因为这样被引用，所以 for 循环结束后，这些作用域在 setTimeout 未执行前都不会被释放。

## 补充

在写示例代码的过程中，发现一个语法点：

```
function a(i){ 
  console.log(i);  
}
for (var i = 0; i < 5; i++) { 
  setTimeout(a(i),1000); 
} 
```
报错：
```
TypeError: "callback" argument must be a function
at setTimeout (timers.js:421:11)
……
```
百度了下，原来 setTimeout 不支持传带参数的函数，可以再用一个匿名函数包装下它吧，见下面代码：
```
function a(i){ 
  console.log(i);  
}
for (var i = 0; i < 5; i++) { 
  setTimeout(function(){ //用匿名函数包装
    a(i);
  },1000); 
} 
```
**总结**

以上所述是小编给大家介绍的for循环 + setTimeout 结合一些示例(前端面试题），希望对大家有所帮助，如果大家有任何疑问请给我留言，小编会及时回复大家的。在此也非常感谢大家对脚本之家网站的支持！














