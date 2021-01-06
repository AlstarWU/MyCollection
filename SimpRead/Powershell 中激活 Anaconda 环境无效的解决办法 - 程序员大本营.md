> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.pianshen.com](https://www.pianshen.com/article/65022041132/)

**转载自：**  
作者：Dereen  
出处：[https://www.cnblogs.com/dereen/p/ps_conda_env.html](https://www.cnblogs.com/dereen/p/ps_conda_env.html)

最近在使用 Anaconda 的过程中，发现在 Win10 的 PowerShell 在使用 `conda activate` 环境名激活环境时无效，而 CMD 则可以。这里**前提必须将 Anaconda 写入环境变量**。否则在 PowerShell 输入`conda` 的任何命令都会无法识别。

首先在终端输入 `conda --version` 查看自己的 anaconda 版本。

![](https://www.pianshen.com/images/657/c20d3477d77b7854f5fe378c033b7b49.png)

Conda 版本低于 4.6
--------------

解决方法如下：

*   用 Win + X 组合键调出 PowerShell 管理员模式；
*   输入命令 `conda install -n root -c pscondaenvs pscondaenvs` 安装 PSCondaEnvs 包；
*   输入命令 `Set-ExecutionPolicy RemoteSigned` 在出现选项后输入 Y 回车，更改 PowerShell 的安全策略。
*   在 PowerShell 中激活和退出环境的命令分别为 `activate 环境名` 和 `deactivate 环境名`，**注意：需要去掉原命令中开头的 conda，否则也不会成功。**

这时问题应该解决了，结果如下：

![](https://www.pianshen.com/images/678/7ed862d1a5b13a5b45da744f4f58a23e.png)

Conda 版本大于等于 4.6
----------------

解决方法如下：

*   用 Win + X 组合键调出 PowerShell 管理员模式；
*   输入命令 `conda init powershell` ；
*   关闭当前 powershell 窗口，重新打开一个 powershell 窗口输入 `conda activate 环境名` 测试。

CMD 的话只需把上面三步中的 powershell 改为 cmd.exe 即可。

这时问题应该解决了，结果如下：

![](https://www.pianshen.com/images/15/42ddb5aac988de0a3b7472f18b9597ef.png)

_**如果不想每次一启动 Shell 就自动激活 Base 环境**_

在终端输入 `conda config --set auto_activate_base false` ，即可。

如果又反悔了，想显示了：

`conda config --set auto_activate_base true`

参考资料
----

https://stackoverflow.com/questions/47800794/how-to-activate-different-anaconda-environment-from-powershell?rq=1  
https://www.anaconda.com/conda-4-6-release/  
https://github.com/BCSharp/PSCondaEnvs  
https://blog.csdn.net/kdongyi/article/details/81905494