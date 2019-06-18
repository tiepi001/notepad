# JS����DOM�ڵ����ʾ�������� �����룬ɾ�������ƣ����ҡ�

> ��ƪ������Ҫ������JS����DOM�ڵ����,���ʵ����ʽ������JavaScript���DOM�ڵ�Ĵ��� �����룬ɾ�������ƣ����ҵȲ�����غ�����ʹ�ü���

**DOM����**��DOM���ĵ�����ģ��(Document Object Model���ǻ����������̵�һ��API�ӿڣ���W3C��̨���Ƽ���׼���丳����JS�����ڵ������������ҳ������ʱ��������ͻᴴ��ҳ����ĵ�����ģ�͡�

**�ڵ�**������ W3C �� HTML DOM ��׼��HTML �ĵ��е��������ݶ��ǽڵ㣺

1. �����ĵ�ʱһ���ĵ��ڵ㡣
2. ÿ��HTMLԪ����Ԫ�ؽڵ㡣
3. HTMLԪ���ڵ��ı����ı��ڵ㡣
4. ÿ��HTML���������Խڵ㡣
5. ÿ��ע����ע�ͽڵ㡣

*����HTML DOM �� HTML �ĵ��������ṹ�����ֽṹ����Ϊ�ڵ�����ͨ�� HTML DOM���ڵ����е����нڵ㶼����ͨ�� JS ���з��ʡ����� HTML Ԫ�أ��ڵ㣩���ɱ��޸ġ�*

## һ�������ڵ㡢׷�ӽڵ�

1��`createElement`����ǩ��������һ��Ԫ�ؽڵ㣨�����һ��Ԫ�أ���
2��`appendChild`���ڵ㣩׷��һ���ڵ㡣
3��`createTextNode`���ڵ��ı����ݣ�����һ���ı��ڵ�

```
var oDiv = document.createElement("div");//����һ��divԪ�أ���Ϊ��document����ķ�����
var oDivText = document.createTextNode("666");//����һ���ı��ڵ������ǡ�666������Ϊ��document����ķ�����
oDiv.appendChild(oDivText);//����.appendChild(�ӽڵ�);��divԪ������ӡ�666��
document.body.appendChild(oDiv);//����.appendChild(�ӽڵ�);;document.body��ָ��<body>Ԫ��
document.documentElement.appendChild(createNode);//����.appendChild(�ӽڵ�);;document.document
```

## ��������ڵ�

1��`appendChild`���ڵ㣩Ҳ��һ�ֲ���ڵ�ķ�ʽ������������Ѿ����ڵ�Ԫ�أ��Ὣ��Ԫ�ش�ԭ����λ���Ƶ��µ�λ�á�
2��`insertBefore`��a,b���ǲ��սڵ㣬��˼��a�ڵ�����b�ڵ��ǰ�档
3��`insertAfter`��a,b���ǲ��սڵ㣬��˼��a�ڵ�����b�ڵ�ĺ��档

```
var oDiv = document.createElement("div");//����һ��divԪ�أ���Ϊ��document����ķ�����
var oDiv1 = document.getElementById("div1");
document.body.insertBefore(oDiv,oDiv1);//��oDiv1�ڵ�ǰ�����´�����Ԫ�ؽڵ�
ul.appendChild(ul.firstChild); //��ul�ĵ�һ��Ԫ�ؽڵ��Ƶ�ul�ӽڵ��ĩβ
```

## ����ɾ�����Ƴ��ڵ�

1��`removeChild`(�ڵ�) ɾ��һ���ڵ㣬�����Ƴ�ɾ��һ���������ڵ㣩���䷵�صı��Ƴ��Ľڵ㣬���Ƴ��Ľڵ������ĵ��У�ֻ���ĵ�����û����λ���ˡ�

```
var removeChild = document.body.removeChild(div1);//�Ƴ�document����ķ���div1
```

## �ġ��滻�ڵ�

1��`replaceChild`(����Ľڵ㣬���滻�Ľڵ�) �������滻�ڵ㣬����������������һ������Ҫ����Ľڵ㣬�ڶ�����Ҫ���滻�Ľڵ㡣���ص��Ǳ��滻�Ľڵ㡣

```
var replaceChild= document.body.replaceChild(div1,div2); //��div1�滻div2
```

## �塢���ҽڵ�

```
getElementsByTagName() //ͨ����ǩ����

getElementsByClassName() //ͨ��Ԫ�ص�class��������

getElementById() //ͨ��Ԫ�� Id��Ψһ��
```

1. childNodes �����ı��ڵ��Ԫ�ؽڵ���ӽڵ㡣
```
for (var i = 0; i < oList.childNodes.length; i++) {//oList������ul�Ķ���
//nodeType�ǽڵ�����ͣ�����nodeType���жϽڵ����ͣ���ȥ�����ӽڵ�
//nodeType==1 ��Ԫ�ؽڵ�
//nodeType==3 ���ı��ڵ�
  if (oList.childNodes[i].nodeType == 1) {//���ҵ�oList�ڵ�Ԫ�ؽڵ�
    console.log(oList.childNodes[i]);//�ڿ�������־����ʾ�ҵ���Ԫ�ؽڵ�
  }
}
```

2��

**A��childrenҲ���Ի�ȡ�ӽڵ㣬���Ҽ��ݸ��������������IE6-8**

**B��parentNode����ȡ���ڵ�**
```
var oList = document.getElementById('list');//oList������ul�Ķ���
var oChild=document.getElementById('child');//oChild������ul�е�һ��li�Ķ���
//ͨ���ӽڵ���Ҹ��ڵ�//parentNode����ȡ���ڵ�
console.log(oChild.parentNode);//�ڿ�������־����ʾ���ڵ�
console.log(oList.children);//�ڿ�������־����ʾoList�ӽڵ�
console.log(children.length)//�ӽڵ�ĸ���
```

3��

**A��firstChild ; firstElementChild���ҵ�һ���ӽڵ㡣�˴���������������⣺firstChild��IE���ݣ�firstElementChild�Ƿ�IE���ݡ�**
```
//���ҵ�һ���ӽڵ�ķ�װ����
function firstChild(ele) {
  if (ele.firstElementChild) {//�����������true���ڸ��������IE���IE���м���
    return ele.firstElementChild;
  } else {
    return ele.firstChild;
  }
}
firstChild(oList).style.background = 'red';//����õĽڵ�ı�����ɺ�ɫ
```

**B��lastChild ; lastElementChild�������һ���ӽڵ㡣�˴���������������⣺lastChild ��IE���ݣ�lastElementChild�Ƿ�IE���ݡ�**
```
//�������һ���ӽڵ�ķ�װ����
function lastChild(ele) {
  if (ele.lastElementChild) {//�����������true���ڸ��������IE���IE���м���
    return ele.lastElementChild;
  } else {
    return ele.lastChild;
  }
}
lastChild(oList).style.background = 'red';//����õĽڵ�ı�����ɺ�ɫ
```

**C��nextSibling ; nextElementSibling������һ���ֵܽڵ㡣Ҳ�Ǵ��ڼ��������⡣**
```
//������һ���ֵܽڵ�ķ�װ����
function nextSibling(ele) {
  if (ele.nextElementSibling) {
    return ele.nextElementSibling;
  } else {
    return ele.nextSibling;
  }
}
nextSibling(oMid).style.background = 'red';
```
**D��previousSibling ; previousElementSibling������һ���ֵܽڵ㡣Ҳ�Ǵ��ڼ��������⡣**
```
//������һ���ֵܽڵ�ķ�װ����
function previousSibling(ele) {
  if (ele.nextElementSibling) {
    return ele.previousElementSibling;
  } else {
    return ele.previousSibling;
  }
}
previousSibling(oMid).style.background = 'red';
```

## �������ƽڵ�

`cloneNode()`�������Ը���һ���ڵ㣬�÷����ܹ����ڵ㴴��һ��������

cloneNode()�������Ը���һ���ڵ㣬�÷����ܹ����ڵ㴴��һ��������
	
`var ele = node.cloneNode(deep);
`		
deep��һ���߼�ֵ��
			
����ֵΪtrueʱ�����ƵĽڵ㽫���������ӽڵ����ݣ�
			
����ֵΪfalseʱ����ֵ�Ľڵ������ָ���������������κ��ӽڵ㡣��������ƵĽڵ�ʱһ��Ԫ�ؽڵ㣬������������ı������ᱻ���ӣ���Ϊ��Щ�ı���һ���ڵ㣬�������Խڵ㽫�����ơ�
	
cloneNode()�������Ƶ��½ڵ��뱻���ƽڵ����һ����nodeName��nodeType����



```
window.onload = function() {

    var p = document.createElement("p");
	
    var p1 = p.cloneNode(false);
	
    var info = "nodeName: " + p1.nodeName;
	
    info += ", nodeType: " + p1.nodeType;
	
    alert(info);//nodeName: P, nodeType: 1

} 
```

**ע��**

nodeType ���Է���������ֵ����ָ���ڵ�Ľڵ����͡�

����ڵ���Ԫ�ؽڵ㣬�� nodeType ���Խ����� 1��

����ڵ������Խڵ㣬�� nodeType ���Խ����� 2��






