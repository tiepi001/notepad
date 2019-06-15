## JavaScript������

1. Number
2. ʱ��
3. �ַ���
4. ����
5. Math
6. ����

### һ��Number

1. ��������
```
������10 
С����3.14 
��ѧ��������1e5 | 1e-5 
�������Infinity | -Infinity 
```

2. ���ý���
```
�����ƣ�0b1020 
�˽��ƣ�012 
ʮ���ƣ�10 
ʮ�����ƣ�0xA
```

3. NaN
```
���������ͣ�ͨ��isNaN()�����ж�
```

4. ���ó���
```
���ֵ��MAX_VALUE(1.7976931348623157e+308) 
��Сֵ��MIN_VALUE(5e-324) 
�������NEGATIVE_INFINITY | POSITIVE_INFINITY(Infinity | -Infinity)
```

5. ����ʵ������
```
toExponential(n) => 3.14.toExponential(1) => 1.3e+1 (�ȿ�ѧ��������ȷ�����ȣ�nΪС������) 
toFixed(n) => 3.14.toFixed(1) => 3.1 (��ȷ�����ȣ�����ͨ������nΪС������) 
toPrecision(n) => 13.14.toPrecision(1|2) => 1e+1|13 (��ȷ�����ȣ��ټ�����nΪλ������) 
toString() => 
```

### ����ʱ��

1. ��������ȡʱ��
```var date = new Date();```

2. ʱ���
```date.getTime();```

3. ��ȡʱ��
```
�꣺date.getFullYear() 
�£�date.getMonth() + 1 
�գ�date.getDate() 
���ڣ�date.getDay() 
Сʱ��date.getHours() 
���ӣ�date.getMinutes() 
�룺date.getSeconds() 
���룺date.getMilliseconds()
```
4. ������ʽʱ��
```
getUTCFullYear() 
getUTCDate() 
getUTCHours()
```

### �����ַ���

1.  �����ַ���
```'string' | "string" | 'my name is "zero"' | "I'm boy" | "I \"love\" you"```

2. ��������
```length���ַ�������```

3.  ���÷���
```
chartAt(n)��ָ�������ַ���ͬ[n] 
concat(str)����Ŀ���ַ���ƴ�ӵ�ָ���ַ���֮�� 
indexOf(str)��ָ���ַ�����һ�γ��ֵ�λ�� 
lastIndexOf(str)��ָ���ַ�����һ�γ��ֵ�λ�� 
replace(re, str)��������ƥ�䵽���ַ����滻Ϊָ���ַ��� 
substr(n, m)��������n��ʼ����ȡm���ַ�����(mʡ�Դ����ȡ�����) 
substring(n, m)��������n��ʼ����ȡ������m(mʡ�Դ����ȡ�����) 
slice(n, m)��ͬsubstring(n, m) 
split(re)����ָ�������ַ������Ϊ���� 
toUpperCase()��ת��Ϊ��д 
toLowerCase()��ת��ΪСд 
trim()��ȥ����β�հ��ַ�
```

### �ġ�����

1. ��������
```[1, 2, 3] | ['1', '2', '3'] | [1, '2', true]```

2. ��������
```length������Ԫ�ظ���```

3. ���û�������
```
concat(arr)����Ŀ������ƴ�ӵ�ָ������֮�� 
indexOf(ele)��ָ��Ԫ�ص�һ�γ��ֵ�λ�� 
lastIndexOf(ele)��ָ��Ԫ����һ�γ��ֵ�λ�� 
reverse()����ת���� 
includes(ele, n)��������n��ʼ����Ԫ��ele�Ƿ��������У���ȫ��ƥ�䣬������ͷ��ʼn����ʡ��(inֻ��ֵƥ��) 
fill(ele)����ָ��Ԫ������������� 
slice(n, m)��������n��ʼ����ȡ������m(mʡ�Դ����ȡ�����) 
join(str)����ָ���ַ������ӳ��ַ���
```

4. ��ɾ�ķ���
```
push(ele)����β�� 
unshift(ele)����ͷ�� 

pop()����βɾ 
shift()����ͷɾ 

splice(begin, length, ...eles)�������ɾ�� 
// begin��ʼ���� 
// length���� 
// ��Ԫ����(����ʡ��) 
```

5. �ص���������
```
filter(function(value, index){ return true | false})�������� 
every(function(value, index){ return �������ʽ; })��ȫ���������� 
some(function(value, index){ return �������ʽ; })�������������� 
reduce(function(prev,value,index){ return prev * value; })���ۻ� 
sort(function(o, n){ return o > n })������������
```


### �塢Math

1. ���ó���
```
E�������������� e������Ȼ�����ĵ�����Լ����2.718�� 
LN2������ 2 ����Ȼ������Լ����0.693�� 
LN10������ 10 ����Ȼ������Լ����2.302�� 
LOG2E�������� 2 Ϊ�׵� e �Ķ�����Լ���� 1.4426950408889634�� 
LOG10E�������� 10 Ϊ�׵� e �Ķ�����Լ����0.434�� 
PI������Բ���ʣ�Լ����3.14159��
```

2.���÷���
```
 abs(x)������ x �ľ���ֵ 
ceil(x)������ȡ�� 
floor(x)������ȡ�� 
max(...n)�������ֵ 
min(...n)������Сֵ 
pow(x,y)������ x �� y ���� 
random()������ 0 ~ 1 ֮�������� 
round(x)����������
```


### ��������

1. �������
```
// ���캯��
var re = new RegExp('^\\w', 'igm');
// ������
var re = /^\w/igm;
```

2. ���η�
```
i�������ִ�Сд 
g��ȫ��ƥ�� 
m������ƥ��
```

3. ���򷽷�
```
test()��ƥ��Ŀ���ַ��������Ϊtrue|false 
exec()��ƥ��Ŀ���ַ��������Ϊ��һ�����������Ϣ������
```

4. �ַ�������
```
match(re)��ƥ��ָ�����򣬽��Ϊ����(��ȫ��ƥ��) 
search(re)��ƥ��ָ�����򣬽��Ϊƥ�����������֮-1 
replace(re, newStr)��ƥ��ָ�������滻ƥ��Ľ��(��ȫ��ƥ��) 
split(re, n)����������в�֣�n��ֵ���Ծ�����������鳤��(��ѡ����)
```









