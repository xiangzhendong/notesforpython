# 生成SSH密匙

原则上，如果你在github上有一个repository，可以在gitbook的[设置](https://www.gitbook.com/book/xiangzhendong/notesforpython/settings/github)中设置gitbook和github repository的关联，这样，你就可以Link your book to a GitHub repository to edit this repository directly from the editor.

此外，你也可以在gitbook的history中查看push的情况

但是，二者的双推并不稳定，这就需要我们使用终端来手动push

[帮助文档](https://help.github.com/articles/generating-ssh-keys/)

ssh keys是一种不需要密码就可以识别可信任电脑的方式。


### 第1步：检查SSH keys

检查电脑上已经存在的SSH keys。在终端输入：```$ ls -al ~/.ssh```


### 第2步：生成一个新的SSH keys

终端输入：```ssh-keygen -t rsa -b 4096 -C "your_email@example.com"```

生成一个新的ssh keys，用你的邮箱作为标签。接下来会询问你本地保存key、输入口令、然后显示ssh key的fingerprint


### 第3步：将key添加到ssh－agent中

配置ssh－agent以使用你的ssh key

激活ssh－agent：```$ eval "$(ssh-agent -s)"```

将ssh key添加到ssh－agent中：```$ ssh-add ~/.ssh/id_rsa id_rsa是private key file```


### 第4步：将ssh key添加到账户中

配置github账户以使用你的key

拷贝id_rsa.pub文件到剪贴板：```$ pbcopy < ~/.ssh/id_rsa.pub```

在github设置中的ssh key中点击add ssh key，粘贴刚刚拷贝的内容，完成key的添加


### 第5步：测试连接

终端输入：```$ ssh -T git@github.com```
