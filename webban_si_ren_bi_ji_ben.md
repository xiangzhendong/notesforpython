# web版私人笔记本


# 开发环境
ipython外加一个文本编辑器（vim）


## 在iterm(命令行工具)创建文件并编辑
 ```pwd``` ＃查看当前文件夹位置
 
```cd /Users/xiangzhendong/OMOOC2py/_src/om2py4w``` ＃进入指定文件夹；技巧：将文件夹拖动到命令行便能显示文件夹位置

```echo > login.py``` #创建文件

```vim login.py```    ＃使用vim编辑文件


按ESC键 跳到命令模式，然后：

:w   保存文件但不退出vi
:w file 将修改另外保存到file中，不退出vi
:w!   强制保存，不推出vi
:wq  保存文件并退出vi
:wq! 强制保存文件，并退出vi
q:  不保存文件，退出vi
:q! 不保存文件，强制退出vi
:e! 放弃所有修改，从上次保存文件开始再编辑
按i键键入插入模式 下方显示—insert--


## 在ipython粘贴代码

在iterm中输入```ipython```进入ipython模式

If you want to paste code into IPython, try the %paste and %cpaste magic functions.

You can't copy to IPython directly. This are the steps:

Copy the lines you want to copy into IPython into the clipboard
Enter %paste into IPython
Press enter
Profit!

另一种说法：

A clarification on the steps:

First, copy target lines into your clipboard.

Type into the iPython prompt:

If on Tkinter: enter %paste
Otherwise: enter %cpaste
Paste (Ctrl-V) and hit enter.

Then type -- and hit enter.

[参考资料](http://stackoverflow.com/questions/10886946/how-does-ipythons-magic-paste-work)





# 版本迭代
## 版本1:输入与保存


    from bottle import get, post, request, run

    @get('/writediary')
    def writediary():
        return '''
            <form action='/writediary' method='post' >
                diary:<input name='diary' type='text'/> 
            </form>
     '''

    @post('/writediary')
    def savediary():
        mydiary=open('mydiary.txt', 'a')
        mydiary.write(request.forms.get('diary')+'\n')
        mydiary.close()
        return open('mydiary.txt').read()

    run(host='localhost', port=8080, debug=True) 