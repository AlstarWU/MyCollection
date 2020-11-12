\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.csdn.net\](https://blog.csdn.net/fyuanfena/article/details/52080270)

1.  使用 conda  
    首先我们将要确认你已经安装好了 conda
    
2.  配置环境  
    下一步我们将通过创建几个环境来展示 conda 的环境管理功能。使你更加轻松的了解关于环境的一切。我们将学习如何确认你在哪个环境中，以及如何做复制一个环境作为备份。
    
3.  测试 python  
    然后我们将检查哪一个版本的 python 可以被安装，以及安装另一个版本的 python，还有在两个版本的 python 之间的切换。
    
4.  检查包  
    1) 我们将罗列出安装在我们电脑上的包
    
    2) 浏览可用的包
    
    3) 使用 conda install 命令来来安装以及移除一些包
    
    4) 对于一些不能使用 conda 安装的包，我们将在 Anaconda.org 网站上搜索
    
    5) 对于那些在其它位置的包，我们将使用 pip 命令来实现安装。我们还会安装一个可以免费试用 30 天的商业包 IOPro
    
5.  移除包、环境以及 conda
    

管理 conda：
=========

检查 conda 版本:
------------

```
conda --version
```

* * *

升级当前版本的 conda
-------------

```
conda update conda
```

* * *

管理环境
====

创建并激活一个环境
---------

使用”conda create” 命令，后边跟上你希望用来称呼它的任何名字：

```
conda create --name snowflake biopython
```

这条命令将会给 Biopython 创建一个新的环境，位置在 Anaconda 安装文件的 / envs/snowflakes

* * *

激活这个新环境
-------

*   Linux，OS X:

```
source activate snowflakes
```

*   Windows：

```
activate snowflake
```

### 小技巧：

新的开发环境会被默认安装在你 conda 目录下的 envs 文件目录下。你可以指定一个其他的路径；去通过  
`conda create -h`了解更多信息吧。

### 小技巧：

如果我们没有指定安装 python 的版本，conda 会安装我们最初安装 conda 时所装的那个版本的 python。

* * *

列出所有的环境
-------

```
conda info -envis或者(-e)
```

_\* 注意：conda 有时也会在目前活动的环境前边加上_号。\*\*

* * *

切换到另一个环境 (activate/deactivate)
------------------------------

为了切换到另一个环境，键入下列命令以及所需环境的名字。

*   Linux，OS X:

```
source activate snowflakes
```

*   Windows：

```
activate snowflakes
```

如果要从你当前工作环境的路径切换到系统根目录时，键入：  
\- Linux，OS X:

```
source deactivate
```

*   Windows:

```
deactivate
```

* * *

复制一个环境
------

通过克隆来复制一个环境。这儿将通过克隆 snowfllakes 来创建一个称为 flowers 的副本。

```
conda create -n flowers --clone snowflakes
```

通过

```
conda info –-envs
```

来检查环境

* * *

删除一个环境
------

如果你不想要这个名为 flowers 的环境，就按照如下方法移除该环境：

```
conda remove -n flowers
```

* * *

管理 Python
=========

安装一个不同版本的 python
----------------

现在我们假设你需要 python3 来编译程序，但是你不想覆盖掉你的 python2.7 来升级，你可以创建并激活一个名为 snakes 的环境，并通过下面的命令来安装最新版本的 python3：

```
conda create -n snakes python=3
```

* * *

检查新的环境中的 python 版本
------------------

确保 snakes 环境中运行的是 python3：

```
python --version
```

* * *

使用不同版本的 python
--------------

为了使用不同版本的 python，你可以切换环境，通过简单的激活它就可以，让我们看看如何返回默认版本

*   Linux，OS X:

```
source activate - snowflakes
```

*   Windows：

```
activate snowflakes
```

* * *

注销该环境
-----

当你完成了在 snowflakes 环境中的工作室，注销掉该环境并转换你的路径到先前的状态：

*   Linux，OS X：

```
source deactivate
```

*   Windows：

```
deactivate
```

* * *

管理包
===

*   conda 安装和管理 python 包非常方便，可以在指定的 python 环境中安装包，且自动安装所需要的依赖包，避免了很多拓展包冲突兼容问题。
*   不建议使用 easy\_install 安装包。大部分包都可以使用 conda 安装，无法使用 conda 和 anaconda.org 安装的包可以通过 pip 命令安装
*   使用合适的源可以提升安装的速度

* * *

