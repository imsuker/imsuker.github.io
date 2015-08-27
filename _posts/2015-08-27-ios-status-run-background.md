--- 
  layout : post
  title : "ios切入后台后的变化"
  date : 2015-08-06 16:20:00
---
ios app切换到后台后，会有哪些变化，需要如何应对,简单的做了一下研究。写了个[demo][background in github]。

结论：
1，`background状态`:即后台状态，此时APP还在运行，CPU占用，内存占用;如果APP被激活到前台，则继续运行。  
2，`suspend状态`:即挂起状态，此时APP所有线程暂停，CPU不占用，内存占用;如果APP被激活到前台，线程恢复到之前状态。  
3，`not running状态`:停止状态，CPU不占用，内存不占用;如果APP再次被激活前台，则会重启。  
4，如何进入`background状态`:下拉通知栏，按Home键。注：双击Home键并不会进入background状态，直到切换到其他APP。  
5，进入`background状态`后，如果不做任何操作，则会在极端时间内，切换成`suspend状态`。当通过`beginBackgroundTaskWithExpirationHandler`申请task后，可以得到得到N分钟的`background状态`,可以提前手动通过`endBackgroundTask`结束该状态。  
6，当系统内存吃紧时，系统会杀掉一些处于`background状态`和`suspend状态`的APP，其中内存占用量是很大的因素。  
7，终极结论:再进入`suspend状态`之前，需要尽可能的让自己APP占用更少的内存，从而不被系统杀掉，保持好的用户体验（切换回APP时能够保持之前状态而不是重启）  
手头机器有限，测试了一下iphone4(ios6.1.3),结果如下。

![iphone4](/assets/ios-status-run-background/iphone4.png)
iphone6+ios8.4.1  

![ios8](/assets/ios-status-run-background/ios8.png)

![ios81](/assets/ios-status-run-background/ios8_2.png)

[background in github]:https://github.com/imsuker/DemoBackground
