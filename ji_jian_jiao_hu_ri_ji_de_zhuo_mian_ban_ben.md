# 极简交互日记的桌面版本




## 版本1

先解决主要矛盾：输入文本并保存（输入多行文本、输入中文、输入框大小等暂时不处理）

    from tkinter import *
    import tkinter as tk
    class myapp(tk.Tk):
        def __init__(self):
            tk.Tk.__init__(self)
            self.entry=tk.Entry(self)
            self.button=tk.Button(self,text='save',command=self.on_button)
            self.button.pack()
            self.entry.pack()
        def on_button(self):
            mydiary=open('mydiary.txt','a')
            mydiary.write(self.entry.get()+'\n')
            mydiary.close()
    
    app=myapp()
    app.mainloop()



 ##版本2
目标：输入多行文本

    from tkinter import *
    import tkinter as tk
    class myapp(tk.Tk):
        def __init__(self):
            tk.Tk.__init__(self)
            self.text=tk.Text(self)
            self.button=tk.Button(self,text='save',command=self.on_button)
            self.button1=tk.Button(self,text=‘quit’,command=quit)
            self.button.pack()
            self.button1.pack
            self.text.pack()
        def on_button(self):
            mydiary=open('mydiary.txt','a')
            mydiary.write(self.text.get(1.0,END)+'\n')
            mydiary.close()
    
    app=myapp()
    app.mainloop()




参考资料：

[Tkinter Entry “get” function is returning nothing](http://stackoverflow.com/questions/10727131/tkinter-entry-get-function-is-returning-nothing)