查看已安装包
------

使用这条命令来查看哪个版本的 python 或其他程序安装在了该环境中，或者确保某些包已经被安装了或被删除了。在你的终端窗口中输入：

```
conda list
```

* * *

向指定环境中安装包
---------

### 使用 Conda 命令安装包

我们将在指定环境中安装这个 Beautiful Soup 包，有两种方式:  
\- 直接指定 - n 指定安装环境的名字

```
conda install --name bunnies beautifulsoup4
```

_\* 提示：你必须告诉 conda 你要安装环境的名字（-n bunies）否则它将会被安装到当前环境中。\*_

*   激活 bunnies 环境，再使用 conda install 命令。

```
activate bunnies
conda install beautifulsoup4
```

### 2\. 从 Anaconda.org 安装一个包

如果一个包不能使用 conda 安装，我们接下来将在 Anaconda.org 网站查找。

在浏览器中，去 [Anaconda 资源官网](http://anaconda.org) 。我们查找一个叫 “bottleneck” 的包，所以在左上角的叫 “Search Anaconda Cloud” 搜索框中输入 “bottleneck” 并点击 search 按钮。

Anaconda.org 上会有超过一打的 bottleneck 包的版本可用，但是我们想要那个被下载最频繁的版本。所以你可以通过下载量来排序，通过点击 Download 栏。  
点击包的名字来选择最常被下载的包。它会链接到 Anaconda.org 详情页显示下载的具体命令：

```
conda install--channel https：//conda .anaconda.ort/pandas bottleneck
```

### 3\. 通过 pip 命令来安装包

对于那些无法通过 conda 安装或者从 Anaconda.org 获得的包，我们通常可以用 pip 命令来安装包。

可以上 pypi 网  
站查询要安装的包，查好以后输入 pip install 命令就可以安装这个包了。

我们激活想要放置程序的 python 环境，然后通过 pip 安装一个叫 “See” 的程序。

*   Linux，OS X：

```
source activate bunnies
```

*   Windows：

```
activate bunnies
```

所有平台：

```
pip install see
```

### 提示：pip 只是一个包管理器，所以它不能为你管理环境。pip 甚至不能升级 python，因为它不像 conda 一样把 python 当做包来处理。但是它可以安装一些 conda 安装不了的包。

### 4\. 文件安装

如果真的遇到走投无路的境地，也就是上面这些方法通通不管用！！！那就只能下载源码安装了，比如 exe 文件（双击安装）或者 whl 文件（pip 安装）等等。还有在 github 上找到源码，使用`python setup.py install`命令安装

Tips: 不建议使用 setuptools 的 easy\_install，非常不方便管理，也不好卸载  
有些时候，Anaconda 和 pip 下载的速度慢，访问不稳定怎么办？换个源呗，[清华大学的源](https://mirrors.tuna.tsinghua.edu.cn/)就很不错，当然啦，你可以自己 google 一些好用的源

对于包管理工具，了解这么多就够了，比较喜欢追根究底的童鞋可以移步[包管理工具解惑](http://zengrong.net/post/2169.htm)  
\*\* 提示：  
在任何时候你可以通过在命令后边跟上 - help 来获得该命令的完整文档。  
\*\*

eg:

```
conda update --help
```

_\* 小技巧：\*_  
很多跟在–后边常用的命令选项，可以被略写为一个短线加命令首字母。所以–name 选项和 - n 的作用是一样的。通过`conda -h`或`conda –-help`来看大量的缩写。

移除包、环境、或者 conda
===============

如果你愿意的话。让我们通过移除一个或多个试验包、环境以及 conda 来结束这次测试指导。

移除包
---

假设你决定不再使用商业包 IOPro。你可以在 bunnies 环境中移除它。

```
conda remove -n bunnies iopro
```

移除环境
----

我们不再需要 snakes 环境了，所以输入以下命令：

```
conda remove -n snakes --all
```

删除 conda
--------

*   Linux，OS X：

移除 Anaconda 或 Miniconda 安装文件夹

```
rm -rf ~/miniconda
```

OR

```
rm -rf ~/anaconda
```

*   Windows：

去控制面板，点击 “添加或删除程序”，选择“Python2.7（Anaconda）” 或“Python2.7（Miniconda）”并点击删除程序。

Reference:
==========

[30 分钟 Anaconda 快速入门英文版](http://conda.pydata.org/docs/test-drive.html)

[Anaconda 清华大学镜像源](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)