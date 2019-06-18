# JS常见DOM节点操作示例【创建 ，插入，删除，复制，查找】

> 这篇文章主要介绍了JS常见DOM节点操作,结合实例形式分析了JavaScript针对DOM节点的创建 ，插入，删除，复制，查找等操作相关函数与使用技巧

**DOM含义**：DOM是文档对象模型(Document Object Model，是基于浏览器编程的一套API接口，是W3C出台的推荐标准。其赋予了JS操作节点的能力。当网页被加载时，浏览器就会创建页面的文档对象模型。

**节点**：根据 W3C 的 HTML DOM 标准，HTML 文档中的所有内容都是节点：

1. 整个文档时一个文档节点。
2. 每个HTML元素是元素节点。
3. HTML元素内的文本是文本节点。
4. 每个HTML属性是属性节点。
5. 每个注释是注释节点。

*所以HTML DOM 将 HTML 文档视作树结构，这种结构被称为节点树。通过 HTML DOM，节点树中的所有节点都可以通过 JS 进行访问。所有 HTML 元素（节点）均可被修改。*

## 一、创建节点、追加节点

1、`createElement`（标签名）创建一个元素节点（具体的一个元素）。
2、`appendChild`（节点）追加一个节点。
3、`createTextNode`（节点文本内容）创建一个文本节点

```
var oDiv = document.createElement("div");//创建一个div元素，因为是document对象的方法。
var oDivText = document.createTextNode("666");//创建一个文本节点内容是“666”，因为是document对象的方法。
oDiv.appendChild(oDivText);//父级.appendChild(子节点);在div元素中添加“666”
document.body.appendChild(oDiv);//父级.appendChild(子节点);;document.body是指向<body>元素
document.documentElement.appendChild(createNode);//父级.appendChild(子节点);;document.document
```

## 二、插入节点

1、`appendChild`（节点）也是一种插入节点的方式，还可以添加已经存在的元素，会将其元素从原来的位置移到新的位置。
2、`insertBefore`（a,b）是参照节点，意思是a节点会插入b节点的前面。
3、`insertAfter`（a,b）是参照节点，意思是a节点会插入b节点的后面。

```
var oDiv = document.createElement("div");//创建一个div元素，因为是document对象的方法。
var oDiv1 = document.getElementById("div1");
document.body.insertBefore(oDiv,oDiv1);//在oDiv1节点前插入新创建的元素节点
ul.appendChild(ul.firstChild); //把ul的第一个元素节点移到ul子节点的末尾
```

## 三、删除、移除节点

1、`removeChild`(节点) 删除一个节点，用于移除删除一个参数（节点）。其返回的被移除的节点，被移除的节点仍在文档中，只是文档中已没有其位置了。

```
var removeChild = document.body.removeChild(div1);//移除document对象的方法div1
```

## 四、替换节点

1、`replaceChild`(插入的节点，被替换的节点) ，用于替换节点，接受两个参数，第一参数是要插入的节点，第二个是要被替换的节点。返回的是被替换的节点。

```
var replaceChild= document.body.replaceChild(div1,div2); //将div1替换div2
```

## 五、查找节点

```
getElementsByTagName() //通过标签名称

getElementsByClassName() //通过元素的class属性名称

getElementById() //通过元素 Id，唯一性
```

1. childNodes 包含文本节点和元素节点的子节点。
```
for (var i = 0; i < oList.childNodes.length; i++) {//oList是做的ul的对象。
//nodeType是节点的类型，利用nodeType来判断节点类型，再去控制子节点
//nodeType==1 是元素节点
//nodeType==3 是文本节点
  if (oList.childNodes[i].nodeType == 1) {//查找到oList内的元素节点
    console.log(oList.childNodes[i]);//在控制器日志中显示找到的元素节点
  }
}
```

2、

**A、children也可以获取子节点，而且兼容各种浏览器。包括IE6-8**

**B、parentNode：获取父节点**
```
var oList = document.getElementById('list');//oList是做的ul的对象
var oChild=document.getElementById('child');//oChild是做的ul中的一个li的对象
//通过子节点查找父节点//parentNode：获取父节点
console.log(oChild.parentNode);//在控制器日志中显示父节点
console.log(oList.children);//在控制器日志中显示oList子节点
console.log(children.length)//子节点的个数
```

3、

**A、firstChild ; firstElementChild查找第一个子节点。此存在浏览器兼容问题：firstChild是IE兼容，firstElementChild是非IE兼容。**
```
//查找第一个子节点的封装函数
function firstChild(ele) {
  if (ele.firstElementChild) {//如果该条件是true则在该浏览器（IE或非IE）中兼容
    return ele.firstElementChild;
  } else {
    return ele.firstChild;
  }
}
firstChild(oList).style.background = 'red';//将获得的节点的背景变成红色
```

**B、lastChild ; lastElementChild查找最后一个子节点。此存在浏览器兼容问题：lastChild 是IE兼容，lastElementChild是非IE兼容。**
```
//查找最后一个子节点的封装函数
function lastChild(ele) {
  if (ele.lastElementChild) {//如果该条件是true则在该浏览器（IE或非IE）中兼容
    return ele.lastElementChild;
  } else {
    return ele.lastChild;
  }
}
lastChild(oList).style.background = 'red';//将获得的节点的背景变成红色
```

**C、nextSibling ; nextElementSibling查找下一个兄弟节点。也是存在兼容性问题。**
```
//查找下一个兄弟节点的封装函数
function nextSibling(ele) {
  if (ele.nextElementSibling) {
    return ele.nextElementSibling;
  } else {
    return ele.nextSibling;
  }
}
nextSibling(oMid).style.background = 'red';
```
**D、previousSibling ; previousElementSibling查找上一个兄弟节点。也是存在兼容性问题。**
```
//查找上一个兄弟节点的封装函数
function previousSibling(ele) {
  if (ele.nextElementSibling) {
    return ele.previousElementSibling;
  } else {
    return ele.previousSibling;
  }
}
previousSibling(oMid).style.background = 'red';
```

## 六、复制节点

`cloneNode()`方法可以复制一个节点，该方法能够给节点创建一个副本。

cloneNode()方法可以复制一个节点，该方法能够给节点创建一个副本。
	
`var ele = node.cloneNode(deep);
`		
deep是一个逻辑值：
			
参数值为true时，复制的节点将包含多有子节点内容；
			
参数值为false时，赋值的节点仅包含指定对象本身，不包含任何子节点。如果被复制的节点时一个元素节点，其包含的所有文本将不会被父子，因为这些文本是一个节点，但是属性节点将被复制。
	
cloneNode()方法复制的新节点与被复制节点具有一样的nodeName和nodeType属性



```
window.onload = function() {

    var p = document.createElement("p");
	
    var p1 = p.cloneNode(false);
	
    var info = "nodeName: " + p1.nodeName;
	
    info += ", nodeType: " + p1.nodeType;
	
    alert(info);//nodeName: P, nodeType: 1

} 
```

**注：**

nodeType 属性返回以数字值返回指定节点的节点类型。

如果节点是元素节点，则 nodeType 属性将返回 1。

如果节点是属性节点，则 nodeType 属性将返回 2。






