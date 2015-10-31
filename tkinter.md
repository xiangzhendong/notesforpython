# tkinter


## 什么是tkinter
Tk是一个图形库，它并不是python的一部分。python中的tkinter模块封装了访Tk的接口，完成图形界面的构建


## 如何使用tkinter


### 第1步：导入tkinter的所有内容
```import tkinter```

 or,more often:
```from tkinter import ＊```

>插曲：Tk T大写k小写

错误代码：

    import tkinter
    root tkinter.TK()
    root mainloop()

尝试1:```dir(tkinter)``` tkinter有属性"TK"

尝试2:[stackoverflow](http://stackoverflow.com/questions/20997761/tkinter-module-object-has-no-attribute-frame) 还是傻傻分不清楚

尝试3:[ibm](http://www.ibm.com/developerworks/cn/linux/sdk/python/charm-12/)

顿悟：Tk写成TK了

### 第2步：从Frame派生一个Application类，这是所有Widget的父容器
    class Application(Frame):
        def __init__(self, master=None):
            Frame.__init__(self, master)
            self.pack()
            self.createWidgets()

        def createWidgets(self):
            self.helloLabel = Label(self, text='Hello, world!')
            self.helloLabel.pack()
            self.quitButton = Button(self, text='Quit', command=self.quit)
            self.quitButton.pack()










