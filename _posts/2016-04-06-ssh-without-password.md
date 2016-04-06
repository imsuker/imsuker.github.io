---
layout : post
title : "通过id_rsa快捷ssh到服务器,无需密码"
keywords : "防火墙，nginx"
date : 2016-04-06 18:00:00
---
非常简单，将本机`~/.ssh/id_rsa.pub` 追加进服务器的`~/.ssh/authorized_keys`里即可。
