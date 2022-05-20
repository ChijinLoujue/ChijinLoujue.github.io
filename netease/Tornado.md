# Tornado
Tornado龙卷风是一个开源的网络服务器框架
它是非阻塞式的服务器，速度相当快。这得益于其非阻塞的方式和对epoll的运用。Tornado每秒可以处理数以千计的连接，对于实时Web服务来说Tornado确实是一个理想的Web框架。
## 特点
轻量级Web框架
异步非阻塞IO处理方式
Tornado采用的单进程单线程异步IO的网络模式，其高性能源于Tornado基于Linux的Epoll（UNIX为kqueue）的异步网络IO。
出色的抗负载能力
不依赖多进程或多线程
WSGI全栈替代产品
WSGI把应用（Application）和服务器（Server）结合起来，Tornado既可以是WSGI应用也可以是WSGI服务。
既是WebServer也是WebFramework

[官方网站](https://www.tornadoweb.org/en/stable/)
[官方网站<中文>](https://tornado-zh-cn.readthedocs.io/zh_CN/latest/)
[GitHub主页](https://github.com/tornadoweb/tornado)
[WSGI](https://wsgi.readthedocs.io/en/latest/)
## 结构 
一个Web框架（包括RequestHandler子类以创建Web应用程序，以及各种支持类）。
HTTP（HTTPServer和 AsyncHTTPClient）的客户端和服务器端实现。
一个异步网络库，其中包括类IOLoop 和IOStream，这些类用作HTTP组件的构建块，还可以用于实现其他协议。
一个协程库（tornado.gen），它允许以比链接回调更直接的方式编写异步代码。这类似于Python 3.5（）中引入的本机协程功能。如果可用，建议使用本地协程代替模块。async deftornado.gen

## 异步&非阻塞IO
为了减小对于并发连接需要的开销,Tornado使用了一种单线程事件循环的方式. 这意味着所有应用程序代码都应该是异步和非阻塞的,因为在同一时刻只有一个操作是有效的.
## 阻塞
主要为网络I/O上下文阻塞
## 异步
函数在结束前已经返回，触发内容后后台执行任务，常用接口
回调函数  返回一个占用符  传送一个队列  回调注册（ex:POSIX信号）

Future

## 协程
Tornado 中推荐用 协程 来编写异步代码. 协程使用 Python 中的关键字 yield 来替代链式回调来实现挂起和继续程序的执行
在 Tornado 中所有协程使用异步函数来实现的明确的上下文切换
不浪费额外的线程

ython 3.5 引入了 async 和 await 关键字 (使用了这些关键字的函数通常被叫做 “native coroutines” ). 从 Tornado 4.3 开始, 在协程基础上你可以使用这些来代替 yield. 简单的通过使用 async def foo() 来代替 @gen.coroutine 装饰器, 用 await 来代替 yield. 文档的剩余部分还是使用 yield 来兼容旧版本的 Python, 但是 async 和 await 在可用时将会运行的更快

*协程：又称微线程，在单线程上执行多个任务，用函数切换，开销极小。不通过操作系统调度，没有进程、线程的切换开销。genvent，monkey.patchall
多线程请求返回是无序的，那个线程有数据返回就处理那个线程，而协程返回的数据是有序的。
缺陷：单线程执行，处理密集CPU和本地磁盘IO的时候，性能较低。处理网络I/O性能还是比较高.*
https://blog.csdn.net/zlx_csdn/article/details/79886705

一个含有yield的函数是一个生成器，调用时先返回一个对象，而不是运行完，@gen.coroutine 修饰器通过 yield 表达式通过产生一个 Future 对象和生成器进行通信.
使用 IOLoop.spawn_callback
IOLoop 负责调用. 如果它失败了, IOLoop 会在日志中记录调用栈

## 协程模式
**结合 callbacks**
为了使用回调来代替 Future 与异步代码进行交互, 讲这个调用报装在 Task 中. 这将会在你生成的 Future 对象中添加一个回调参数
**调用阻塞函数**
在协程中调用阻塞函数的最简单方法时通过使用 ThreadPoolExecutor, 这将返回与协程兼容的 Futures
**并行**
协程装饰器能识别列表或者字典中的 Futures ,并且并行等待这些 Futures
**交叉存取技术**
**循环**
**在后台运行**

## Tornado web 应用程序的结构
```py
import tornado.ioloop
import tornado.web

class MainHandler(tornado.web.RequestHandler):
    def get(self):
        self.write("Hello, world")

def make_app():
    return tornado.web.Application([
        (r"/", MainHandler),
    ])

if __name__ == "__main__":
    app = make_app()
    app.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```
## 异步网络
### tornado.ioloop —主事件循环
