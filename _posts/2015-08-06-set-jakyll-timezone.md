--- 
  layout : post
  title : "jekyll设置timezone,显示正确的时间"
  date : 2015-08-06 16:20:00
---
[官方文档][jekyll config]里没有写怎么设置timezone,因此如果用`{post.date | date: "%Y-%m-%d %H:%M:%S"}`输出相应时间时，结果会不正确。

解决办法：在config.yml文件中添加时区配置：
{% highlight bash %}
timezone : +0800
{% endhighlight %}


[jekyll config]:http://jekyll.bootcss.com/docs/variables/
