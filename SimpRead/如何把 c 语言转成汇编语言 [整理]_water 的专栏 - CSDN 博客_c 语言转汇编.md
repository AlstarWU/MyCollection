> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/water_wenzhou/article/details/12777129)

1. 使用 gcc

        使用 gcc -S 1.c 可以把 1.c 转成特殊的 1.s，感觉其实是类似于汇编，然后可以修改其代码，要想继续编译可以用 gcc -s 1.s 然后就可以实现

2. 使用 VC++ 编译器 自带的 dumpbin 就可以 做反汇编。   
       如 vc++ 中在 C:\Program Files\Microsoft Visual Studio\VC98\BIN\DUMPBIN.exe   
       dumpbin /DISASM abc.exe   
       dumpbin /DISASM abc.exe /OUT:abc.asm

3. 在 vc 或者 vs 的时候按 alt+8 可以进行汇编调试，不仅可以查看程序的汇编代码，而且也可以查看此时的变量。

4. 通过修改项目 -> 属性 -> C/C++ -> 输出文件 -> 汇编输出之后，每次运行后都可以在 debug 下面找到一个 asm 文件