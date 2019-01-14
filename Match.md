---
typora-root-url: ./Images
---

# Match

*class* **Match** 匹配类

一个Match类的对象表示着find操作的成功返回结果。它包含了被用来搜索的图片的矩形范围。它还包含了它在已知的显示器被发现位置的左上角信息。

因为Match类是Region类的扩展，所有Region类的方法都可以被一个Match对象使用。



### 创建一个Match对象，获取其属性

一个Match对象会作为[find操作](https://sikulix-2014.readthedocs.io/en/latest/region.html#findinginsidearegionandwaitingforavisualevent)的显式结果被创建出来，并可以被存储在变量中用于后续的[click()](https://sikulix-2014.readthedocs.io/en/latest/region.html#Region.click)等操作。

它包括了被用来搜索的图片的矩形范围，它在已知的显示器被发现位置的左上角顶点，它被发现时相似度数据以及它被一种流程设计好的点击点。

```# 如果发现结果有返回，m是一个Match对象索引```

```m = find(``` ![apple](/../assets/apple.png)```)```

```print m #信息域内容：Match[10,0 30x22] score =1.00, target=center```

```# 如果发现结果有返回，m是一个Match对象索引```

```m = find(Pattern(``` ![apple](/../assets/apple.png)```).similar(0.5).targetOffset(100,0))```

```print m #信息域内容：Match[10, 0 30x22] score=1.00, target=(105,11)```

关于其他方面，Match对象适用一切Region类的特征和属性。



*class* **Match**

　　**getScore()**

　　　　获取图片或那啥被发现时的相似度，此值在0~1之间

　　**getTarget()**

　　　　获取被作为点击点得位置对象

　　　　显然，当没有位移通过Pattern.targetOffset()被作用于此时，点击点就

　　　　在匹配成功区域的中心。当有位移被作用于此时，点击点就位于中心点

　　　　进行相应位移后的位置。