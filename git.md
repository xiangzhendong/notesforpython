# github和gitbook的双推实现

git是一个版本管理系统。git有3种状态，你的文件可能处于其中之一：已提交（committed）、已修改（modified）和已暂存（staged）。已提交表示数据已经安全的保存在本地数据库中。已修改表示修改了文件，但还没保存到数据库中。已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。

由此引入 Git项目的三个工作区域的概念：Git 仓库、工作目录以及暂存区域。

基本的 Git 工作流程如下：

1. 
在工作目录中修改文件。

2. 
暂存文件，将文件的快照放入暂存区域。

3. 
提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录。




## 获得帮助
```git help```




## 克隆现有的仓库

```$ git clone https://github.com/libgit2/libgit2 <mylibgit>``` 
括号里的内容用于命名，可写可不写。初次克隆某个仓库的时候，工作目录中的所有文件都属于已跟踪文件，并处于未修改状态。

检查当前文件状态

git status



echo (‘OMOOC2py’) >test

在状态报告中你会看到信件的TESTTEST文件出现在untracked files下面



跟踪新文件

使用git add开始跟踪一个文件，这时你会看到TESTTEST文件已被跟踪，并处于暂存状态（changes to be committed）

git add 可以开始跟踪新文件，或者把已跟踪的文件（修改）放到暂存区

vim test
编辑文件，编辑完成后点击esc，并输入<:wq!>，即写入（w）并退出（q）
此时使用git status命令查看文件状态时会发现，test同时出现在暂存区和非暂存区
实际上git只是暂存了你运行git add命令时的版本，如果你做了修改，需要重新运行git add把最新版本重新暂存起来
查看已暂存和未暂存的修改
要查看尚未暂存的文件更新了哪些部分，不加参数直接输入git diff（diff是指工作目录中当前文件和暂存区域快照之间的差异，也就是修改之后还没有暂存起来的变化内容）
要查看已暂存的将要添加到瑕疵提交里的内容，可以用git diff －－cached命令
将test暂存后再编辑，运行git status会看到暂存前后的两个版本
git add test
echo ‘＃ test line’>>test
git status
运行git diff看暂存前后的变化
图
运行git diff －－cached查看已经暂存起来的变化

提交的时候不会记录没有暂存的变化。所以，提交时先用git status命令看下是不是都已暂存起来了，然后再git commit -m “<提交信息>"
跳过使用暂存区域
git commit -a -m “add new benchmarks”
git会自动把所有已跟踪文件暂存起来一并提交，不需要git add命令

删除文件
git rm test
如果删除之前修改过且放入暂存区的话，则要用强制删除选项－f（force）
此外，我们想把文件从git仓库中删除（即从暂存区移除），但仍希望保留在当前工作目录中，git rm —cached test

git push 同步到远程仓库


