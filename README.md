# SimpleWebApllication

一：过程
1. 安装Flask （web框架）
2. 安装jinjia2
Flask默认支持的模板是jinja2，所以我们先直接安装jinja2

3. 使用MVC 结构

1）： 写app.py文件

Controller： 负责业务逻辑，检查输入的用户名密码是否正确
Model：app.py文件里接收浏览器的请求，组装成一个dict

还包括url和函数的对应关系

2）：写jinjia模板

form.html： 登陆页面 | 登陆失败页面（原来基础上加上红色信息提醒）

home.html （主页）

signi-ok.html （登陆成功）

4.注意

1): python app.py报错
OSError: [WinError 10013] An attempt was made to access a socket in a way forbidden by its access permissions

--原因是端口被占用

--解决办法是：flask默认端口是5000，我们改变默认端口，我们可以到 if __name__ == '__main__': 里指定 host名，端口名还有debug，如下
 if __name__ == '__main__':
     app.run(
       host='0.0.0.0',
       port= 5000,
       debug=True
     )

我们这里不需要改变host名字，所以我们更改如下

if __name__ == '__main__':
    app.run(
    port= 6000,
    debug=False)
    
2):在chrome里不能访问http://127.0.0.1:6000/ 页面，用ie就可以访问


二：基本介绍

1.Flask
Flask通过Python的装饰器在内部自动地把URL和函数给关联起来

2.MVC
作用： 分离了Python代码和HTML代码。HTML代码全部放到模板里，写起来更有效率 （模板Flask框架用的是jinjia2）

Model：传入关键字参数，然后，在框架内部组装出一个dict作为Model。Model是用来传给View的，这样View在替换变量的时候，就可以从Model中取出相应的数据

View： 包含变量{{ name }}的模板就是V：View，View负责显示逻辑，通过简单地替换一些变量，View最终输出的就是用户看到的HTML。

Controller： 负责业务逻辑，比如检查用户名是否存在，取出用户信息等等

3.jinjia2

在Jinja2模板中，我们用{{ name }}表示一个需要替换的变量。很多时候，还需要循环、条件判断等指令语句，在Jinja2中，用{% ... %}表示指令。
比如循环输出页码：

{% for i in page_list %}
    <a href="/page/{{ i }}">{{ i }}</a>
{% endfor %}


