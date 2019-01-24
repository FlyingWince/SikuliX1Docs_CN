# Screen

这里的Screen类代表了一个用来执行搜索操作（从屏幕截取上抓取矩形）的实体屏幕。关于[多屏幕环境](https://sikulix-2014.readthedocs.io/en/latest/screen.html#multimonitorenvironments)，链接文档包含了映射到相关屏幕的特性。

因为Screen类是[Region](https://sikulix-2014.readthedocs.io/en/latest/region.html#Region)类的扩展，所有Region类的方法都可以被Screen类对象调用。

请注意，在整个屏幕上进行搜索操作可能会存在性能问题。所以在可能的前提下，将搜索操作限制在一个较小的区域内(如reg.find())有助于提高处理速度。



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

　　　　获得Screen对象所指代的显示器分辨率

　　　　返回值: 一个矩形对象

　　　　该矩形的宽和高既了Screen对象所指屏幕的分辨率。这些属性是通过操作系统获取的，它们无法被SIkuli脚本修改。



### 屏幕作为默认的域

所有域的方法都应像reg.find(PS)这样调用，其中reg是一个Region对象(或Screen/Match对象)。当其被写作时find(PS)时，其作用于默认的屏幕上(此时默认指向常引用SCREEN)。在多屏幕环境下，其指向基准显示器(通过常引用SCREEN)，既通常情况下的Screen(0)。但根据平台与设置的不同，有时其也可指另一个Screen对象。

另一方面，因为搜索域为整个屏幕，使用默认屏幕作为操作域可能会降低操作处理速度。为了提升性能，建议使用region.find()来限制搜索域为特定的矩形。另一种方法是，通过setROI()来限制接下来所有的搜索操作到一个相对全屏较小的区域。当域显著的小于整屏时，处理性能会得到提示。



### 捕获

捕获(Screen.capture())功能，用来从截图中按照像素抓取矩形并可将其存入到临时文件中去，待搜索操作备用。每一个捕获完成时会生成一份新截图。

还有一种交互方式为Screen.selectRegion(), 直接返回用户交互所选择的矩形的坐标和分辨率。

**IDE的注意点**：这两种功能都可以通过IDE上的工具条按钮进行调用。捕获按钮可以让用户通过直接在屏幕上选取一个矩形进行交互。该矩形内容会被存储到当前脚本的包路径下，并被插入到脚本当前的编辑位置(以缩略图或自动生成的文件名形式)。

根据参数设置不同有两种情况：

- 第一种永远将截图储存到临时文件中
- 第二种允许指定存储截图的文件名与文件路径

*class* Screen

　　**capture** ([*region / rectangle / text*])

　　**capture**(x ,y ,w ,h)

　　　　**Parameters**:  

　　　　　　**region** - 一个现存的Region对象

　　　　　　**rectangle** - 一个现存的矩形对象（作为另一个Region方法的返回值）

　　　　　　**text** - 交互模式屏幕中央显示的文本

　　　　　　**x** - 捕获矩形的x坐标

　　　　　　**y** - 捕获矩形的y坐标

　　　　　　**w** - 捕获矩形的宽度

　　　　　　**h** - 捕获矩形的高度

　　　　**Results**:

　　　　　　捕获图片的存储路径（文件总是存储在临时空间）

　　　　　　在交互模式下，用户可以取消捕获，返回值为None.

　　　　**Interactive Mode**: 

　　　　　　点击IDE上的相关按钮时会进入屏幕捕获模式，用户此时可以捕获屏幕上的矩形范围。

　　　　　　除了文本以外的任何可用参数被指定的时候，程序会自动捕获指定的屏幕矩形。可用时，一个新的截屏会被生成，选中的矩形范围内容会被存储到临时文件中。文件名会被返回，并可作为对该图片的引用后续使用。在允许参数PS的脚本中，它可以被直接使用（如Region.find(), Region.click(), ...）。

　　**selectRegion**([*text*])

　　　　交互式地从屏幕上选取一个域(译注：鼠标选取)

　　　　**Parametrs: text** - 屏幕中现实的文本

　　　　**Returns:**  一个新域对象或者None（若用户取消捕获进程）

　　　　**text** 会在屏幕中央显示2秒。如果**text**参数被省略，则启用默认文本“Select a region on the screen”

　　　　进入交互式捕获模式，用户可以使用IDE的选择工具以相同方式选取一个域。

　　　　**Note**: 考虑到用户可能取消捕获，你应当检查结果。

**Save the captured image elsewhere(not temporary)**

*class*  **Screen**

　　　　**capture**(*region / text, [path, ]name*)

　　仅Python有效（必须按照不打点的方式调用）///？这里

　　**Parameters**: 

　　　　**region** - 一个现存的域对象

　　　　**text** - 交互模式下展示的文本

　　　　**path** - 图片存储的路径（默认为包路径）

　　　　**name** - 图片文件名（默认格式为 .png）

　　**Returns**: 捕获图片的存储绝对路径，格式为path/name.png。若失败则返回None

　　基本上和普通的捕获功能没区别，但会直接将获得的图片存储到指定位置。```name```字段勿需以```.png```结尾

　　　　如果路径未指定，图片文件会被存储到当前包路径。此情况下图片文件名回显为```bundlepath/_name.png```，下划线是IDE





　　　　　　　　　　　　

