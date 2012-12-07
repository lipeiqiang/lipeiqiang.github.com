---
layout: post
title: 如何开始写一个iOS APP
categories:
- Programming
tags:
- iOS
- iOS
---

本文是根据个人经验所总结，主要是写给没有iOS开发经验但是准备投入到iOS开发行列的开发者，
希望能够减少前期的准备工作，把精力用在产品上面而不是不停地到处咨询一些琐碎的开发问题。本文的前提是具有Mac电脑和iOS设备，黑苹果也不在本文讨论范围。

####首先，申请一个IDP账号 
需要有一张VISA信用卡，然后到Apple开发者中心https://developer.apple.com/ 注册一个账号，然后选择99美元开发者计划即可。当然，你也可以在产品开发的差不多的时候再去申请，
但是如果需要在iOS Deviece上进行调试的话，是必须有iDP的。

####Objective-C和iOS入门
iOS Dev Center最近上线了一篇中文的开发文档,<马上着手开发 iOS 应用程序 (Start Developing iOS Apps Today)>,初学者一定要看看。https://developer.apple.com/library/ios/#referencelibrary/GettingStarted/RoadMapiOSCh/chapters/Introduction.html

####加快开发速度的框架
*  AFNetworking or MKNetwork
	推荐使用AFNetworking，这是一个非常简洁，功能又十分强大，作者还保持频繁更新的网络框架。使用AFNetworking
	可以大大减少网络部分的开发工作量。强烈推荐使用。

*MBProgressHud
    这又是一个iOS APP常用的控件，非常方便的等待框，样式很多，并且使用很方便。强烈推荐使用。
*  SDWebImage
	如果你的APP需要用到很多网络图片，SDWebImage必不可少。SDWebImage可以方便加载网络图片，并且自动处理缓	存，大大提高程序的流畅度。接口简单，使用方便，可以节约很多工作量。
 
####产品测试
Testflight进行测试和收集用户统计
使用Testflight可以方便的分发给测试用户，测试用户可以直接通过邮件的URL下载安装测试包，不再需要放到iTunes里面同步，并且可以收集用户反馈意见。借助脚本，Achive以后可以方便的上传到Testflight，可以大大提高测试的效率。
使用Testflight也可以方便知道测试用户有没有安装，使用了哪些接口，特别方便。

####发布以后的产品监测
* Flurry
   如果你是个人开发或者小团队，建议不要再搞自己的数据后台了，浪费时间又不一定比Flurry的功能多。如果你对国内服务放心的话也可以使用友盟。

####赚点广告钱
* ADMob和iAD
  广告平台很多，只是列出两个，如果你的产品用户比较多的话，可以考虑一下其它的平台。如果专注于国内，可能国内的广告平台更方便一些。
  
  以上可以大大提高开发的速度，如果你有更多服务或者技术分享，可以联系我，互相学习。
