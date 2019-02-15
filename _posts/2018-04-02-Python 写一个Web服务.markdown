---
layout:		post
title: 		Python 写一个Web服务
date: 		2018-04-02 15:23:22
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
#  Python 写一个Web服务

##  本文目的：

写一个简单的Python服务，可以通过http请求访问该服务。

##  代码实现：

    
    
    # coding:utf-8
    
    import socket   # 导入socket包
    # multiprocessing包是Python中的多进程管理包
    # 在 multiprocessing 中，通过创建 Process 对象然后调用其 start() 方法来生成进程。 Process 遵循 threading.Thread 的API。多进程程序的一个简单例子是
    from multiprocessing import Process
    
    # 定义客户端处理函数
    def handle_client(client_socket):
        """处理客户端请求"""
        # 获取客户端请求数据
        request_data = client_socket.recv(1024)     #接收TCP数据，数据以字符串形式返回。指定要接收的最大数据量为1024字节
        print("request data:", request_data)        #打印客户端请求的数据
    
        # 构造响应数据
        response_start_line = "HTTP/1.1 200 OK\r\n"
        response_headers = "Server: My server\r\n"
        response_body = "hello wtclab"
        response = response_start_line + response_headers + "\r\n" + response_body
        print("response data:", response)
    
        client_socket.send(bytes(response, "utf-8")) # 向客户端返回响应数据
        client_socket.close()# 关闭客户端连接
    
    
    if __name__=="__main__":
        server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)   # 创建TCP Socket对像
        server_socket.bind(("", 8000))  # 将套接字绑定到地址和端口，在AF_INET下，以tuple(host, port)的方式传入，如s.bind((host, port))
        server_socket.listen(120)   # 开始监听TCP传入连接，backlog指定在拒绝链接前，操作系统可以挂起的最大连接数，该值最少为1，大部分应用程序设为5就够用了
    
        while True:
            client_socket, client_address = server_socket.accept()  # accept()方法接受TCP链接并返回（conn, address），其中conn是新的套接字对象，可以用来接收和发送数据，address是链接客户端的地址。
            print("[%s, %s]用户连接上了" % client_address)    # 打印连接的客户端的IP作为提示信息
            # Process([group [, target [, name [, args [, kwargs]]]]])，target表示调用对象，args表示调用对象的位置参数元组。kwargs表示调用对象的字典。name为别名。group实质上不使用。
            handle_client_process = Process(target=handle_client, args=(client_socket,))
            handle_client_process.start()# 启动进程
            client_socket.close()   #关闭socket

运行后在浏览器输入：127.0.0.1:8000

###  http页面显示如下：

![这里写图片描述](https://img-blog.csdn.net/20180402152152374?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  控制台输出如下：

![这里写图片描述](https://img-blog.csdn.net/20180402152242402?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

参考资料：  
1、 [ python 写一个静态服务（实战）
](https://blog.csdn.net/qq_30262201/article/details/78797364)  
2、 [ Python Socket 编程详细介绍
](https://gist.github.com/kevinkindom/108ffd675cb9253f8f71)  
3、 [ multiprocessing —基于过程的并行性
](https://www.rddoc.com/doc/Python/3.6.0/zh/library/multiprocessing
/#multiprocessing-programming)  
4、 [ Python 网络编程 ](https://www.w3cschool.cn/python/python-socket.html)

