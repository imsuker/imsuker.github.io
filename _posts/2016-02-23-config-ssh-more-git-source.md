---
  layout : post
  title : "一台机器操作多个github源"
  date : 2016-02-21 16:40:00
---
github不允许多个帐号绑定同一个客户端的rsa,所以想在一台机器上操作两个github帐号，需要做特殊配置：  
1,生成新的rsa
{% highlight bash %}
ssh-keygen -t ras -C "email"
#注意，回车后第一行不要回车，写上新的rsa名字，譬如:imsuker
{% endhighlight %}
2,添加到ssh`ssh-add imsuker`  
3,在`~/.ssh/`目录下新建config文件
{% highlight bash %}
 Host github.com
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa
Host imsuker.github.com
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/imsuker
{% endhighlight %}
4,在之后操作git或者gitconfig中修改对应的hosts`vi .git/config`
{% highlight bash %}
[remote "origin"]
  url = git@imsuker.github.com:imsuker/imsuker.github.io
  fetch = +refs/heads/*:refs/remotes/origin/*
{% endhighlight %}
