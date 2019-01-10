# Sikuli/Sikulix 文档 1.1及更新版本(2014以后)
这份文档由[Raimund Hocke aka RaiMan](https://launchpad.net/~raimund-hocke)维护。

如果你对这份文档有任何问题或想法，欢迎通过上方的链接及文后的邮件地址与他直接联系。

**快速入门信息及其他联系方式详见**：<https://sikulix.com>。

关于Sikuli本身的特性和功能，本文并不会充分的解读，请移步[Sikuli Questions and Answers Board](https://answers.launchpad.net/sikuli)

提示及更多帮助信息链接，请见侧边栏。

**关于先前版本的文档**

文档可能已失效或无法正常使用，恕不另行通知。欢迎提出Bug.

这里依旧提供到SikuliX-1.0rc3版本为止的文档。

### 如何使用这份文档
SikuliX通过**SikuliX IDE**尽可能地支持各种脚本运行（SikuliX IDE是一个可以读写、存储及运行脚本的基础编辑器，它还负责创建与管理你的可视化工作流中的各种图片。）

**支持的脚本语言**

**Python** (level 2.7): 由Jython解释器支持.

**Ruby** (level 1.9/2.0): 由JRuby解释器支持.

**JavaScript** 由Java内置引擎支持 (Java 7: Rhino, Java 8: Nashorn).

如果你是个新人程序员，你仍可以通过SikuliX IDE享受轻松自动运行重复任务的快感，而不需要学习其中任何一门脚本。

​		学习教程会是一个比较好的入手方式。

如果你想要写一些包含模块或类的复杂脚本，那就需要深入了解下Python, Ruby或是Javascript。

**注**: 因为Jython和JRuby是基于Java的，所以Python和Ruby可用的模块未必能被Sikulix的环境支持。因此在尝试任何非标准模块或插件时，你需要先检查他们是否被SikuliX环境所支持。

**关于使用Java的说明**: SikuliX的特性是通过Java底层进行支持的。所以你也可以在你的Java项目或其他Java支持环境中已API的形式调用SikuliX ([如何应用](https://sikulix-2014.readthedocs.io/en/latest/faq/030-java-dev.html)). 尽管这份文档的目标是服务那些脚本用户，但是它也包含了有关于Java API层面的基本信息，以及两者API层面最主要的不同之处。

​		此外你可以阅读下Java的文档(最新版)。

这份文档中的每个章节依据一个类或一组方法的基本特征进行了简单的描述。
 每章都提供了其中方法的一般使用信息及提示。我们建议您在使用相关特性前仔细的阅读该对应章节。 

如果你此前从未接触过Sikuli系列工具，循序渐进的将这份文档读一遍应当是个不错的方法。当然你也可以选择检视[内容表](https://sikulix-2014.readthedocs.io/en/latest/toc.html)，直接跳到你感兴趣的章节。一个折中的办法是按下列顺序阅读那些关键章节：[域Region](https://sikulix-2014.readthedocs.io/en/latest/region.html#Region), [匹配Match](https://sikulix-2014.readthedocs.io/en/latest/match.html#Match)和 [屏幕Screen](https://sikulix-2014.readthedocs.io/en/latest/screen.html#Screen)。

之后，你可以根据按字母排序的[内容表](https://sikulix-2014.readthedocs.io/en/latest/toc.html)或[索引](https://sikulix-2014.readthedocs.io/en/latest/genindex.html)去浏览所有的类、方法及函数。
