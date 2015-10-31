#输入文本 


# Entry Widgets

entry是tkinter用来获得用户输入的基本部件（widgets），它可以让用户输入单行文本。如果你想输入多行文本，就要使用text部件。entry的语法如下：

```w = Entry(master, option, ... ) ```

master代表父窗口（parent window），entry部件会布置在里面。像其他部件一样可以使用属性（options）来进一步修饰entry部件。

下面的程序创造了有两个entry区域的应用（这里没有使用属性）：

    from tkinter import *

    master = Tk()
    Label(master, text="First Name").grid(row=0)
    Label(master, text="Last Name").grid(row=1)

    e1 = Entry(master)
    e2 = Entry(master)

    e1.grid(row=0, column=1)
    e2.grid(row=1, column=1)

    mainloop()


程序运行结果：

![](屏幕快照 2015-10-31 下午10.18.24.png)

我们已经有了两个输入的地方，但是，我们的程序要如何获取这些数据呢？这就是get()方法的作用。

下面的程序使用了get()方法来获取用户输入，同时增加了两个按钮：

    from tkinter import *

    def show_entry_fields():
       print("First Name: %s\nLast Name: %s" % (e1.get(), e2.get()))

    master = Tk()
    Label(master, text="First Name").grid(row=0)
    Label(master, text="Last Name").grid(row=1)

    e1 = Entry(master)
    e2 = Entry(master)

    e1.grid(row=0, column=1)
    e2.grid(row=1, column=1)

    Button(master, text='Quit', command=master.quit).grid(row=3, column=0, sticky=W, pady=4)
    Button(master, text='Show', command=show_entry_fields).grid(row=3, column=1, sticky=W, pady=4)

    mainloop( )


如果我们想让输入框显示默认值怎么办？
    
    e1.insert(10,"Miller")
    e2.insert(10,"Jill")


如果我们想删除entry对象的输入怎么办？我们可以使用delete()方法：

    delete(first,last=None)
如果只有一个数字，就按索引删除对应字母。如果是两个数字，就删除first到last的字母。使用```delete(0,END)```删除部件内的所有文本。

    from tkinter import *

    def show_entry_fields():
       print("First Name: %s\nLast Name: %s" % (e1.get(), e2.get()))
       e1.delete(0,END)
       e2.delete(0,END)

    master = Tk()
    Label(master, text="First Name").grid(row=0)
    Label(master, text="Last Name").grid(row=1)

    e1 = Entry(master)
    e2 = Entry(master)
    e1.insert(10,"Miller")
    e2.insert(10,"Jill")

    e1.grid(row=0, column=1)
    e2.grid(row=1, column=1)

    Button(master, text='Quit', command=master.quit).grid(row=3,column=0, sticky=W, pady=4)
    Button(master, text='Show', command=show_entry_fields).grid(row=3, column=1, sticky=W, pady=4)

    mainloop( )

下面的程序让我们以更加pythonic的方式创建许多输入框：

    #!/usr/bin/python3

    from tkinter import *
    fields = 'Last Name', 'First Name', 'Job', 'Country'

    def fetch(entries):
       for entry in entries:
          field = entry[0]
          text  = entry[1].get()
          print('%s: "%s"' % (field, text)) 

    def makeform(root, fields):
        entries = []
        for field in fields:
            row = Frame(root)
            lab = Label(row, width=15, text=field, anchor='w')
            ent = Entry(row)
            row.pack(side=TOP, fill=X, padx=5, pady=5)
            lab.pack(side=LEFT)
            ent.pack(side=RIGHT, expand=YES, fill=X)
            entries.append((field, ent))
        return entries

    if __name__ == '__main__':
       root = Tk()
       ents = makeform(root, fields)
       root.bind('<Return>', (lambda event, e=ents: fetch(e)))   
       b1 = Button(root, text='Show',
          command=(lambda e=ents: fetch(e)))
       b1.pack(side=LEFT, padx=5, pady=5)
       b2 = Button(root, text='Quit', command=root.quit)
       b2.pack(side=LEFT, padx=5, pady=5)
       root.mainloop()



# Text Widgets






参考资料：

[Entry Widgets](http://www.python-course.eu/tkinter_entry_widgets.php)