# 极简交互式日记系统


## 任务
完成一个极简交互式日记系统,需求如下:

* 
一次接收输入一行日记
* 
保存为本地文件
* 
再次运行系统时,能打印出过往的所有日记


## 背景
系统环境：mac OSY 10.10.5

python版本：python 3.5.0


技术（1wd4）：

raw_input()

while+break while ＃执行无限循环，使用break来跳出循环

os.path.exists

open() ＃创建文件，w for writing,默认是r for reading

for in 回读

>小贴士
```import os```
```os.getcwd()```
搜索文件位置找到文件

## 版本1

    ＃-*- coding:utf-8 -*-
    mydiary=open(‘mydiary.txt’,’a’)
    while True:
        content=input(‘—>’)
        mydiary.write(content+’\n’)
        if content==‘q’:break
    mydiary.close()


执行程序，输入中文后返回错误：
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-5: ordinal not in range(128)

python unicode
python utf-8

尝试不写中文，看看程序运行结果：
i love you,suqin
when i am down
q
this is a bike
how are you
i am fine
q

q不用输入，修改：
mydiary=open(‘mydiary.txt’,’a’)
while True:
    content=input(‘—>’)
    if content==‘q’:break
    mydiary.write(content+’\n’)
 mydiary.close()


for line in open(‘mydiary.txt’):
    print(line,end=‘ ‘)

