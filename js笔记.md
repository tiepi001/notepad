### 浏览器两大部分 
1、shell 用户能操作看到的部分
2、内核部门
（1）、渲染引擎（语法规则和渲染） 
（2）、js引擎 
（3）、其他模块 辅助异步等其他


### js是一种解释性语言特点  
1、读一行翻译一行  
2、单线程  ECMA标准

> 编译性语言 c c++  
优点：快 
不足：移植性不好（不跨平台）

java --> javac --> 编译 --> .class -->jvm -- 解释执行  跨平台


### 解释性语言    
> js php python 
优点：跨平台 
不足：稍微慢


- 网站页面为异步加载执行模式

### js三大部分
1. ecmascript 
2. DOM 
3. BOM


### 主流浏览器及内核
IE            trident
Chrome        webkit/blink
firefox       Gecko
Opera         presto
Safari        webkit


### 命名规则
1. 变量名必须以英文字母、_、$开头
2. 变量名可以包括英文字母、_、数字
3. 不可以用系统的关键字、保留字作为变量名



值类型   重点 - 没理解---------

原始值 存在栈里 stack   原始值不可改变
Number String Bollean undefined null
栈内存赋值是拷贝

引用值 存在堆里 heap
array Object function date RegExp


赋值的顺序 自右向左， 计算的顺序 自左向右



### 运算操作符
“+”
1. 数学运算、字符串连接
2. 任何数据类型加字符串都等于字符串

> “-”  “*”  “/”  “%”  “=”  “()” 

优先级  “=”  最弱  “()”优先级最高 

“++”  “--”  “+=”  “-=”  “/=”  “*=”  “5=” 
 
 
a++  先运行a  后++ 
 
++a  先++  再运行a



3. 逻辑运算符   &&与   ||或   ！非    与运算符碰到假就停  或运算符碰到真就停


- &&运算符

> 先看第一表达式转换成布尔值的结果，如果结果为真，他会看第二个表达式转换成
布尔值的结果，然后如果只有两个表达式的话，只看看到第二个表达式，就可以返
回该表达式的值了
如果第一个表达式转换成布尔值的结果为假，则返回第一个表达式的值

var = 0 && 1  返回0
var = 1 && 2  返回2


- ！非    转换成布尔值再取反


> undefined, null, NaN, "", 0， false   ==>  转换成布尔值为false 
 
 
while循环是 for 循环的简化版



-------

- 条件补充语句  switch case         break        continue


switch case语句
```
var n = parseInt(window.prompt('input'));

    switch(n){
        case "a":
        case "b":
            console.log('a');
            break;
        case 3:
            console.log('true');
            break;
    }
```

break语句    break必须写到循环里面
```
var i = 0;
while(1){
  i++;
  console.log(i);
  if(i > 100){
    break;
  }
}
```
continue语句  终止本次循环进行下一次循环



引用值


对象

var deng = {
        laseName:"Deng",
        age:"20"
    }
    console.log(deng.laseName);
    deng.laseName = "Old Deng";



### 编程形式的区别


1. 面向过程

2. 面向对象

> JavaScript  既面向过程 又面向对象

- type of  可返回六个值

> number string Boolean object undefined  function


显示类型转换

var demo = true;
var num = Number(demo);转换成数字
console.log(typeof((num) + ":" + num));





### 函数

- 定义  名称首字母小写 后面词首字母大写

- 函数声明
```
   function theFirstName(){
       
   }
```
1. 命名函数表达式
```
var test = function abc(){  
  //test的函数名为abc
}
```
2. 匿名函数表达式 --- 函数表达式
```
var demo= function(){  
  //demo的函数名为demo

}
```



### 组成形式

1. 函数名称
2. 参数

```
     function test(a,b){  
         //test为函数名  
           a,b为参数  相当于定义了a b变量
     }


     //形式参数 --- 形参
     function sum(a,b){
        var c = a + b;
        document.write(c);
     }
     //实际参数 --- 实参
     sum(1,2)

     // 形参 和 实参数量没有限制

     sum.length         代表形参长度
     arguments.length   代表实参长度
```

### 递归
> 缺点：递归处理速度慢   优点：减少工作量

- n的阶乘 n！

```
  function mul(n){
    if(n == 1 || n == 0){
      return 1;
    }
    return n * mul(n - 1);
  }
```


### 闭包



- 函数声明整体提升
- 变量 声明提升

#### 预编译前奏
1. imply global暗示全局变量：即任何变量，如果变量未经声明就赋值，此变量就为全局对象所有`
a = 10
`
相当于
`
window.a = 10
`

2. 一切声明的全局变量，全是window的属性
`
var a = 123;
`
等同于
`
window.a = 123
`

### 预编译

function fn(a){
  console.log(a);

  var a = 123;
  console.log(a);
}

> 预编译发生在函数执行的前一刻

> 四部曲：
  1.创建AO对象（执行期上下文）
  2.找形参和变量声明


















