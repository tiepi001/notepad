### ��������󲿷� 
1��shell �û��ܲ��������Ĳ���
2���ں˲���
��1������Ⱦ���棨�﷨�������Ⱦ��
��2����js����
��3��������ģ�� �����첽������


### js��һ�ֽ����������ص�  
1����һ�з���һ��  
2�����߳�  ECMA��׼

> ���������� c c++ 
�ŵ㣺��
���㣺��ֲ�Բ��ã�����ƽ̨��

java --> javac --> ���� --> .class -->jvm -- ����ִ��  ��ƽ̨


### ����������    
> js php python
�ŵ㣺��ƽ̨
���㣺��΢��


- ��վҳ��Ϊ�첽����ִ��ģʽ

### js���󲿷�
1.ecmascript
2.DOM 
3.BOM


### ������������ں�
IE            trident
Chrome        webkit/blink
firefox       Gecko
Opera         presto
Safari        webkit


### ��������
1.������������Ӣ����ĸ��_��$��ͷ
2.���������԰���Ӣ����ĸ��_������
3.��������ϵͳ�Ĺؼ��֡���������Ϊ������



ֵ����   �ص� - û���---------

ԭʼֵ ����ջ�� stack   ԭʼֵ���ɸı�
Number String Bollean undefined null
ջ�ڴ渳ֵ�ǿ���

����ֵ ���ڶ��� heap
array Object function date RegExp


��ֵ��˳�� �������� �����˳�� ��������



### ���������
��+��
1.��ѧ���㡢�ַ�������
2.�κ��������ͼ��ַ����������ַ���

> ��-��  ��*��  ��/��  ��%��  ��=��  ��()��

���ȼ�  ��=��  ����  ��()�����ȼ����

��++��  ��--��  ��+=��  ��-=��  ��/=��  ��*=��  ��5=��


a++  ������a  ��++

++a  ��++  ������a



�߼������   &&��   ||��   ����    ������������پ�ͣ  ��������������ͣ


- &&�����

> �ȿ���һ���ʽת���ɲ���ֵ�Ľ����������Ϊ�棬���ῴ�ڶ������ʽת����
����ֵ�Ľ����Ȼ�����ֻ���������ʽ�Ļ���ֻ�������ڶ������ʽ���Ϳ��Է�
�ظñ��ʽ��ֵ��
�����һ�����ʽת���ɲ���ֵ�Ľ��Ϊ�٣��򷵻ص�һ�����ʽ��ֵ

var = 0 && 1  ����0
var = 1 && 2  ����2


- ����    ת���ɲ���ֵ��ȡ��


> undefined, null, NaN, "", 0�� false   ==>  ת���ɲ���ֵΪfalse


whileѭ���� for ѭ���ļ򻯰�



-------

- �����������  switch case         break        continue


switch case���
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

break���    break����д��ѭ������
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
continue���  ��ֹ����ѭ��������һ��ѭ��



����ֵ


����

var deng = {
        laseName:"Deng",
        age:"20"
    }
    console.log(deng.laseName);
    deng.laseName = "Old Deng";



### �����ʽ������


1.�������

2.�������

> JavaScript  ��������� ���������

- type of  �ɷ�������ֵ

> number string Boolean object undefined  function


��ʾ����ת��

var demo = true;
var num = Number(demo);ת��������
console.log(typeof((num) + ":" + num));





### ����

- ����  ��������ĸСд ���������ĸ��д

- ��������
```
   function theFirstName(){
       
   }
```
1.�����������ʽ
```
var test = function abc(){  
  //test�ĺ�����Ϊabc
}
```
2.�����������ʽ --- �������ʽ
```
var demo= function(){  
  //demo�ĺ�����Ϊdemo

}
```



### �����ʽ

1.��������
2.����

```
     function test(a,b){  
         //testΪ������  
           a,bΪ����  �൱�ڶ�����a b����
     }


     //��ʽ���� --- �β�
     function sum(a,b){
        var c = a + b;
        document.write(c);
     }
     //ʵ�ʲ��� --- ʵ��
     sum(1,2)

     // �β� �� ʵ������û������

     sum.length         �����βγ���
     arguments.length   ����ʵ�γ���
```

### �ݹ�
> ȱ�㣺�ݹ鴦���ٶ���   �ŵ㣺���ٹ�����

- n�Ľ׳� n��

```
  function mul(n){
    if(n == 1 || n == 0){
      return 1;
    }
    return n * mul(n - 1);
  }
```


### �հ�



- ����������������
- ���� ��������

#### Ԥ����ǰ��
1. imply global��ʾȫ�ֱ��������κα������������δ�������͸�ֵ���˱�����Ϊȫ�ֶ�������`
a = 10
`
�൱��
`
window.a = 10
`

2. һ��������ȫ�ֱ�����ȫ��window������
`
var a = 123;
`
��ͬ��
`
window.a = 123
`

### Ԥ����

function fn(a){
  console.log(a);

  var a = 123;
  console.log(a);
}

> Ԥ���뷢���ں���ִ�е�ǰһ��

> �Ĳ�����
  1.����AO����ִ���������ģ�
  2.���βκͱ�������


















