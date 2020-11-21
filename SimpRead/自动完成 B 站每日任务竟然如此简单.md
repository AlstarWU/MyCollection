\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[mp.weixin.qq.com\](https://mp.weixin.qq.com/s/KuOxlHZL2VnonvxA-QDbOw)

【公众号回复 “**1024**”，免费领取程序员赚钱实操经验】

![](https://mmbiz.qpic.cn/mmbiz_jpg/zRiam9B2qkhTE3icDJBqabB84w2sEjuQfxnlofACvibI0fqbT7nbROjAibZE60QGw6Y4V3dYvh79JUamO8r9vA90Bw/640?wx_fmt=jpeg)

大家好，我是章鱼猫。  

今天推荐的这个项目是「**BilibiliTask**」，是一个 Bilibili 助手，可以自动完成哔哩哔哩 (B 站) 每日任务，投币，点赞，直播签到，自动兑换银瓜子为硬币，自动送出即将过期礼物，漫画 App 签到。

**本项目已经完成的功能：**

*   自动获取经验 (投币、点赞、分享视频)
    
*   直播辅助 (直播签到，自动送出即将过期的礼物)
    
*   自动兑换银瓜子为硬币
    
*   漫画辅助脚本 (漫画 APP 签到)
    

**本项目将要完成的功能：**

*   自动领取大会员每月权益 (B 币劵，优惠券)
    

**使用方法：**

1、fork 本项目

2、需要的参数

本项目想成功运行需要三个参数，分别是 SESSDATA，bili\_jct，DedeUserID

3、如何获取需要的参数

b 站首页（任意一个页面都行）--> 按下 F12 --> Application --> Cookies --> https://www.bilibili.com

然后找到需要所需要的参数对应的数据，找不到可能是你的账号没有登录。

![](https://mmbiz.qpic.cn/mmbiz_png/zRiam9B2qkhScMp67Sd5YKVKg7iacStwc9xJiav6xIzcuFxK1nYaa2icafOdOVJaHFcRCMIAc8Sw6k2SlCdmvxgH7Q/640?wx_fmt=png)

4、Secrets 的格式

需要把上面的 SESSDATA，bili\_jct，DedeUserID 隐私数据添加到 Secrets 中。

![](https://mmbiz.qpic.cn/mmbiz_png/zRiam9B2qkhScMp67Sd5YKVKg7iacStwc9588muOy0KSTQHib3xcnzRL6RWib6ibHtUbJAW53fnReic2n2DyDaZicjTsg/640?wx_fmt=png)

5、开启 actions

默认 actions 处于禁止状态，在 Actions 中开启 Actions，把那个绿色的长按钮点一下。

![](https://mmbiz.qpic.cn/mmbiz_png/zRiam9B2qkhScMp67Sd5YKVKg7iacStwc9a8libdm7SJCLF2vzQvHeMLQRW0pMeic3eXXEmdZsXdQSr5YQ9UxX9Licw/640?wx_fmt=png)

6、运行一次工作流

当填写完上面数据之后，再创建 wiki，就可以运行一次工作流。

Wiki --> Create the first --> Save Page

然后查看 actions，显示对勾就说明运行成功了。以后会在每天的 10：30 进行运行，自动完成每日任务。

点击阅读原文，查看更多内容。

开源项目地址：https://github.com/srcrs/BilibiliTask

开源项目作者：srcrs

**推荐阅读：**

[标星高达 6.5 K 的一份《Vim 从入门到精通》的中文教程](https://mp.weixin.qq.com/s?__biz=MzA3MzE4ODY0Mg==&mid=2455986693&idx=1&sn=a35e8117ee06f80e08bbeb5acd0b14c4&scene=21#wechat_redirect)

[这个项目竟然可以自动生成原创文章](https://mp.weixin.qq.com/s?__biz=MzA3MzE4ODY0Mg==&mid=2455986676&idx=1&sn=bd71c65db44dae184ae02db52f015053&scene=21#wechat_redirect)

[推荐一个开源 GitHub 技术资料阅读的微信小程序](https://mp.weixin.qq.com/s?__biz=MzA3MzE4ODY0Mg==&mid=2455986667&idx=1&sn=0ec35620c2191d5a42f4f8d165f92660&scene=21#wechat_redirect)

\--- 特别推荐 ---

特别推荐：一个新的优质的推荐高效工具，软件，插件的公众号，每天给大家分享优秀的效率工具，**「程序员掘金」**，专门为程序员挖掘好东西的一个公众号，非常值得大家关注。

![](https://mmbiz.qpic.cn/mmbiz_png/GVyeDObNlrHoUyQ78KPahoHiaBIq0QibfNibFU5852DaccBpGUbFwic7JUwvXSEBImhnF1DOOR75BbheOehWjJXX0A/640?wx_fmt=png)