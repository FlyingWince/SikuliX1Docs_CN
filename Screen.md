# Screen

这里的Screen类代表了一个用来执行捕获操作（从屏幕截取上抓取矩形）的实体屏幕。关于[多屏幕环境](https://sikulix-2014.readthedocs.io/en/latest/screen.html#multimonitorenvironments)，链接文档包含了映射到相关屏幕的特性。

因为Screen类是Region类的扩展，所有Region类的方法都可以被Screen类对象调用。

请注意，在整个屏幕上进行捕获操作可能会存在性能问题。所以在可能的前提下，将捕获操作限制在一个较小的区域内有助于提高处理速度。