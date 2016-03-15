---
layout : post
title : "使用pull request时保持与fork源同步"
keywords : "pull request,fork"
date : 2016-03-15 18:40:00
---
1,[github.com官网教程](https://help.github.com/articles/syncing-a-fork/)
2,在本地绑定源服务器
{% highlight bash %}
#将源绑定到本地
git remote add upstream *****
#将源的更新同步到本地
git fetch upstream 
#将源的更新merge到master
git merge upstram/master
#更新到自己的github 
git push origin master
{% endhighlight %}





