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



关于其他方面，Match对象适用一切[Region](https://sikulix-2014.readthedocs.io/en/latest/region.html#Region)类的特征和属性。



*class* **Match**

　　**getScore()**

　　　　获取图片或那啥被发现时的相似度，此值在0~1之间

　　**getTarget()**

　　　　获取被作为点击点得位置对象

　　　　显然，当没有位移通过[Pattern.targetOffset()](https://sikulix-2014.readthedocs.io/en/latest/pattern.html#Pattern.targetOffset)被作用于此时，点击点就

　　　　在匹配成功区域的中心。当有位移被作用于此时，点击点就位于中心点

　　　　进行相应位移后的位置。



### findAll()后遍历全部匹配对象

Region.findAll()发现操作会返回一个用来遍历全部匹配的Match对象结果的对象。对此遍历对象的索引会被存储在单独的空间内，并且可以通过[Region.getLastMatches()](https://sikulix-2014.readthedocs.io/en/latest/region.html#Region.getLastMatches).

**重要提示**

- 每一个定义中，遍历器只能被使用一次，过后就会被清空。

你可以从[Finder]([`Finder`](https://sikulix-2014.readthedocs.io/en/latest/finder.html#Finder))类的描述中，了解更多关于遍历器基本操作的信息。如果你想将区域内的匹配结果存储待用，你可以将他们存储到列表中。



```findAll(```![star](/../assets/star.png) ```) #find all matches```

```mm = list(getLastMatches())```



示例：在默认屏幕上使用while:



``` findAll(```![star](/../assets/star.png) ```) #find all matches```

``` mm=SCREEN.getLastMatches()```

```while mm.hasNext(): #loop as long there is a first and more matches```

　　```print "found: ", mm.next() #access the next match in the row```

```print mm.hasNext() # is False, because mm is empty now```

```print mm.next() # is None, because mmis empty now```

```print SCREEN.getLastMatches().hasNext() # is False also ;-)```



示例：在默认屏幕上使用while:



```with findAll(```![star](/../assets/star.png) ```) as mm:```

``` while mm.hasNext(): # loop as long there is a first and more matches```

```print "found: ", mm.next() #access the nexxt match```

``` # mm will be None afterwards (destroyed automatically) ```