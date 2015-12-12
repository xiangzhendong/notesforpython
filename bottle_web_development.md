# bottle web development







# 内建模版引擎

    # -*- coding:utf-8 -*-
    #encoding = utf-8
    from bottle import route, run,template
    
    """
    双大括号内的内容是待替换的内容。courses变量前加！是为了解析courses列表元素中html的内容。使用％在模板内容中输入python代码。
    """
    html="""
    hello {{name}}!
    I'm  {{age}}.
    My weight:{{int(weight)}}.
    My favourite courses:{{!courses}}
    MyTestclass {{mytest}}
    % if MyScore:
    <table>
        <tr>
            <td>subject</td>
            <td>score</td>
        </tr>
        % for (sub,score) in MyScore.items():
        <tr>
            <td>{{sub}}</td>
            <td>{{score}}</td>
        </tr>
        % end
    </table>
    % else:
    没有查询到该分数！
    % end
    """
    
    """
    下面自定义了一个类。
    """
    class MyTestclass:
        def __int__(self,x=0,y=0):
            self.x=x
            self.y=y
        def disp(self):
            return (self.x,self.y)
    
    @route('/stud/<name>')
    def index(name='Stranger'):
        age=12
        weight=34.5
        courses=['chinese', 'math', 'English','<a href="#">French</a>']    #第4个元素将在模板中解析出来而不是原样输出
        mytest=MyTestclass()    #创建类的实例
        MyScore={'chinese':99,'math':9,'English':87}
        MyScore=None    #这里是为了测试当查询分数没有时返回“没有查询到该分数！”而写的，可删除
        mypara=dict(name=name, age=age, weight=weight, courses=courses,mytest=mytest,MyScore=MyScore) #我们先将内容放入一个字典中，待会在template中使用**mypara解析出来，当然，这里括号里的内容也可以作为下面template里面的参数
        return template(html,**mypara)

    run(port='8080', debug=True, reloader=True)


