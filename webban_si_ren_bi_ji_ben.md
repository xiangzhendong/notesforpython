# web版私人笔记本






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