## css未知宽高元素水平垂直居中

### 方法一 
> **思路**：显示设置父元素为：table，子元素为：cell-table，这样就可以使用vertical-align: center，实现水平居中<br>
**优点**：父元素（parent）可以动态的改变高度（table元素的特性）<br>
**缺点**：IE8以下不支持

```
.parent1{
    display: table;
    height:300px;
    width: 300px;
    background-color: #FD0C70;
}
.parent1 .child{
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    color: #fff;
    font-size: 16px;
}


    <div class="parent1">
        <div class="child">hello world-1</div>
    </div>

```

### 方法二：

> **思路**：使用一个空标签span设置他的vertical-align基准线为中间，并且让他为inline-block，宽度为0 <br>
**缺点**：多了一个没用的空标签，display:inline-blockIE 6 7是不支持的(添加上：_zoom1;*display:inline)。<br>
当然也可以使用伪元素来代替span标签，不过IE支持也不好，但这是后话了

```
.parent2{
    height:300px;
    width: 300px;
    text-align: center;
    background: #FD0C70;
}
.parent2 span{
    display: inline-block;;
    width: 0;
    height: 100%;
    vertical-align: middle;
    zoom: 1;/*BFC*/
    *display: inline;
}
.parent2 .child{
    display: inline-block;
    color: #fff;
    zoom: 1;/*BFC*/
    *display: inline;
}

    <div class="parent1">
        <div class="child">hello world-1</div>
    </div>

    <div class="parent2">
        <span></span>
        <div class="child">hello world-2</div>
    </div>
```

### 方法三

> **思路**：子元素绝对定位，距离顶部 50%，左边50%，然后使用css3 transform:translate(-50%; -50%) <br>
**优点**：高大上,可以在webkit内核的浏览器中使用 <br>
**缺点**：不支持IE9以下不支持transform属性

```
.parent3{
    position: relative;
    height:300px;
    width: 300px;
    background: #FD0C70;
}
.parent3 .child{
    position: absolute;
    top: 50%;
    left: 50%;
    color: #fff;
    transform: translate(-50%, -50%);
}

    <div class="parent3">
        <div class="child">hello world-3</div>
    </div>
```

### 方法四

> **思路**：使用css3 flex布局 <br>
**优点**：简单 快捷 <br>
**缺点**：兼容不好吧，详情见：http://caniuse.com/#search=flex

```
.parent4{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 300px;
    height:300px;
    background: #FD0C70;
}
.parent4 .child{
    color:#fff;
}

    <div class="parent4">
        <div class="child">hello world-4</div>
    </div>
```