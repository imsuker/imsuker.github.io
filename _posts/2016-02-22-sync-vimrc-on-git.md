---
  layout : post
  title : "在git上同步自己的vimrc及vundle使用"
  date : 2016-02-21 16:40:00
---
保存自己平常用的vimrc,在换机器时能够快速导入并进入自己熟悉的vim环境。  
1，将vimrc 软链 到一个文件夹:
{% highlight bash %}
ln -s ~/.vimrc ~/.myvim/.vimrc
{% endhighlight %}
2，在`~/.myvim/`初始化git或clone自己vimrc的git目录。  
3，修改更新即可。  
vundle使用办法：   
1，克隆vundle源代码到本地
{% highlight bash %}
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
{% endhighlight %}
2,按`https://github.com/scrooloose/nerdtree`里第3步，将配置文件copy到`~/.vimrc`里。  
3,打开vim,运行`:PluginInstall`即可安装自己配置的插件。  
4,在vimrc文件底部可以添加自己定义的一些配置。
