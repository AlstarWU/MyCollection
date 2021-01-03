> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/hhxy_wlzx/article/details/103518566)

有关 Windows10 中允许 UWP 应用走代理的操作方法
-------------------------------

**我们都知道，Win10 之后，Windows 系统中除了基于传统的 exe 可执行程序的软件之外，又多了 “UWP 应用” 这一新颖的玩意儿。**  
有关 UWP 应用的详细介绍，可以查阅度娘百科的相关词条：[Universal Windows Platform](https://baike.baidu.com/item/Universal%20Windows%20Platform/23796796?fromtitle=uwp&fromid=4236943&fr=aladdin)  
**可以看到，磁贴风格还是挺好看哒（至少笔者是这样认为的）**  
![](https://img-blog.csdnimg.cn/20191212230556860.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**自然，UWP 应用使用的也都是这样的界面风格，而现如今的 Microsoftstore 已经不和当初 Win8 时那样鸡肋了，其中已经有了较多实用的应用，所以有相当一部分人除了普通的放在桌面上的软件，更偏向于使用已经在开始菜单固定了的 UWP 应用**  
![](https://img-blog.csdnimg.cn/20191212231329616.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**但当我们使用这些 UWP 应用时，可能有时会遇到这种情况：**  
（（打开 UWP 版 bilibili 之后）诶，这个番剧是锁区的？还好我有其他地区的代理，挂上之后再看！）  
（啧啧啧，UWP 版本的推特界面还挺好看，我不会再想用浏览器登录了！）  
**诸如此类**  
**但当我们自信的打开代理软件**~（比如说小飞机 ）~ **之后，却发现不该连上的网站还是连不上，看不了的番剧还是看不了…**  
“为什么呢？”  
“是我的代理软件有问题吗？？”  
~我们遇到什么困难，也不要怕，微笑着面对它~ **其实，并不是我们的代理出现了问题，而是在 Windows10 系统中，默认是不允许这些 UWP 应用走代理网络的。**

那么该怎么解决呢？
---------

先说一说麻烦一点的办法吧！
-------------

**1. 通过注册表获取应用的 SID**  
首先通过 Win + R 快捷键打开「运行」窗口，输入「Regedit」打开注册表编辑器，然后定位到 **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppContainer\Mappings** ，接着在左边的注册表项中找到你想解除网络隔离的应用（这里以 UWP 版的推特为例），右边的 DisplayName 就是应用名称，而左边那一大串字符就是应用的 SID 值了。  
![](https://img-blog.csdnimg.cn/20191212233727844.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**复制应用的 SID**  
![](https://img-blog.csdnimg.cn/20191212234224576.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)

**2. 打开 CMD 面板**  
输入 **CheckNetIsolation.exe loopbackexempt -a -p=SID**（SID 就是上一步复制的 SID），出现「完成」后就大功告成了。  
![](https://img-blog.csdnimg.cn/2019121223432085.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**这时再打开 UWP 应用，你应该就能愉快的做自己想做的事情了。**  
“我就是个小白，看不懂怎么办？”  
~“这要再看不懂那你别用电脑了”~

别急别急，这还有个稍微简单一点的方法！
-------------------

**1. 首先下载安装网络调试工具** [Fiddler](https://www.telerik.com/fiddler)  
![](https://img-blog.csdnimg.cn/2019121223525693.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20191212235538604.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**这时会要求填写用途、电子邮件，看着填就行了**  
**2. 下载安装完成后，打开它**  
![](https://img-blog.csdnimg.cn/20191212235830582.png)  
**3. 点击 “WinConfig”**  
![](https://img-blog.csdnimg.cn/20191213000348443.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**遇到这种情况直接点否就好了**  
![](https://img-blog.csdnimg.cn/20191213000538689.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
**4. 在新弹出来的窗口中勾选你要允许的应用，点击 “Save Changes” 即可**  
![](https://img-blog.csdnimg.cn/20191213000903802.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hoeHlfd2x6eA==,size_16,color_FFFFFF,t_70)  
_**亦可直接点击 “Exempt All” 来允许所有的应用**_  
**这时再打开 UWP 应用，你应该就能愉快的做自己想做的事情了。**  
**是不是比刚刚手动找 SID 简单的多呢？qwq**  
**到这里，Windows10 中允许 UWP 应用走代理的操作教程已经结束辣！**  
**如果有错误之处或更好的方法还请各位指点喔 qwq！**  
![](https://img-blog.csdnimg.cn/20191213001616299.JPG)  
**码字不易，点个赞留个言再走嘛 qwq**

**2019.12.13  
袁 #一**