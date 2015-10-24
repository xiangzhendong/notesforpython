# 42行代码

任务：在脚本编辑器中运行[42行代码](http://wiki.woodpecker.org.cn/moin/ZqQuickIntoPy)并返回正确结果


### 背景
系统环境：OS X 10.10.5


### 安装
从[python官网](https://www.python.org/downloads/)获取安装包并安装

问题：之前在win系统下python的脚本编辑器有CLI和GUI两个版本，为什么mac环境下只有一个IDLE?

尝试：
在[docs](https://docs.python.org/3/)里面搜索"GUI",返回结果[Using Python on a Macintosh](https://docs.python.org/3/using/mac.html?highlight=gui)，其中4.1.2 Running scripts with a GUI就此问题解释：

With older versions of Python, there is one Mac OS X quirk that you need to be aware of: programs that talk to the Aqua window manager (in other words, anything that has a GUI) need to be run in a special way. Use pythonw instead of python to start such scripts.

With Python 3.4, you can use either python or pythonw


 
