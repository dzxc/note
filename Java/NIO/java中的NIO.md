转自：http://www.watchmen.cn/portal.php?mod=view&aid=509
# 基本概念解析

1)阻塞和非阻塞:

阻塞和非阻塞是进程在访问数据的时候，数据内是否准备就绪的一种处理方式,当数据没有准备的时候  阻塞：往往需要等待缓冲区中的数据准备好过后才处理其他的事情，否则一直等待在那里

非阻塞:当我们的进程访问我们的数据缓冲区的时候  数据没有准备好的时候   直接返回 不需要等待.数据有的时候 也直接返回.

2）同步和异步的方式:

同步和异步都是基于应用程序和操作系统处理IO时间锁采用的方式.比如同步应用程序要直接参与IO读写的操作,异步：所有的IO读写交给操作系统去处理. 同步的方式在处理IO事件的时候 必须阻塞在某个方法上面等待我们的IO时间完成(阻塞IO事件或则通过轮询IO事件的方式),对于异步来说，所有的IO读写都交给了操作系统  这个时候  我们可以去做其他的事情  并不需要去完成真正的IO操作，当操作完成IO后 给我们的应用程序一个通知就可以的，

同步:1)阻塞到IO事件  阻塞到read  或则 write.  这个时候我们就完全不能做自己的事情.让读写方法加入到线程里面   然后阻塞线程来实现.对线程的性能开销比较大.

3)IO事件的轮询  --多路复用技术(select模式)

读写事件交给一个单独的线程来处理，这个完成IO事件的注册供，还有就是不断的去轮询我们的读写缓冲区  看是否有数据准备好。 通知我们通知相应读写线程. 这样的话  以前的读写线程就可以做其他的事情  这个时候阻塞的不是所有的IO线程   阻塞的select这个线程.

    Client                 Select  管家                BOSS

   当客人来的时候,就给管家说 我来了，管家得到这个注册信息后， 给BOSS说  我这里有一个或则多个客人  ，BOSS你去给某人A

这件东西，给另外人B这样东西。这个时候  客人是可以去做自己的事情的，比如看看花园等等， 当管家知道boss给他任务后 他就是去找对应的某人  告诉他boss给他某样东西。（根据我们的注册信息）
 

二.Java IO模型


BIO:JDK1.4以前我们使用都是BIO 阻塞IO

阻塞到我们的读写方法,阻塞到线程来提供性能.对于线程的开销本来就是性能的浪费.

NIO:jdk1.4  linux 多路复用技术(select模式)  实现IO事件的轮询方式:同步非阻塞的模式.这个种方式目前是主流的网络通信模式.

![](/Java/NIO/1.jpg)
Mina，netty    mina2.0    netty5.0---网络通信框架.比我直接写NIO要容易些  并且代码可读性更好

AIO:jdk1.7 (NIO2) 才是实现真正的异步aio，学习linux epoll模式

AIO使用的比较少,大家可以认真的学习一些思想

小结:1)BIO阻塞的IO

     2）NIO  select+非阻塞  同步非阻塞  

     3)异步非阻塞IO

3.NIO AIO原理的解读


对于网络通信而言NIO，AIO并没有改变网通通信的基本步骤，只是在其原来的基础上(serverscoket,socket)做了一个改进.
 

Socket     <----建立连接需要三次握手----->           serversocket

 
对于三次握手的方式建立稳定的连接性能开销比较大.解决方案从思想上来说比较容易  就是减少连接的次数.对我们的读写通信管道进行一个抽象.                               

 
4.NIO原理

 

通过selctor（选择器）就相当管家 ，管理所有的IO事件

 Connction   accept    客服端和服务端的读写.-----IO事件


selctor（选择器）如何进行管理IO事件

当IO事件注册给我们的选择器的时候   选择器会给他们分配一个key（可以简单的理解成一个时间的标签） 当IO事件完成过通过key值来找到相应的管道  然后通过管道发送数据和接收数据等操作.

 

数据缓冲区：

通过bytebuffer，提供很多读写的方法   put（）   get（）

 

服务端：ServerSocketChannel  

客服端:  SocketChannel  

选择器:  Selector  selector=Select.open();这样就打开了我们的选择器.



4.Selectionkey:



  可以通过它来判断IO事件是否已经就绪.

  key.isAccptable:是否可以接受客户端的连接

  Key.isconnctionable:是否可以连接服务端

  Key.isreadable():缓冲区是否可读

  Key.iswriteable():缓冲区是否可写



5.如何获得事件的keys

Selectionkey  keys=  Selector.selectedkeys();



6.如何注册

 channel.regist(Selector,Selectionkey.OP_Write);

 channel.regist(Selector,Selectionkey.OP_Read);

 channel.regist(Selector,Selectionkey.OP_Connct);

 channel.regist(Selector,Selectionkey.OP_Accept);


6.AIO:


服务端:AsynchronousServerSocketChannel

客服端:AsynchronousSocketChannel\

用户处理器:CompletionHandler接口,这个接口实现应用程序向操作系统发起IO请求,当完成后处理具体逻辑，否则做自己该做的事情.



