---
layout : post
title : "解决mac上cvs乱码问题,批量修改cvs编码"
date : 2015-08-06 14:43:00
---
从服务器上下来的导出来的cvs文件，用mac下的excel打开时会出现中文乱码的情况。主要是mac下的excel不支持utf8格式的中文，因此将其转换为GB18030,请参考[文章][dcharm]。

在此基础上，如果想批量修改一个文件夹下所有的文件，用到了以下办法：
{% highlight bash %}
$ mkdir ../result
# => 创建文件夹
$ in *;do iconv -f UTF8 -t GB18030 $i > ../result/$i;done
# =>循环转化每个文件到新文件夹
{% endhighlight %}
[dcharm]:http://www.dcharm.com/?p=8, 


