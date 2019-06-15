## JavaScript常用类

1. Number
2. 时间
3. 字符串
4. 数组
5. Math
6. 正则

### 一、Number

1. 常用数字
```
整数：10 
小数：3.14 
科学计数法：1e5 | 1e-5 
正负无穷：Infinity | -Infinity 
```

2. 常用进制
```
二进制：0b1020 
八进制：012 
十进制：10 
十六进制：0xA
```

3. NaN
```
非数字类型，通过isNaN()进行判断
```

4. 常用常量
```
最大值：MAX_VALUE(1.7976931348623157e+308) 
最小值：MIN_VALUE(5e-324) 
正负无穷：NEGATIVE_INFINITY | POSITIVE_INFINITY(Infinity | -Infinity)
```

5. 常用实例方法
```
toExponential(n) => 3.14.toExponential(1) => 1.3e+1 (先科学记数，再确定精度，n为小数精度) 
toFixed(n) => 3.14.toFixed(1) => 3.1 (先确定精度，再普通记数，n为小数精度) 
toPrecision(n) => 13.14.toPrecision(1|2) => 1e+1|13 (先确定精度，再记数，n为位数进度) 
toString() => 
```

### 二、时间

1. 创建并获取时间
```var date = new Date();```

2. 时间戳
```date.getTime();```

3. 获取时间
```
年：date.getFullYear() 
月：date.getMonth() + 1 
日：date.getDate() 
星期：date.getDay() 
小时：date.getHours() 
分钟：date.getMinutes() 
秒：date.getSeconds() 
毫秒：date.getMilliseconds()
```
4. 常见格式时间
```
getUTCFullYear() 
getUTCDate() 
getUTCHours()
```

### 三、字符串

1.  常用字符串
```'string' | "string" | 'my name is "zero"' | "I'm boy" | "I \"love\" you"```

2. 常用属性
```length：字符串长度```

3.  常用方法
```
chartAt(n)：指定索引字符，同[n] 
concat(str)：将目标字符串拼接到指定字符串之后 
indexOf(str)：指定字符串第一次出现的位置 
lastIndexOf(str)：指定字符串最一次出现的位置 
replace(re, str)：将正则匹配到的字符串替换为指定字符串 
substr(n, m)：从索引n开始，截取m个字符长度(m省略代表截取到最后) 
substring(n, m)：从索引n开始，截取到索引m(m省略代表截取到最后) 
slice(n, m)：同substring(n, m) 
split(re)：以指定正则将字符串拆分为数组 
toUpperCase()：转换为大写 
toLowerCase()：转换为小写 
trim()：去除首尾空白字符
```

### 四、数组

1. 常见数组
```[1, 2, 3] | ['1', '2', '3'] | [1, '2', true]```

2. 常用属性
```length：数组元素个数```

3. 常用基础方法
```
concat(arr)：将目标数组拼接到指定数组之后 
indexOf(ele)：指定元素第一次出现的位置 
lastIndexOf(ele)：指定元素最一次出现的位置 
reverse()：反转数组 
includes(ele, n)：从索引n开始往后，元素ele是否在数组中，做全等匹配，索引从头开始n可以省略(in只做值匹配) 
fill(ele)：以指定元素填充整个数组 
slice(n, m)：从索引n开始，截取到索引m(m省略代表截取到最后) 
join(str)：以指定字符串连接成字符串
```

4. 增删改方法
```
push(ele)：从尾加 
unshift(ele)：从头加 

pop()：从尾删 
shift()：从头删 

splice(begin, length, ...eles)：完成增删改 
// begin开始索引 
// length长度 
// 新元素们(可以省略) 
```

5. 回调函数方法
```
filter(function(value, index){ return true | false})：过滤器 
every(function(value, index){ return 条件表达式; })：全部满足条件 
some(function(value, index){ return 条件表达式; })：部分满足条件 
reduce(function(prev,value,index){ return prev * value; })：累积 
sort(function(o, n){ return o > n })：正逆向排序
```


### 五、Math

1. 常用常量
```
E：返回算术常量 e，即自然对数的底数（约等于2.718） 
LN2：返回 2 的自然对数（约等于0.693） 
LN10：返回 10 的自然对数（约等于2.302） 
LOG2E：返回以 2 为底的 e 的对数（约等于 1.4426950408889634） 
LOG10E：返回以 10 为底的 e 的对数（约等于0.434） 
PI：返回圆周率（约等于3.14159）
```

2.常用方法
```
 abs(x)：返回 x 的绝对值 
ceil(x)：向上取整 
floor(x)：向下取整 
max(...n)：求最大值 
min(...n)：求最小值 
pow(x,y)：返回 x 的 y 次幂 
random()：返回 0 ~ 1 之间的随机数 
round(x)：四舍五入
```


### 六、正则

1. 正则对象
```
// 构造函数
var re = new RegExp('^\\w', 'igm');
// 字面量
var re = /^\w/igm;
```

2. 修饰符
```
i：不区分大小写 
g：全文匹配 
m：多行匹配
```

3. 正则方法
```
test()：匹配目标字符串，结果为true|false 
exec()：匹配目标字符串，结果为第一条结果所有信息的数组
```

4. 字符串方法
```
match(re)：匹配指定正则，结果为数组(可全文匹配) 
search(re)：匹配指定正则，结果为匹配的索引，反之-1 
replace(re, newStr)：匹配指定正则，替换匹配的结果(可全文匹配) 
split(re, n)：按正则进行拆分，n的值可以决定结果的数组长度(可选参数)
```









