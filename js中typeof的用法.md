# JS��typeof���÷�

> js��һ�������ԣ�������������ʱ����ȷ�����������ͣ�js������ʱ���Զ��жϡ���ô����ж�һ�������������أ�js�ṩ��typeof��������������һ�����������͡�

**1. typeof���﷨**

typeof��һ�����������2��ʹ�÷�ʽ��typeof(���ʽ)��typeof ����������һ���ǶԱ��ʽ�����㣬�ڶ����ǶԱ��������㡣

**2. typeof�ķ���ֵ**
typeof������ķ�������Ϊ�ַ�����ֵ�������¼��֣�? ? ? ? 

1. 'undefined'? ? ? ?--δ����ı�����ֵ? ? ? ? 
2. 'boolean'? ? ? ?  --�������͵ı�����ֵ? ? ? ? 
3. 'string'? ? ? ? ?--�ַ������͵ı�����ֵ? ? ? ? 
4. 'number'? ? ? ? ?--�������͵ı�����ֵ? ? ? ? 
5. 'object'? ? ? ? ?--�������͵ı�����ֵ������null(�����js��ʷ�������⣬��null��Ϊobject���ʹ���)? ? ? ? 
6. 'function'? ? ? ? --�������͵ı�����ֵ?

**3. �򵥵�ʾ��**
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


