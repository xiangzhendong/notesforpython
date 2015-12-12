# bottle web development







# 内建模版引擎

    # -*- coding:utf-8 -*-
    #encoding = utf-8
    from bottle import route, run,template
    
    """
    双大括号内的内容是待替换的内容。courses变量前加！是为了解析courses列表元素中html的内容。
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
        courses=['chinese', 'math', 'English','<a href="#">French</a>']
        mytest=MyTestclass()
        MyScore={'chinese':99,'math':9,'English':87}
        MyScore=None
        mypara=dict(name=name, age=age, weight=weight, courses=courses,mytest=mytest,MyScore=MyScore)
        return template(html,**mypara)

    run(port='8080', debug=True, reloader=True)


