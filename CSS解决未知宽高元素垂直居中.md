## cssδ֪���Ԫ��ˮƽ��ֱ����

### ����һ 
> **˼·**����ʾ���ø�Ԫ��Ϊ��table����Ԫ��Ϊ��cell-table�������Ϳ���ʹ��vertical-align: center��ʵ��ˮƽ����<br>
**�ŵ�**����Ԫ�أ�parent�����Զ�̬�ĸı�߶ȣ�tableԪ�ص����ԣ�<br>
**ȱ��**��IE8���²�֧��

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

### ��������

> **˼·**��ʹ��һ���ձ�ǩspan��������vertical-align��׼��Ϊ�м䣬��������Ϊinline-block�����Ϊ0 <br>
**ȱ��**������һ��û�õĿձ�ǩ��display:inline-blockIE 6 7�ǲ�֧�ֵ�(����ϣ�_zoom1;*display:inline)��<br>
��ȻҲ����ʹ��αԪ��������span��ǩ������IE֧��Ҳ���ã������Ǻ���

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

### ������

> **˼·**����Ԫ�ؾ��Զ�λ�����붥�� 50%�����50%��Ȼ��ʹ��css3 transform:translate(-50%; -50%) <br>
**�ŵ�**���ߴ���,������webkit�ں˵��������ʹ�� <br>
**ȱ��**����֧��IE9���²�֧��transform����

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

### ������

> **˼·**��ʹ��css3 flex���� <br>
**�ŵ�**���� ��� <br>
**ȱ��**�����ݲ��ðɣ��������http://caniuse.com/#search=flex

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