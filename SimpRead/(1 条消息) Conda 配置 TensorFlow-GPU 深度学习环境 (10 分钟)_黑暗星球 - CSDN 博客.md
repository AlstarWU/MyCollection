> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/u014061630/article/details/88543422)

TensorFlow 作为一个比较流行的框架，每年都有很多的新用户。而作为一个 TensorFlow 学习者，首当其冲的便是配置 TensorFlow 深度学习环境。TensorFlow 深度学习环境一般分为 CPU 版和 GPU 版本，其中，CPU 版本比较好配置，GPU 版本比较难配置。目前，随着 Conda（Anaconda 和 Miniconda） 的大量使用，TensorFlow 深度学习环境的配置已经变的非常简单（尤其是 GPU 版的）。

网上关于使用 Conda 配置 TensorFlow-GPU 深度学习环境的教程一抓一大把，但其仍然不够简单，安装过程有着诸多冗余步骤。

基于 Conda 配置 TensorFlow-GPU 深度学习环境
=================================

Conda 是一种包管理工具。要安装 Conda 一般需要安装 Anaconda 或者 Miniconda 包。这里不具体介绍两者之间的差别，我一般选择 Miniconda（因为占的空间少），版本直接选择最新就好了（在创建的隔离环境里配置 TensorFlow，所以默认环境的 Python 版本无关紧要）。

下面开始正式的配置工作：

第一步：安装显卡驱动
----------

从 Nvidia 官网下载合适的显卡驱动，并安装。

第二步：安装 Miniconda
----------------

**2019 年 5 月 2 日更新：** 国内源都已停止对 Anaconda 源的支持，所以请直接从官网下载安装包。

从[清华开源镜像站](https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/?C=M&O=A)或者[官网](https://repo.anaconda.com/miniconda/)下载 Miniconda 的安装包，然后安装。

这里推荐[清华开源镜像站](https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/?C=M&O=A)，因为可以很方便的查找各个版本（我一般使用这个方法：通过 Date 进行排序，然后按时间找最新的，特别方便）。

第三步：更换 Conda 源
--------------

**2019 年 5 月 2 日更新：** 国内源都已停止对 Anaconda 源的支持，所以不用换源了。

打开终端（命令行），输入以下内容，将 conda 清华源添加进来。

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

第四步：创建隔离环境
----------

打开终端（命令行），输入以下内容，创建一个名为 tf_latest 的隔离环境。

```
conda create -n tf_latest python=3.6
```

第五步：安装 TensorFlow-GPU
---------------------

打开终端（命令行），激活上一步创建的隔离环境：

```
activate tf_latest 或者 conda activate tf_latest
```

接着，输入以下内容，就将 TensorFlow-GPU 安装好了。

```
conda install tensorflow-gpu
```

安装 opencv （可选操作）：

```
conda install opencv
```

安装一些机器学习常用的包（可选操作）：

```
conda install numpy, scipy, matplotlib, pandas,scikit-learn,scikit-image
```

到此，TensorFlow-GPU 深度学习环境就算配置好了。

**说明：**

1.  因为 TensorFlow 安装在隔离环境中，所以使用时，需要激活隔离环境，才能使用上面安装的 TensorFlow。
    
2.  这里，我们没有手动安装 CUDA 和 cuDNN，这是因为 Conda 在安装 TensorFlow 时会自动在隔离环境中安装合适版本的 CUDA 及 cuDNN。
    
3.  总安装时间 10 分钟，仅供参考。因为需要网络，所以时间仅供参考。当然，如果网速足够快，那么 10 分钟是能够安装完的。