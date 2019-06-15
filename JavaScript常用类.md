## JavaScript������

1. Number
2. ʱ��
3. �ַ���
4. ����
5. Math
6. ����

### Number

1. ��������
```
������10 <br/>
С����3.14 <br/>
��ѧ��������1e5 | 1e-5 <br/>
�������Infinity | -Infinity <br/>
```

2. ���ý���
```
�����ƣ�0b1020 <br/>
�˽��ƣ�012 <br/>
ʮ���ƣ�10 <br/>
ʮ�����ƣ�0xA
```

3. NaN
```
���������ͣ�ͨ��isNaN()�����ж�
```

4. ���ó���
```
���ֵ��MAX_VALUE(1.7976931348623157e+308) <br/>
��Сֵ��MIN_VALUE(5e-324) <br/>
�������NEGATIVE_INFINITY | POSITIVE_INFINITY(Infinity | -Infinity)
```

5. ����ʵ������
```
toExponential(n) => 3.14.toExponential(1) => 1.3e+1 (�ȿ�ѧ��������ȷ�����ȣ�nΪС������) <br/>
toFixed(n) => 3.14.toFixed(1) => 3.1 (��ȷ�����ȣ�����ͨ������nΪС������) <br/>
toPrecision(n) => 13.14.toPrecision(1|2) => 1e+1|13 (��ȷ�����ȣ��ټ�����nΪλ������) <br/>
toString() => 
```

### ʱ��

1. ��������ȡʱ��
```var date = new Date();```

2. ʱ���
```date.getTime();```

3. ��ȡʱ��
```
�꣺date.getFullYear() <br/>
�£�date.getMonth() + 1 <br/>
�գ�date.getDate() <br/>
���ڣ�date.getDay() <br/>
Сʱ��date.getHours() <br/>
���ӣ�date.getMinutes() <br/>
�룺date.getSeconds() <br/>
���룺date.getMilliseconds()
```
4. ������ʽʱ��
```
getUTCFullYear() <br/>
getUTCDate() <br/>
getUTCHours()
```

### �ַ���

1.  �����ַ���
```'string' | "string" | 'my name is "zero"' | "I'm boy" | "I \"love\" you"```

2. ��������
```length���ַ�������```

3.  ���÷���
```
chartAt(n)��ָ�������ַ���ͬ[n] <br/>
concat(str)����Ŀ���ַ���ƴ�ӵ�ָ���ַ���֮�� <br/>
indexOf(str)��ָ���ַ�����һ�γ��ֵ�λ�� <br/>
lastIndexOf(str)��ָ���ַ�����һ�γ��ֵ�λ�� <br/>
replace(re, str)��������ƥ�䵽���ַ����滻Ϊָ���ַ��� <br/>
substr(n, m)��������n��ʼ����ȡm���ַ�����(mʡ�Դ����ȡ�����) <br/>
substring(n, m)��������n��ʼ����ȡ������m(mʡ�Դ����ȡ�����) <br/>
slice(n, m)��ͬsubstring(n, m) <br/>
split(re)����ָ�������ַ������Ϊ���� <br/>
toUpperCase()��ת��Ϊ��д <br/>
toLowerCase()��ת��ΪСд <br/>
trim()��ȥ����β�հ��ַ�
```

### ����

1. ��������
```[1, 2, 3] | ['1', '2', '3'] | [1, '2', true]```

2. ��������
```length������Ԫ�ظ���```

3. ���û�������
```
concat(arr)����Ŀ������ƴ�ӵ�ָ������֮�� <br/>
indexOf(ele)��ָ��Ԫ�ص�һ�γ��ֵ�λ�� <br/>
lastIndexOf(ele)��ָ��Ԫ����һ�γ��ֵ�λ�� <br/>
reverse()����ת���� <br/>
includes(ele, n)��������n��ʼ����Ԫ��ele�Ƿ��������У���ȫ��ƥ�䣬������ͷ��ʼn����ʡ��(inֻ��ֵƥ��) <br/>
fill(ele)����ָ��Ԫ������������� <br/>
slice(n, m)��������n��ʼ����ȡ������m(mʡ�Դ����ȡ�����) <br/>
join(str)����ָ���ַ������ӳ��ַ���
```

4. ��ɾ�ķ���
```
push(ele)����β�� <br/>
unshift(ele)����ͷ�� <br/>

pop()����βɾ <br/>
shift()����ͷɾ <br/>

splice(begin, length, ...eles)�������ɾ�� <br/>
// begin��ʼ���� <br/>
// length���� <br/>
// ��Ԫ����(����ʡ��) <br/>
```

5. �ص���������
```
filter(function(value, index){ return true | false})�������� <br/>
every(function(value, index){ return �������ʽ; })��ȫ���������� <br/>
some(function(value, index){ return �������ʽ; })�������������� <br/>
reduce(function(prev,value,index){ return prev * value; })���ۻ� <br/>
sort(function(o, n){ return o > n })������������
```


### Math

1. ���ó���
```
E�������������� e������Ȼ�����ĵ�����Լ����2.718�� <br/>
LN2������ 2 ����Ȼ������Լ����0.693�� <br/>
LN10������ 10 ����Ȼ������Լ����2.302�� <br/>
LOG2E�������� 2 Ϊ�׵� e �Ķ�����Լ���� 1.4426950408889634�� <br/>
LOG10E�������� 10 Ϊ�׵� e �Ķ�����Լ����0.434�� <br/>
PI������Բ���ʣ�Լ����3.14159��
```

2.���÷���
```
 abs(x)������ x �ľ���ֵ <br/>
ceil(x)������ȡ�� <br/>
floor(x)������ȡ�� <br/>
max(...n)�������ֵ <br/>
min(...n)������Сֵ <br/>
pow(x,y)������ x �� y ���� <br/>
random()������ 0 ~ 1 ֮�������� <br/>
round(x)����������
```


### ����

1. �������
```
// ���캯��
var re = new RegExp('^\\w', 'igm');
// ������
var re = /^\w/igm;
```

2. ���η�
```
i�������ִ�Сд <br/>
g��ȫ��ƥ�� <br/>
m������ƥ��
```

3. ���򷽷�
```
test()��ƥ��Ŀ���ַ��������Ϊtrue|false <br/>
exec()��ƥ��Ŀ���ַ��������Ϊ��һ�����������Ϣ������
```

4. �ַ�������
```
match(re)��ƥ��ָ�����򣬽��Ϊ����(��ȫ��ƥ��) <br/>
search(re)��ƥ��ָ�����򣬽��Ϊƥ�����������֮-1 <br/>
replace(re, newStr)��ƥ��ָ�������滻ƥ��Ľ��(��ȫ��ƥ��) <br/>
split(re, n)����������в�֣�n��ֵ���Ծ�����������鳤��(��ѡ����)
```









