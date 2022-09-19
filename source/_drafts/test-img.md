---
title: test img
date: 2022-09-18 22:26:17
updated: 2022-09-18 22:26:17
tags:
---

```md
![图片描述](/img/full.png)
```

markdown语言插入本地图片：

![图片描述](../img/test.jpg)

markdown语言插入网络图片：

![图片描述](https://img10.360buyimg.com/ddimg/jfs/t1/166587/8/21344/72069/6088c24fEda5fdeb6/f9730ab637b7ca47.png)



html语言插入网络图片：

<img src="https://img10.360buyimg.com/ddimg/jfs/t1/166587/8/21344/72069/6088c24fEda5fdeb6/f9730ab637b7ca47.png" alt="text">

html语言插入本地图片：

<img src="../img/test.jpg" alt="text">

%%方式：

```bash
这是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif %} 一段话。

这又是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif, height=40px %} 一段话。

这又是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif, height=100px %} 一段话。
```

这是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif %} 一段话。

这又是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif, height=40px %} 一段话。

这又是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif, height=100px %} 一段话。

```bash
{% image https://pic1.zhimg.com/80/v2-5fe6be356ddda4afe6063b0682edfead_1440w.jpg?source=1940ef5c, alt=自定义图片 %}
```

{% image https://pic1.zhimg.com/80/v2-5fe6be356ddda4afe6063b0682edfead_1440w.jpg?source=1940ef5c, alt=自定义图片 %}

```bash
{% image https://pic3.zhimg.com/80/v2-08d7fdf0201e560c22a2e9d9c2c040f6_1440w.jpg?source=1940ef5c, width=400px, alt=指定宽度 %}
```

{% image https://pic3.zhimg.com/80/v2-08d7fdf0201e560c22a2e9d9c2c040f6_1440w.jpg?source=1940ef5c, width=400px, alt=指定宽度 %}

```bash
{% image  https://pic3.zhimg.com/80/v2-c18a3b0f2e82533d6c47e72e085aca0b_1440w.jpg?source=1940ef5c, width=400px, bg=#1D0C04, alt=设置占位背景色 %}
```

{% image  https://pic3.zhimg.com/80/v2-c18a3b0f2e82533d6c47e72e085aca0b_1440w.jpg?source=1940ef5c, width=400px, bg=#1D0C04, alt=设置占位背景色 %}
