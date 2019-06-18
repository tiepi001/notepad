# JS中typeof的用法

> js是一门弱语言，它在声明变量时无需确定变量的类型，js在运行时会自动判断。那么如何判断一个变量的类型呢，js提供了typeof运算符，用来检测一个变量的类型。

**1. typeof的语法**

typeof是一个运算符，有2种使用方式：typeof(表达式)和typeof 变量名，第一种是对表达式做运算，第二种是对变量做运算。

**2. typeof的返回值**
typeof运算符的返回类型为字符串，值包括如下几种：? ? ? ? 

1. 'undefined'? ? ? ?--未定义的变量或值? ? ? ? 
2. 'boolean'? ? ? ?  --布尔类型的变量或值? ? ? ? 
3. 'string'? ? ? ? ?--字符串类型的变量或值? ? ? ? 
4. 'number'? ? ? ? ?--数字类型的变量或值? ? ? ? 
5. 'object'? ? ? ? ?--对象类型的变量或值，或者null(这个是js历史遗留问题，将null作为object类型处理)? ? ? ? 
6. 'function'? ? ? ? --函数类型的变量或值?

**3. 简单的示例**
console.log(typeof a);? ?  //'undefined'? ??
console.log(typeof(true));? //'boolean'? ? 
console.log(typeof '123');? //'string'? ? 
console.log(typeof 123);? ?//'number'? ??
console.log(typeof NaN);? ?//'number'? ? console.log(typeof null);?  //'object'? ??? ? 
var obj = new String();? ? 
console.log(typeof(obj));?  //'object'? ? 
var? fn = function(){};? ? 
console.log(typeof(fn));?   //'function'? ??
console.log(typeof(class c{}));? //'function'


