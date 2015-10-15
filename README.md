# 写在前面



如何配置DISQUS插件？

解决过程：
从[Gitbook官方教程](help.gitbook.io)的plungis一章找到[plugins帮助文档那个](https://plugins.gitbook.com/plugin/disqus)，得知Install the Disqus plugin via NPM。如果要配置插件，就要先知道NPM是什么，如何获得。于是百度搜索“gitbook 插件 npm”，返回结果：
[使用Gitbook制作电子书](http://www.ituring.com.cn/article/127645)。从这篇文章得知从[npm官方网站](https://nodejs.org/en/)可以下载安装NPM。 

反思：如果要下载npm以及获知npm的使用信息，可以直接找到[npm的官网](https://www.npmjs.com)和查看documentation。节省无用信息筛选成本

下载安装node.js后，回到[plugins帮助文档](https://plugins.gitbook.com/plugin/disqus)。
问题：npm是什么？怎么操作？

打开终端，按npm帮助文档的提示安装npm并检查安装版本：
$ node -v #检查node.js版本
$ sudo npm install npm -g 
$ npm -v
![](38.pic.jpg)

回到[plugins帮助文档](https://plugins.gitbook.com/plugin/disqus)，按操作安装disqus插件：
$ sudo npm install gitbook-plugin-disqus -g
![](屏幕快照 2015-10-14 下午10.29.05.png)

To use the Disqus plugin in your Gitbook project, add the disqus plugin to the book.json file, along with your shortname (you create a shortname for disqus by creating a new website on the disqus.com website)
问题：什么是book.json?怎么操作？

推测可能在gitbook的编辑器里，于是误打误撞通过右上角的设置添加了disqus插件：
![](屏幕快照 2015-10-14 下午10.45.06.png)

这时文件树里多了book.json文件，恍然大悟，点击查看代码内容，按[plugins帮助文档](https://plugins.gitbook.com/plugin/disqus)说明编写代码将disqus插件添加到book.json文件。
{
    "plugins": ["disqus"],
    "pluginsConfig": {
        "disqus": {
            "shortName": "notesforpython"  ＃在disqus上创建的channel
        }
    }  
}

大功告成？
在create your page点击read时发现：This book has not been published yet

回到[gitbook官方教程](http://help.gitbook.com/build/index.html)，在build章得知：
为了build website，首先要使用git或gitbook editor push content
问题：如何使用gitbook editor push content？

尝试1：在设置中添加push插件。失败，无push插件
尝试2：在book.json中添加代码。为此，在百度中搜索“gitbook editor push content”，找到[gitbook简明教程](http://www.colobu.com/2014/10/09/gitbook-quickstart/)。在book.json中添加如下代码：

$ gitbook build ./repository --output=./outputFolder

成功！

成功？
现象：We were unable to load Disqus.

尝试1：问题旁边直接附有[帮助文档](https://help.disqus.com/customer/portal/articles/472007-i-m-receiving-the-message-%22we-were-unable-to-load-disqus-%22)。查看帮助文档，看不懂，暂且放弃，转换思路。

尝试2:重新研读[plugins帮助文档](https://plugins.gitbook.com/plugin/disqus)
you create a shortname for disqus by creating a new website on the disqus.com website
我在disqus那边创建了一个channel，与这里的website是不是一个概念？这个问题的答案在disques的帮助文档里一定有，于是找到[disques帮助文档](https://help.disqus.com)，搜索“create website”，返回结果：
Disqus Sites and Channels
On Disqus, there are two different ways to facilitate Discussions and encourage conversation: Sites and Channe...
A single embed code gives you access to both Engage and Reveal for your Site.
进入[engage](https://publishers.disqus.com/engage)创建website，命名为notesforpythonjed
在book.json中将shortName修改为notesforpythonjed
刷新浏览器，disqus插件已添加到gitbook
大功告成！！


重要资源：

[Gitbook官方教程](help.gitbook.io)
