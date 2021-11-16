# 基础题

## 练习一:ip地址和端口号概念

描述:

1.  请写出IP地址的概念：

2.  请写出端口号的概念：

答案:

```java
IP地址:互联网协议地址(Internet Protocol
Address),俗称IP.IP地址用来给一个网络中的计算机设备做唯一的编号.

端口号:端口号用来给计算机里的应用程序(进程)做唯一的标识,用2个字节表示的整数,取值范围0\~65535.
```



## 练习二:UDP协议

判断下列说法是否正确

由于UDP面向无连接的协议,可以保证数据完整性,因此在传输重要数据时采用UDP协议.

答案

```java
判断错误,因为面向无连接,容易丢失包,所以不能保证数据完整.
```



## 练习三:TCP协议

TCP协议中”三次握手”,第一次握手指的是什么：

答案

```java
第一次握手:客户端向服务器发送请求,等待服务器确认
```



## 练习四:TCP网络程序

需求说明：创建新项目，按以下要求编写代码：

在项目下创建TCP 服务器端 端口号为8888

1:等待客户端连接 如果有客户端连接 获取到客户端对象

2:获取到客户端对象之后 当前在服务器读取数据客户端传送数据

答案

```java
public class TCPServer {

public static void main(String[] args) throws Exception {

//1创建服务器对象

ServerSocket ss = new ServerSocket(8888);

//2等待客户端连接 如果有客户端连接 获取到客户端对象

Socket socket = ss.accept();

//3当前在服务器中 要读取数据 需要输入流 流由谁提供 客户端

InputStream in = socket.getInputStream();//获取输入流

//4:读数据

int len;

byte[] buffer = new byte[1024];

while((len=in.read(buffer))!=-1){

System.out.println(new String(buffer, 0, len));

}

//释放资源

in.close();

// ss.close();服务器一般不会关闭

}

}
```



## 练习五:TCP网络程序

需求说明：创建新项目，按以下要求编写代码：

在项目下创建TCP 客户端

访问之前创建的服务器端,服务器端ip127.0.0.1 端口号8888

1:客户端连接服务器,并发送 hello.服务器,我是客户端.

2:开启上一题服务器,等待客户端连接,客户端连接并发送数据

答案:

```java
public class TCPClient {

public static void main(String[] args) throws Exception {

//创建 Socket客户端对象

Socket socket = new Socket("127.0.0.1", 8888);

//写数据 需要输出流 谁提供 客户端

OutputStream out = socket.getOutputStream();

//写数据

out.write("hello.服务器,我是客户端.".getBytes());

//释放资源

out.close();

socket.close();

}

}
```

