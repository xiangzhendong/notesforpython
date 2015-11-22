# 公网版私人笔记






# 关于PaaS？


## 什么是PaaS?什么时候用PaaS?
云计算就是使用互联网来接入存储或运行在远程服务器端的应用、数据或者服务。

云计算是分层的。分别是IaaS(底层)、PaaS（中间层）、SaaS（顶层）

PaaS 平台即服务，面向软件开发者，云计算平台提供硬件、os、编程语言、开发库、部署工具，帮助软件开发者更快地开发软件服务。优点（为什么用？什么时候用？）：1、节省了硬件上的费用；2、PaaS excels when multiple developers are working on a single application. It allows for the simultaneous use of a single source code and the ability to automate testing and deployment.（build）

SaaS 软件即服务，面向软件消费者，无需安装，通过浏览器即可食用云计算平台提供的软件，比如goole的gmail。任何一个远程服务器上的应用都可以通过网络来运行，就是saas了（consume）

IaaS 基础设施即服务。购买服务器或硬件，或者外包（host）

资料来源：
http://www.leiphone.com/news/201406/iaas-paas-and-saas.html
http://www.zhihu.com/question/20387284
https://www.techopedia.com/2/28934/technology-trends/software-as-a-service-saas/choosing-between-iaas-and-paas-what-you-need-to-know

## 如何使用PaaS?(how)
换句话说，全球能免费运行python应用网络的有哪些PaaS?

SAE就是其中的一种。它的全称是Sina App Engine， 是新浪内部云计算平台。
http://www.sinacloud.com/doc/sae/python/index.html



# 通过sae创建公网版私人笔记

## 第1步：创建应用
在注册新浪云账号的前提下登录sae，进入[我的首页](http://sae.sina.com.cn/?m=dashboard)，点击创建新应用，创建一个新的应用jedsdiary。 开发语言选择Python。


## 第2步：代码管理
进入应用的代码管理栏目，选择git作为代码管理的工具
打开命令行，创建一个新的git远程仓库：

```$ git remote add sae https://git.sinacloud.com/jedsdiary```

将该仓库克隆到本地:

```$ git clone https://git.sinacloud.com/jedsdiary```

在文件夹中创建应用代码文件：

    cd jedsdiary
    echo >index.wsgi   #接口文件
    echo >jedsdiary.py    #应用代码文件
    git add index.wsgi    #将新文件放至暂存区
    git add jedsdiary.py
    git commit index.wsgi -m "make it better"  ＃提交至本次仓库
    git commit jedsdiary.py -m "make it better"
    git push sae master:1  ＃push到远程仓库


##第2步：编辑应用代码
首先创建应用的接口文件index.wsgi




