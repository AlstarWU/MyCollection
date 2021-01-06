> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [sspai.com](https://sspai.com/post/52907)

在上一篇文章中，我们介绍了如何将 PowerShell 的终端变得漂亮起来。在这一篇文章中，我将为大家介绍如何定制 PowerShell 中的 Prompt 单元，并推荐 5 个赏心悦目的 Prompt（命令提示符）主题。

推荐阅读：[告别 Windows 终端的难看难用，从改造 PowerShell 的外观开始](https://sspai.com/post/52868)

开始之前，我先介绍一下 PowerShell 的基本构成。PowerShell 等 Shell 的一个基本的命令单元大致如下：

*   前面的部分就是 Prompt，能够展示包括用户、系统、开发环境、版本控制等等有用的信息
*   后面的部分是具体的命令，也就是我们每次执行操作时输入命令的位置

![](https://cdn.sspai.com/2019/02/25/e9e7eea3d8b7e6958afc6dd0b909475d.jpg) Shell 命令结构

PowerShell 相对不人性化的地方在于其默认 Prompt 只有 `PS C:\User\..\folder>` 这样的一部分。**所以，我推荐 `oh-my-posh` 这个 PowerShell 的主题框架。**`oh-my-posh` 是一个开源、低调的 PowerShell 主题框架，其 GitHub 项目地址位于：[JanDeDobbeleer/oh-my-posh](https://github.com/JanDeDobbeleer/oh-my-posh)。我们可以利用 `oh-my-posh` 为我们定制一个有用且好看的 Prompt。

准备工作
----

首先需要注意的是，`oh-my-posh` 主题使用了一些非 Powerline 字体不支持的字符，因此如果你使用默认的等宽字体（比如 `Consolas`），在显示过程中就会出现乱码、字符显示不全的现象。

![](https://cdn.sspai.com/2019/02/25/524b2e0d4da3cf970d4316fd5c75a85b.png) 字符显示不全的问题

Powerline 字体在 GitHub 开源，我们可以在这里： [powerline/fonts](https://github.com/powerline/fonts) 下载支持相关字符的字体。（如果你使用的是更纱黑体，那么就不必担心。）同时，请务必确认你所使用的终端支持你所想应用的自定义 Powerline 字体。有关默认 PowerShell 终端的字体配置和第三方终端的推荐，请参考 [上一篇文章](https://sspai.com/post/52868)。

下载安装
----

我们通过在 PowerShell 中执行下面的命令安装配置 `oh-my-posh`。

### 安装 posh-git 和 oh-my-posh 这两个模块

```
Install-Module posh-git -Scope CurrentUser 
Install-Module oh-my-posh -Scope CurrentUser
```

### 让 PowerShell 主题配置生效

#### 新增（或修改）你的 PowerShell 配置文件

```
# 如果之前没有配置文件，就新建一个 PowerShell 配置文件
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
用记事本打开配置文件
notepad $PROFILE
```

#### 在其中添加下面的内容

```
Import-Module posh-git 
Import-Module oh-my-posh 
Set-Theme Paradox
```

其中最后一句 `Set-Theme <主题名>` 就是配置主题的命令。如果一切顺利，你应该看到你的 Prompt 部分变成了类似这个的样子：

![](https://cdn.sspai.com/2019/02/25/210d41263f19bfac8d3f9b7ea984ae78.png)

**值得注意**：如果你发现后面的日期显示出现了凌乱的现象（比如本该在同一行显示的字符却跑到了下一行），多半是因为显示了中文。目前很多终端都不能正常的显示中文或 CJK 字符（即：Double-width character），所以你可以通过下面这个命令将 PowerShell 的环境设置为 en-US 的英文环境：

```
Set-Culture en-US
```

![](https://cdn.sspai.com/2019/02/25/3863b371ee030b75b0cc3e3735eb41e1.png)

一般来说，PowerShell 的用户配置文件在 `C:\Users\<用户名>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`，这个也就是刚刚安装过程中生成的文件，接下来定制的过程，就修改这个文件来配置即可。

主题推荐
----

使用某个主题很简单，下面这个命令就可以让我们预览某个主题：

```
Set-Theme <主题名>
```

比如我想要预览 Sorin 这个主题：

```
Set-Theme Sorin
```

![](https://cdn.sspai.com/2019/02/25/16b9e44d1cc533862ed9424a527f5ef7.gif)

**注**：这个命令支持 Tab 自动补全主题名称。

配置文件的最后一句 `Set-Theme Paradox` 的作用就是配置主题。**我们可以在配置文件里面修改这个命令中的 `Paradox` 即「主题名」来更换主题**。`oh-my-posh` 内置有 10 个主题，下面我来推荐几个我比较喜欢的主题：

### Agnoster

`oh-my-posh` 的主题有很多都借鉴了 Linux 世界里相对更加成熟的主题框架 `oh-my-zsh` 的主题。Agnoster 这个主题算是最经典的一个了，长长的箭头配合上鲜明的色彩让这个主题成为经典中的经典。不仅如此，Agnoster 还能够更加方便的显示你的登录用户名、设备名、当前文件夹中 `git` 版本控制的信息等等一系列有用的功能。

![](https://cdn.sspai.com/2019/02/25/7cd790a21f7592173a2b4a8e1fd3acdc.png)

### Sorin

Sorin 这个主题也是我相对比较喜欢的一个了。和上面 Agnoster 相比，Sorin 这个主题简洁、精致，仅由字符和图标构成，没有华丽的箭头，但是信息显示的一点不少。值得推荐。👍

![](https://cdn.sspai.com/2019/02/25/dcdd1d60ec3bd51a97a5e231d01c2f79.png)

### Avit

Avit 是一个极为简单的主题，其主 Prompt 是由两行构成的，第一行显示路径、`git` 版本控制信息和日期等等，第二行显示每次输入的命令。这样的设计有一个好处在于：我们可以避免前面部分显示不支持的字符导致光标位置出现错位的问题。很值得尝试。

![](https://cdn.sspai.com/2019/02/25/5a4b52d10ec2c7b8c9eefcdd644f544a.png)

### robbyrussell

熟悉 `oh-my-zsh` 的同学一定了解，robbyrussell 这个主题是 `oh-my-zsh` 的默认主题！如果说哪个主题能让 PowerShell 用起来像 zsh 那么一定是这个 robbyrussell 主题了。

![](https://cdn.sspai.com/2019/02/25/b001a6604778f06afda0e637dd78d860.png)

### 定制自己的主题

`oh-my-posh` 是相对比较完善的 PowerShell 主题配置引擎，因此我们也可以魔改某个主题，来让它达到我们想要的效果，甚至自己写一个主题配置也可以。在 `oh-my-posh` 的主题文件夹 `C:\Users\<用户名>\Documents\WindowsPowerShell\Modules\oh-my-posh\<版本号>\Themes` 下新建一个 `myTheme.psm1`，之后按照其他主题的写法进行修改就可以了。使用 `Set-Theme myTheme` 这个命令来让你的自定义主题生效。

限于篇幅我这里不具体介绍如何写一个自定义的主题，感兴趣的同学还请自行进行查看 [`oh-my-posh` 的相关文档](https://github.com/JanDeDobbeleer/oh-my-posh)。我自己也有一个自定义主题在：[spencerwooo/dotfiles](https://github.com/spencerwooo/dotfiles)，有兴趣的同学可以去参考一下。

![](https://cdn.sspai.com/2019/02/25/8dbd66254a163a78d491e414c98317fc.png)

**还有一个值得注意的地方是**：我的自定义主题中涉及到一些 Powerline 字体不支持的字符，需要在这里 [ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts) 下载 Nerd Fonts 来正常使用。想要更多字符支持（比如题图中的那个 Windows 徽标 icon 的显示）可以考虑使用 Nerd Fonts。使用 [Scoop 包管理](https://sspai.com/post/52496) 的同学，也可以利用它来安装 Nerd Fonts，具体步骤就不赘述了。

尾巴
--

自从 2016 年微软将 PowerShell 和 PowerShell Core 开源，Windows 上的终端体验也有了长足的发展。经过这篇文章的介绍，我相信你在 Windows 上使用 PowerShell 终端的体验会有所进步。

当然，为了让使用 Windows 的同学们同样能在原生 Windows 的环境下体验甚至直接使用 Linux 的终端环境，在 Windows 10 中 Windows 也正式引入了 Windows Subsystem for Linux，即适用于 Windows 的 Linux 子系统。如果你觉得 PowerShell 依旧糟糕，想使用 Linux 的 `bash` 或 `zsh` 等作为默认的 Shell 进行开发工作，那么使用 Windows 10 的你现在就可以去微软商店下载你希望使用的 Linux 发行版。

有关 PowerShell 等终端的配置指南到这里就结束了，感谢阅读。

> 下载少数派 [客户端](https://sspai.com/page/client)、关注 [少数派公众号](http://sspai.com/s/KEPQ) ，了解更多有趣的应用 🚀

> 特惠、好用的硬件产品，尽在 [少数派 sspai 官方店铺](https://shop549593764.taobao.com/?spm=a230r.7195193.1997079397.2.2ddc7e0bPqKQHc) 🛒