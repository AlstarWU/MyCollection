> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/jeremyjone/article/details/106236656)

原文地址： [https://www.jeremyjone.com/671/](https://www.jeremyjone.com/671/)，转载请注明。

Windows 给我们提供的 PS 本身是这样子的：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1MDI0ODkxMS5wbmc?x-oss-process=image/format,png)

虽然它提供了一些基本的美化功能，但是并不能满足我们的审美。

我们希望在命令行中间有些改进，比如：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1MDQ5MjMyNi5wbmc?x-oss-process=image/format,png)

接下来一步一步实现它。

1、安装 oh-my-posh
---------------

使用`win + x`方式调出**管理员模式**的 PowerShell，然后安装两个模块：

```
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```

安装过程中根据提示选择 Y 或者 A 都可以：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1MTExNDIzNi5wbmc?x-oss-process=image/format,png)

2、导入
----

安装成功后，就可以导入了。

```
Import-Module posh-git
Import-Module oh-my-posh
```

这时候可能会看到这样子的很不友好的提示：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1MTIxMDUzMC5wbmc?x-oss-process=image/format,png)

此时需要修改策略，执行命令：`set-ExecutionPolicy RemoteSigned`后，再运行上面的命令即可:

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1MTM2NDgwMi5wbmc?x-oss-process=image/format,png)

*   注：请忽略我这里的警告，因为我的虚拟机没有安装 git，所以 posh-git 找不到相应的路径。

然后就可以设置对应的主题了。

```
Set-Prompt
Set-Theme PowerLine
```

Set-Theme 后面跟主题的名字，可以选择的`Agnoster`，`Paradox`，`Sorin`，`Darkblood`，`Avit`，`Honukai`，`Fish`，`Robbyrussell`等等，可以通过 Tab 来回切换查看。

成功后，就是这个样子的：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1MTkxMDUzNi5wbmc?x-oss-process=image/format,png)

没错，有一些乱码，不要慌，因为 PS 默认的新宋体本身就会有这些问题，再来一些字体的配置就可以了。

3、配置自动启动主题
----------

在配置字体之前，需要配置自动启动，因为上面设置过的内容，关闭 PS 之后，下次在启动，又回到了起点，很是麻烦，所以需要自动配置。

直接在 PS 中执行：

```
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
notepad $PROFILE
```

然后按下回车，会打开一个记事本，在里面粘贴下面的内容，然后保存即可。

```
Import-Module posh-git
Import-Module oh-my-posh
Set-Theme PowerLine
```

再次重启 PS，会看到已经自动启动配置主题了：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NjAzMTc4NS5wbmc?x-oss-process=image/format,png)

4、配置字体
------

我看好多美化文章中都是用到了一种叫 " [更纱黑体](https://github.com/be5invis/Sarasa-Gothic/releases) " 的等宽字体，直接下载`*.ttf`即可。

下载好的压缩包，先解压（**此处注意：解压后的字体大小会有 10G 多一些，所以需要留出足够硬盘空间**），然后安装需要的字体：[*-Regular]。（如果你愿意，也可以全选，然后右键选择安装全部字体）

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NTUxNjE1Mi5wbmc?x-oss-process=image/format,png)

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NTQ4MzgwOS5wbmc?x-oss-process=image/format,png)

在 PS 的属性中，将字体改为添加的字体即可。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NzE2Mjk4NC5wbmc?x-oss-process=image/format,png)

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NzIwMDU4Mi5wbmc?x-oss-process=image/format,png)

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NzIxOTgyNC5wbmc?x-oss-process=image/format,png)

5、配置 Windows Terminal
---------------------

其实到这里，PS 已经配置好了，那么 Windows Terminal 也就配置好了，只是 WT 还需要单独配置字体。

打开配置文件：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NzM2MjE0NS5wbmc?x-oss-process=image/format,png)

在配置文件`profiles.json`中，在 PowderShell 的配置字段中，添加：

```
"fontFace": "Sarasa Term SC"
```

表示使用的字体，就可以了。

6、配置 VSCode
-----------

因为 VSCode 也经常使用 PS，其他配置不变，也是单独修改字体配置即可。

在配置文件中查找`terminal font`：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NzU0OTUxOS5wbmc?x-oss-process=image/format,png)

如果没有配置过，这里应该为空，直接键入如图的内容：

```
monospace,'Sarasa Term SC'
```

因为 VSCode 的配置基本都是热更新，所以改完就可以看到变化：

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamVyZW15am9uZS5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMjAvMDUvaW1hZ2UtMTU4OTk1NzgwNjcyNC5wbmc?x-oss-process=image/format,png)

完成~