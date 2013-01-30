---
Title: iOS Develeop Tips
Date:2013-01-24
Tags:iOS  
---


=== iOS Development Tips
最近看了一篇博客[《iOS Development Tips I Would Want If I Was Starting Out Today》](http://stuartkhall.com/posts/ios-development-tips-i-would-want-if-i-was-starting-out-today),其中很多观点和我相似，特偷懒将摘要放在我的博客。



1 Use ARC！

  ARC真是超级棒，开发者不用再去处理复杂的内存管理。需要注意的是ARC并不是内存的自动回收，只是把之前需要开发人员手工写的retain,release,autorelease，在编译阶段的由编译器自动添加。
做为有经验的iOS开发者，也请一定要用ARC，对于开发的速度是有很大提升。而iOS新手，用了ARC可以避免很多的内存问题。目前，越来越多的开源代码也采用了ARC。

2 尽可能使用Block
Block可以减少很多的代码，让你的代码更干净。
目前iOS原生API里面也大量的采用block。

3 避免循环Retain，尤其是在Block中
这个问题一定要注意。这里有篇文章专门讲这个问题，[A Quick Gotcha About Blocks](http://zearfoss.wordpress.com/2012/05/11/a-quick-gotcha-about-blocks/)。


4   忘记 Thread吧，多用GCD。
GCD用起来很容易，把耗时的操作放在异步的queue里面，记得把UI的操作放在main queue里！


5  Singletons/Shared Objects
	
	+ (MyClass *)sharedClass {
			static MyClass *_shared = nil;
			static dispatch_once_t onceToken;
			dispatch_once(&onceToken, ^{
	    	_shared = [[MyClass alloc] init];
			});   
			return _shared;
	}

6 Story Boards 只是为了做快速原型

7 只用XIBs处理基本的Layout

对于6，7我一直没有在项目中采用Interface Builder，主要是IB做出来的界面适应性不够强，代码也不容易读。
对于这两点我没有太多发言权，看个人喜好了。

8 组织好工程代码

9  拥抱开源代码
这点我是深深赞同，不要重复造轮子，把优秀的代码拿来直接用，可以大大提高开发效率。
我有两篇文章专门介绍了iOS的优秀开源项目。
[iOS实用开源代码推荐(一)](http://lipq.farbox.com/post/2012/2012-09-06-ios-opensource-recommend-1)

[iOS实用开源代码推荐(二)](http://lipq.farbox.com/post/2012/2012-09-06-ios-opensource-recommend-2)

10 Dependency Management

11   多用Stack Overflow
这个没的说，只要你用google搜索一些iOS的问题，最终大部分会指向Stack Overflow。

12	Graceful Degradation

优雅的向下支持？我不太赞成支持太老的系统版本。只要支持最新版本和向前一个版本就好了。如果是新开的项目直接只支持最新的系统版本吧！

13	自定字体
这个很简单，不过中文字体免费的不多，并且比较大。如果不是阅读APP，真不想增加字体。

14	从一开始就要支持多语言
嗯，国际化很重要。即使你不支持中文以外的语言，我也建议你一定要遵循iOS的Localization。这样你想支持其它语言的时候，很容易就可以添加了。

15	Crash报告
HockeyAPP和TestFlight可以提供比iTunesconnect更好的Crash report。

16 Anayze
可以解决很大一部分潜在的问题，解决掉它们。

17	Instruments
发布前一定要跑一下Instrument，把消耗CPU的地方优化一下。Instruments查找内存泄漏和僵尸指针也很有一套，这个需要经验。改天我会写一篇如何使用Instruments。

18 跟踪Appstore的用户Review
原作者写了个Appbot[http://appbot.co/]专门干这件事儿，网址是http://appbot.co/ 这里算是他的广告吧，哈哈。


