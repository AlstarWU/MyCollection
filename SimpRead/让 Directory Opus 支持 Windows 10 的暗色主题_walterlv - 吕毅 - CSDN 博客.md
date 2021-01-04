> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/wpwalter/article/details/94129130)

使用 Directory Opus 替代 Windows 自带的文件资源管理器来管理你计算机上的文件可以极大地提高你的文件处理效率。

由于我自己的 Windows 10 系统使用的是暗色主题，所以我希望 Directory Opus 也能搭配我系统的纯暗色主题。

本文介绍如何将 Directory Opus 打造成搭配 Windows 10 的暗色主题。

### 本文内容

*   *   [Directory Opus 主题支持](#Directory_Opus__10)
    *   [Windows 10 暗色风格的主题](#Windows_10__32)
    *   [微调主题样式](#_45)
    *   *   [微调文件组标题](#_61)
        *   [微调压缩的文件和文件夹](#_68)
    *   [微调其他部件](#_75)
    *   [还原成默认的主题](#_84)

Directory Opus 主题支持
-------------------

Directory Opus 在安装完之后的默认主题样式是下面这样的：

![](https://img-blog.csdnimg.cn/20190629100820165.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

然而，我的 Windows 10 的主要界面都是暗黑色的：

![](https://img-blog.csdnimg.cn/20190629100825381.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

那么，请在 Directory Opus 顶部菜单中选择 `设置` -> `主题`：

![](https://img-blog.csdnimg.cn/20190629100830327.png)

然后点击左下角的下载主题去网上下载一款主题。

![](https://img-blog.csdnimg.cn/20190629100834780.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

Windows 10 暗色风格的主题
------------------

你可以直接使用下面的链接下载 Windows 10 暗色风格的主题：

*   [Simple Windows 10 Dark Theme - Downloads / Themes - Directory Opus Resource Centre](https://resource.dopus.com/t/simple-windows-10-dark-theme/30055)

然后，依然进入我们一开始说的 `设置` -> `主题` 对话框中，导入刚刚我们下载好的主题：

![](https://img-blog.csdnimg.cn/20190629100839405.png)

点击 “应用”，随后 Directory Opus 会重新启动，你将看到全新的 Windows 10 暗色风格主题。

微调主题样式
------

等等！为什么重启之后看起来样式怪怪的？有一些文件的文字其实在暗色主题下看不太清。

![](https://blog.csdn.net/static/posts/2019-05-14-16-03-10.png)

这当然是主题设计者没有考虑到所有的情况导致的，实际上你下载的任何一款主题可能都有各种考虑不周的情况，那么如何修复这些考虑不周的细节呢？

我们需要前往 `设置` -> `选项` 中微调这些细节。在 “选项” 对话框中，选择 “颜色和字体” 标签。

![](https://img-blog.csdnimg.cn/20190629100844306.png)

![](https://img-blog.csdnimg.cn/20190629100848121.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

### 微调文件组标题

在我一开始的暗色主题应用后，我们注意到我的文件是分组的，组标题是深蓝色，看不清。于是修改 “文件组标题” 中的颜色：

![](https://img-blog.csdnimg.cn/20190629100853526.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

### 微调压缩的文件和文件夹

另外，我的多数文件是加入了 NTFS 压缩的，这部分文件被主题设置了很难看清的深紫色，我将它改为其他的颜色：

![](https://img-blog.csdnimg.cn/20190629100858641.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

微调其他部件
------

里面还有大量可以微调的部件，如果你遇到了不符合你要求的颜色设置，则将其修改即可。

以下是我进行了微调之后的主题效果预览：

![](https://img-blog.csdnimg.cn/20190629100904217.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

还原成默认的主题
--------

你可能会注意到在主题选择窗格中只有我们刚刚下载的那一个主题，我们不能选择回默认的主题样式。那如果一个主题被我们改残了，或者就是想重新体验原生效果的时候该如何做呢？

我们依然需要进入到 `设置` -> `选项` 中，然后选择 “颜色和字体” 标签。

这时，选择顶部的 `文件` -> `重置该页到默认值`。于是，我们的主题就会还原到最初没有修改任何字体和颜色的版本。

![](https://img-blog.csdnimg.cn/2019062910090983.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly93YWx0ZXJsdi5ibG9nLmNzZG4ubmV0,size_16,color_FFFFFF,t_70)

如果主题涉及到图标等其他资源，也需要进入对应的标签页然后还原对应标签页的设置。

**参考资料**

*   [Latest Themes topics - Directory Opus Resource Centre](https://resource.dopus.com/c/downloads/themes)
*   [Simple Windows 10 Dark Theme - Downloads / Themes - Directory Opus Resource Centre](https://resource.dopus.com/t/simple-windows-10-dark-theme/30055)
*   [Plain / Default Theme - Themes - Directory Opus Resource Centre](https://resource.dopus.com/t/plain-default-theme/1169)

我的博客会首发于 [https://blog.walterlv.com/](https://blog.walterlv.com/)，而 CSDN 会从其中精选发布，但是一旦发布了就很少更新。

如果在博客看到有任何不懂的内容，欢迎交流。我搭建了 [dotnet 职业技术学院](https://t.me/dotnet_campus) 欢迎大家加入。

![](https://img-blog.csdnimg.cn/20190406094629787.png)

本作品采用[知识共享署名 - 非商业性使用 - 相同方式共享 4.0 国际许可协议](http://creativecommons.org/licenses/by-nc-sa/4.0/)进行许可。欢迎转载、使用、重新发布，但务必保留文章署名吕毅（包含链接：[https://walterlv.blog.csdn.net/](https://walterlv.blog.csdn.net/)），不得用于商业目的，基于本文修改后的作品务必以相同的许可发布。如有任何疑问，请与我联系。