> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_36759224/article/details/98058240)

![](https://img-blog.csdnimg.cn/20190919235440689.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)

> **本文原创首发于我的个人博客：www.itrhx.com，欢迎访问！**  
> **本文在我个人博客上的链接：https://www.itrhx.com/2019/08/01/A27-image-hosting/**

– 前言
====

图床是个啥东西就不用过多介绍了，先来对比一下各路图床：

> *   微博图床：以前用的人比较多，从 2019 年 4 月开始开启了防盗链，凉凉
> *   SM.MS：运营四年多了，也变得越来越慢了，到了晚上直接打不开图片，速度堪忧
> *   其他小众图床：随时有挂掉的风险
> *   Imgur 等国外图床：国内访问速度太慢，随时有被墙的风险
> *   大厂储存服务：例如七牛云、又拍云、腾讯云 COS、阿里云 OSS 等，容量限制，操作繁琐，又是实名认证又是域名备案的，麻烦，而且还要花钱（有钱又不怕麻烦的当我没说）

因此，GitHub 图床是个不错的选择，利用 jsDelivr CDN 加速访问（jsDelivr 是一个免费开源的 CDN 解决方案），PicGo 工具一键上传，操作简单高效，GitHub 和 jsDelivr 都是大厂，不用担心跑路问题，不用担心速度和容量问题，而且完全免费，可以说是目前免费图床的最佳解决方案！

– 新建 GitHub 仓库
==============

登录 / 注册 GitHub，新建一个仓库，填写好仓库名，仓库描述，根据需求选择是否为仓库初始化一个 README.md 描述文件  
![](https://img-blog.csdnimg.cn/20190920000150159.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20190920000139844.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)

– 生成一个 Token
============

在主页依次选择【Settings】-【Developer settings】-【Personal access tokens】-【Generate new token】，填写好描述，勾选【repo】，然后点击【Generate token】生成一个 Token，注意这个 Token 只会显示一次，自己先保存下来，或者等后面配置好 PicGo 后再关闭此网页  
![](https://img-blog.csdnimg.cn/20190920000128625.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20190920000117661.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20190920000103409.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20190920000048156.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20190920000036465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)

– 配置 PicGo
==========

前往[下载 PicGo](https://github.com/Molunerfinn/picgo/releases)，安装好后开始配置图床  
![](https://img-blog.csdnimg.cn/20190920000020217.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM2NzU5MjI0,size_16,color_FFFFFF,t_70)

*   **设定仓库名：**按照【用户名 / 图床仓库名】的格式填写
    
*   **设定分支名：**【master】
    
*   **设定 Token：**粘贴之前生成的【Token】
    
*   **指定存储路径：**填写想要储存的路径，如【ITRHX-PIC/】，这样就会在仓库下创建一个名为 ITRHX-PIC 的文件夹，图片将会储存在此文件夹中
    
*   **设定自定义域名：**它的作用是，在图片上传后，PicGo 会按照【`自定义域名+储存路径+上传的图片名`】的方式生成访问链接，放到粘贴板上，因为我们要使用 jsDelivr 加速访问，所以可以设置为【`https://cdn.jsdelivr.net/gh/用户名/图床仓库名` 】，上传完毕后，我们就可以通过【`https://cdn.jsdelivr.net/gh/用户名/图床仓库名/图片路径`】加速访问我们的图片了，比如：https://cdn.jsdelivr.net/gh/TRHX/ImageHosting/ITRHX-PIC/A27/08.png
    

关于 jsDelivr 是如何引用资源的可以参考我的另一篇博客：[《免费 CDN：jsDeliver+Github》](https://www.itrhx.com/2019/02/10/A18-free-cdn/)

– 进行高效创作
========

配置好 PicGo 后，我们就可以进行高效创作了，将图片拖拽到上传区，将会自动上传并复制访问链接，将链接粘贴到博文中就行了，访问速度杠杠的，此外 PicGo 还有相册功能，可以对已上传的图片进行删除，修改链接等快捷操作，PicGo 还可以生成不同格式的链接、支持批量上传、快捷键上传、自定义链接格式、上传前重命名等，更多功能自己去探索吧！