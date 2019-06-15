## JavaScript常用类

1. Number
2. 时间
3. 字符串
4. 数组
5. Math
6. 正则

### Number

1. 常用数字
```
整数：10 <br/>
小数：3.14 <br/>
科学计数法：1e5 | 1e-5 <br/>
正负无穷：Infinity | -Infinity <br/>
```

2. 常用进制
```
二进制：0b1020 <br/>
八进制：012 <br/>
十进制：10 <br/>
十六进制：0xA
```

3. NaN
```
非数字类型，通过isNaN()进行判断
```

4. 常用常量
```
最大值：MAX_VALUE(1.7976931348623157e+308) <br/>
最小值：MIN_VALUE(5e-324) <br/>
正负无穷：NEGATIVE_INFINITY | POSITIVE_INFINITY(Infinity | -Infinity)
```

5. 常用实例方法
```
toExponential(n) => 3.14.toExponential(1) => 1.3e+1 (先科学记数，再确定精度，n为小数精度) <br/>
toFixed(n) => 3.14.toFixed(1) => 3.1 (先确定精度，再普通记数，n为小数精度) <br/>
toPrecision(n) => 13.14.toPrecision(1|2) => 1e+1|13 (先确定精度，再记数，n为位数进度) <br/>
toString() => 
```

### 时间

1. 创建并获取时间
```var date = new Date();```

2. 时间戳
```date.getTime();```

3. 获取时间
```
年：date.getFullYear() <br/>
月：date.getMonth() + 1 <br/>
日：date.getDate() <br/>
星期：date.getDay() <br/>
小时：date.getHours() <br/>
分钟：date.getMinutes() <br/>
秒：date.getSeconds() <br/>
毫秒：date.getMilliseconds()
```
4. 常见格式时间
```
getUTCFullYear() <br/>
getUTCDate() <br/>
getUTCHours()
```

### 字符串

1.  常用字符串
```'string' | "string" | 'my name is "zero"' | "I'm boy" | "I \"love\" you"```

2. 常用属性
```length：字符串长度```

3.  常用方法
```
chartAt(n)：指定索引字符，同[n] <br/>
concat(str)：将目标字符串拼接到指定字符串之后 <br/>
indexOf(str)：指定字符串第一次出现的位置 <br/>
lastIndexOf(str)：指定字符串最一次出现的位置 <br/>
replace(re, str)：将正则匹配到的字符串替换为指定字符串 <br/>
substr(n, m)：从索引n开始，截取m个字符长度(m省略代表截取到最后) <br/>
substring(n, m)：从索引n开始，截取到索引m(m省略代表截取到最后) <br/>
slice(n, m)：同substring(n, m) <br/>
split(re)：以指定正则将字符串拆分为数组 <br/>
toUpperCase()：转换为大写 <br/>
toLowerCase()：转换为小写 <br/>
trim()：去除首尾空白字符
```

### 数组

1. 常见数组
```[1, 2, 3] | ['1', '2', '3'] | [1, '2', true]```

2. 常用属性
```length：数组元素个数```

3. 常用基础方法
```
concat(arr)：将目标数组拼接到指定数组之后 <br/>
indexOf(ele)：指定元素第一次出现的位置 <br/>
lastIndexOf(ele)：指定元素最一次出现的位置 <br/>
reverse()：反转数组 <br/>
includes(ele, n)：从索引n开始往后，元素ele是否在数组中，做全等匹配，索引从头开始n可以省略(in只做值匹配) <br/>
fill(ele)：以指定元素填充整个数组 <br/>
slice(n, m)：从索引n开始，截取到索引m(m省略代表截取到最后) <br/>
join(str)：以指定字符串连接成字符串
```

4. 增删改方法
```
push(ele)：从尾加 <br/>
unshift(ele)：从头加 <br/>

pop()：从尾删 <br/>
shift()：从头删 <br/>

splice(begin, length, ...eles)：完成增删改 <br/>
// begin开始索引 <br/>
// length长度 <br/>
// 新元素们(可以省略) <br/>
```

5. 回调函数方法
```
filter(function(value, index){ return true | false})：过滤器 <br/>
every(function(value, index){ return 条件表达式; })：全部满足条件 <br/>
some(function(value, index){ return 条件表达式; })：部分满足条件 <br/>
reduce(function(prev,value,index){ return prev * value; })：累积 <br/>
sort(function(o, n){ return o > n })：正逆向排序
```


### Math

1. 常用常量
```
E：返回算术常量 e，即自然对数的底数（约等于2.718） <br/>
LN2：返回 2 的自然对数（约等于0.693） <br/>
LN10：返回 10 的自然对数（约等于2.302） <br/>
LOG2E：返回以 2 为底的 e 的对数（约等于 1.4426950408889634） <br/>
LOG10E：返回以 10 为底的 e 的对数（约等于0.434） <br/>
PI：返回圆周率（约等于3.14159）
```

2.常用方法
```
 abs(x)：返回 x 的绝对值 <br/>
ceil(x)：向上取整 <br/>
floor(x)：向下取整 <br/>
max(...n)：求最大值 <br/>
min(...n)：求最小值 <br/>
pow(x,y)：返回 x 的 y 次幂 <br/>
random()：返回 0 ~ 1 之间的随机数 <br/>
round(x)：四舍五入
```


### 正则

1. 正则对象
```
// 构造函数
var re = new RegExp('^\\w', 'igm');
// 字面量
var re = /^\w/igm;
```

2. 修饰符
```
i：不区分大小写 <br/>
g：全文匹配 <br/>
m：多行匹配
```

3. 正则方法
```
test()：匹配目标字符串，结果为true|false <br/>
exec()：匹配目标字符串，结果为第一条结果所有信息的数组
```

4. 字符串方法
```
match(re)：匹配指定正则，结果为数组(可全文匹配) <br/>
search(re)：匹配指定正则，结果为匹配的索引，反之-1 <br/>
replace(re, newStr)：匹配指定正则，替换匹配的结果(可全文匹配) <br/>
split(re, n)：按正则进行拆分，n的值可以决定结果的数组长度(可选参数)
```









