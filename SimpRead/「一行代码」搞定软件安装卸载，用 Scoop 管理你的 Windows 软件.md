> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [sspai.com](https://sspai.com/post/52496)

「包管理系统」，常看少数派文章的同学一定对这个名词不陌生。Homebrew 就是 macOS 上体验最佳的软件包管理，能帮助我们方便快捷、干净利落的管理软件。

**推荐阅读：**[《像 Mac 高手一样管理应用，从 Homebrew 开始》](https://sspai.com/post/42924)

有很长一段时间，[当我从 macOS 切换到 Windows 之后](https://sspai.com/post/45742)，都因为 Windows 缺乏一个好用的包管理器而委屈巴巴。不过，经过我两个月以来的体验，**我觉得 Scoop 可能是 Windows 上体验最好的「包管理器」。**

![](https://cdn.sspai.com/2019/01/11/325ad054d00bf6963aeea9d7d7c604ed.png)Scoop - The Windows Package Manager

Scoop 哪里值得推荐
------------

作为一个包管理器，最基础，也是最重要的功能就是**安装软件**。正在使用 Windows 的你一定在想：「为什么我要用它？为什么我不直接百度一下？」。

是，你当然可以按照老套路：

1.  百度一下软件名称；
2.  从几十条搜索结果中筛选出那个看起来安全无毒的下载链接；
3.  下载下来一个你不知道有什么捆绑的 exe 可执行文件；
4.  安装到需要管理员权限的目录；
5.  结束。

好麻烦！

Scoop 等一系列包管理器的诞生，第一大便利就是省去了上述繁琐的「搜索 - 下载 - 安装」的步骤，让我们能够通过「一行代码」急速安装。💪

同时，用 Scoop 来安装和管理我们的软件：

*   集搜索、下载、安装、更新软件于一体：极大的降低了安装维护一个软件的成本，我们甚至不必在软件本身的复杂菜单中寻找那个更新按钮来更新软件自己
*   将软件干干净净的安装到电脑的「用户文件夹」下：这样既不会污染路径也不会请求不必要的权限（UAC）
*   在卸载软件的时候，能够尽量清空软件在电脑上存储的任何数据和痕迹

特别的，Scoop 最适合安装那种干净、小巧、开源的软件。并且，Scoop 也极度适合为开发者配置开发环境，不过这些很多都涉及到进阶使用技巧。下面我们先从基础的安装方法开始介绍如何「像 Windows 高手一样管理应用，从 Scoop 开始」。

Scoop 的安装配置
-----------

安装 Scoop 很简单，不过你需要先确定一些基础环境是否符合安装要求：

*   Windows 版本不低于 Windows 7
*   Windows 中的 PowerShell 版本不低于 PowerShell 3
*   你能 **正常、快速** 的访问 GitHub 并下载上面的资源
*   你的 Windows 用户名为英文（Windows 用户环境变量中路径值不支持中文字符）

之后，右键开始菜单按钮，在右键菜单中打开 PowerShell：

![](https://cdn.sspai.com/2019/01/11/d6bc7bc6b51fe797899b5e64d36681ed.png)打开 PowerShell

在 PowerShell 中输入下面内容，保证允许本地脚本的执行：

`set-executionpolicy remotesigned -scope currentuser`

然后执行下面的命令安装 Scoop：

`iex (new-object net.webclient).downloadstring('https://get.scoop.sh')`

静待脚本执行完成就可以了，安装成功后，让我们尝试一下：

`scoop help`

![](https://cdn.sspai.com/2019/01/11/366081198b4916ad066f1d569a9a0a51.png)Scoop 使用说明书

这样就表明我们 Scoop 已经成功安装了。`scoop help` 这个命令就是 Scoop 的使用说明书，如果我们记不住某个命令怎么执行，也可以通过 `scoop help` 来唤起这个命令参考说明。  

下面我们继续介绍具体应该如何高效的使用 Scoop 管理、安装、更新软件。

Scoop 使用方法
----------

### Scoop 基础语法

从上面的命令中，我们可以发现 Scoop 命令的设计很简单（和 Homebrew 等 Unix-style 的工具一样），是「`scoop` + 动作 + 对象」的语法。其中「对象」是可省略的。

![](https://cdn.sspai.com/2019/01/11/69f2db0e372074441ceb4f2fcf96d31d.png)

最常用的几个基础动作有这些：

<table><thead><tr><th>命令</th><th>动作</th></tr></thead><tbody><tr><td>🌟search</td><td>搜索软件名</td></tr><tr><td>🌟install</td><td>安装软件</td></tr><tr><td>update</td><td>更新软件</td></tr><tr><td>🌟status</td><td>查看软件状态</td></tr><tr><td>uninstall</td><td>卸载软件</td></tr><tr><td>info</td><td>查看软件详情</td></tr><tr><td>home</td><td>打开软件主页</td></tr></tbody></table>

🌰 举几个栗子，比如：

*   我们想要搜索一下有没有 Firefox 浏览器：`scoop search firefox`

![](https://cdn.sspai.com/2019/01/11/8dcf81f085033a9608d5ffb4090b762e.png)

*   我们想要安装 aria2 下载器（我下载过 aria2，所以截图和你的显示可能不太一样）：`scoop install aria2` 

![](https://cdn.sspai.com/2019/01/11/721febd364efc01d06d334e9188648a0.png)

*   我们想要看看 Typora 的主页：`scoop home typora` 

![](https://cdn.sspai.com/2019/01/11/354456ba818d4ecfeb598f340fd3a987.gif)

就这样，十分简单！

那么现在安装软件的流程就变成了：`scoop search 软件名` - `scoop install 搜索结果中符合条件的那个`，结束。方便简洁！当然 Scoop 肯定不止这些命令可以折腾，更多的进阶命令和使用方法可以参考 [Scoop Wiki](https://github.com/lukesampson/scoop/wiki)，如果有机会我也会更新更多的 Scoop 使用技巧。

### Scoop 把软件安装在哪儿？

这就是 Scoop 设计最为精致的地方所在了，也是我推荐 Scoop 超过 Chocolatey 等更知名的 Windows 软件包管理器的原因。

Scoop 和 Homebrew 对软件包安装位置有着相同的处理哲学：「下载、安装在用户文件夹下」。具体来讲：

*   Scoop 在你的用户根目录（一般是 C:\Users \ 用户名）下创建了一个名为 scoop 的文件夹，并默认将软件下载安装到这个文件夹下
*   Scoop 将软件安装到一个相对隔离的环境下（Each program you install is isolated and independent），从而保证环境的统一和路径不被污染

![](https://cdn.sspai.com/2019/01/11/56b71f7f565ba363116394e16808f29e.png)

可以看到，`scoop` 文件夹下的 `apps` 存放有安装的所有应用。值得一提的是：`scoop` 是通过 `shim` 来软链接一些应用，这样的设计让应用之间不会互相干扰，十分方便。

软件包管理哲学
-------

最后我还是想说一说：为什么我们推荐使用「包管理」？

在写这篇文章之前我也看了我派上面对包管理工具介绍的文章，我觉得这些文章其实都没太讲清为什么我们需要用「包管理」这个看上去复杂难用的命令行工具去下载、管理我们的软件。毕竟现在的软件管理哲学是「我去 App Store 下一个不就行了嘛？」

需要明确的是：包管理的设计初衷是为了方便开发者管理和搭建开发环境。用包管理工具能够快速的安装开发工具、开发依赖，从而免去复杂的路径、环境变量等信息的配置。而我们作为普通用户，实际上用「包管理」工具的过程，就是在借鉴这种「软件管理哲学」。

但更重要的，也是更对我们用户安装基本软件的过程来说的，是我前文提到的：

*   一行代码省去了搜索、筛选、下载等繁琐步骤
*   安装方便、更新方便、卸载也方便
*   同时也最大程度杜绝了流氓捆绑软件的安装（因为 Scoop 本身和 Scoop 安装过程参考的配置文件都是开源的，要安装什么一目了然）

这些都是传统的「搜索 - 筛选 - 下载」的软件管理过程带来的复杂过程和安全隐患的极佳解决方法。

尝试一下 Scoop 吧！如果你对这个简洁、克制却依旧强大的工具产生兴趣，你一定离高阶 Windows 用户不远了。限于篇幅，我就先介绍到这里，更多有关 Scoop 的进阶用法、Scoop 的软件 bucket 哲学等等，都请期待一下。