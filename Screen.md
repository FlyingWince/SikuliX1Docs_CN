# Screen

这里的Screen类代表了一个用来执行捕获操作（从屏幕截取上抓取矩形）的实体屏幕。关于[多屏幕环境](https://sikulix-2014.readthedocs.io/en/latest/screen.html#multimonitorenvironments)，链接文档包含了映射到相关屏幕的特性。

因为Screen类是[Region](https://sikulix-2014.readthedocs.io/en/latest/region.html#Region)类的扩展，所有Region类的方法都可以被Screen类对象调用。

请注意，在整个屏幕上进行捕获操作可能会存在性能问题。所以在可能的前提下，将捕获操作限制在一个较小的区域内(如reg.find())有助于提高处理速度。



### Screen: 设置，获取属性值与信息

*class* **Screen**

​　　**Screen**([*id*])

　　　　新建一个Screen对象

　　　　**Parameters**: **id** - 多显示器模式下显示器的编号

　　　　**Returns**: 　　一个新的Screen对象

　　　　构造函数会创建一个新的Screen对象，当id被省略的时，这个对象即代表默认/基础的显示器(id亦为0)。数字1或更大的数字代表了脚本运行时可以获得的其他有效显示器。

　　　　使用一个不代表任何现存显示器的数字，会导致脚本报错退出。你可以通过获取屏幕编号信息的函数或异常处理来避免这种情况。

　　　　请注意：如果你想在不创建新Screen对象的情况下访问默认/基础屏幕（Screen(0)），可以使用常引用SCREEN。这是一个再脚本开始执行时就会被初始化的引用：SCREEN=Screen(0)。

　　getNumberScreens()

　　　　获取当前脚本运行运行时，多屏幕环境内的屏幕数

　　getBounds()

　　　　Get

　　　　返回值: 一个矩形对象

　　　　该矩形的宽和高



### 屏幕作为默认的域

所有域的方法



另一方面



### 捕获

捕获是一种功能，来抓取

还有一种交互

**IDE的注意点**：这两种功能





