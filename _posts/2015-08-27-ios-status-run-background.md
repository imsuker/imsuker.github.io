---
  layout : post
  title : "ios切入后台后的变化"
  date : 2015-08-06 16:20:00
---
ios app切换到后台后，会有哪些变化，需要如何应对,简单的做了一下研究。写了个[demo][background in github]。

### 结论：  
1，`background`:即后台状态，此时APP还在运行，CPU占用，内存占用;如果APP被激活到前台，则继续运行。  
2，`suspend`:即挂起状态，此时APP所有线程暂停，CPU不占用，内存占用;如果APP被激活到前台，线程恢复到之前状态。  
3，`not running`:停止状态，CPU不占用，内存不占用;如果APP再次被激活前台，则会重启。  
4，如何进入`background`:下拉通知栏，按Home键。注：双击Home键并不会进入background，直到切换到其他APP。  
5，进入`background`后，如果不做任何操作，则会在极端时间内，切换成`suspend`。当通过`beginBackgroundTaskWithExpirationHandler`申请task后，可以得到得到N分钟的`background`,可以提前手动通过`endBackgroundTask`结束该状态。  
6，当系统内存吃紧时，系统会杀掉一些处于`background`和`suspend`的APP，其中内存占用量是很大的因素。  
7，终极结论:再进入`suspend`之前，需要尽可能的让自己APP占用更少的内存，从而不被系统杀掉，保持好的用户体验（切换回APP时能够保持之前状态而不是重启）

### 测试结果  
手头机器有限，测试了以下条目：  
1，iphone4 + ios6.1.3,结论:6.0系统进入后台后有10s自由时间，申请task后有600s

![iphone4](/assets/ios-status-run-background/iphone4.png)

2，iphone6+ios8.4.1,结论：8.0系统申请task后有180s

![ios8](/assets/ios-status-run-background/ios8.png)

3，iphone6+ios8.4.1,奇怪的现象，结论：8.0系统申请task并在180s结束后，依然可以跑任务。
![ios81](/assets/ios-status-run-background/ios8_2.png)

[background in github]:https://github.com/imsuker/DemoBackground
