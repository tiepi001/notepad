# ��������������

> ��JS�ﶨ��ı�����������������������ں���ִ��ʱ���Ȱѱ������������������������ǰ���������������������ֵ�Ķ��廹��ԭ��λ�á�ʾ�����£�

```
var test = function() {

    console.log(name); // �����undefined

    var name = "jeri";

    console.log(name); // �����jeri

}
test();
```

**������������������ȼۡ�**

```
var test = function() {

    var name;

    console.log(name); // �����undefined

    name = "jeri";

    console.log(name); // �����jeri

}
test();
```

**�����ϴ����֪���ں���ִ��ʱ���ѱ����������������˺�������������ֵ������Ȼ��ԭ��λ�á�**

