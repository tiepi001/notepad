# 去掉input等点击出现的边框

> 添加属性 :focus{outline:none} 就可以去掉默认点击时，边框会出现的蓝色边框。
提示：接收键盘事件或其他用户输入的元素都允许 :focus 选择器。

```
input,textarea,select,a,button:focus {
    outline: none;
}
```

- 用 :focus  实现外部边框改变颜色:

```
input:focus {
    outline:1px solid #7c448f;
}
```

- 用 :focus  实现内部边框改变颜色:

```
input:focus{
    border-color:#7c448f ;
    outline: none;
}
```


>- outline（轮廓）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。（outline是围绕元素。它是围绕元素的边距。但是，它是来自不同的边框属性，outline不是元素尺寸的一部分，因此     **元素的宽度和高度属性不包含轮廓的宽度**  ）<br/>
>- outline简写属性在一个声明中设置所有的轮廓属性。<br/>
>- 可以设置的属性分别是（按顺序）：outline-color(规定边框的颜色), outline-style(规定边框的样式), outline-width(规定边框的宽度)。<br/>
>- 如果不设置其中的某个值，也不会出问题，比如 outline:solid #ff0000; 也是允许的。
