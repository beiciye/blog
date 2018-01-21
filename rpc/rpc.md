# thrift 介绍

## rpc
    rpc 英文名是 Remote Procedure Call，远程过程调用。 rpc 的目的是为了方便进行远程调用， 想达到的结果是想本地调用一样去调用远程服务。 它的本质过程是把网络通信这一块封装起来，抽象出网络层，使开发人员专注于自己业务逻辑的开发，而不用去考虑复杂的通讯过程。


## rpc 的过程

> 流程图如下

![](http://7xjuf4.com1.z0.glb.clouddn.com/thrift_rpc_rpc.PNG)

> rpc 通常是以下的流程

    1.The client calls the client stub. The call is a local procedure call, with parameters pushed on to the stack in the normal way.

    2.The client stub packs the parameters into a message and makes a system call to send the message. Packing the parameters is called marshalling.

    3.The client’s local operating system sends the message from the client machine to the server machine.

    4.The local operating system on the server machine passes the incoming packets to the server stub.

    5.The server stub unpacks the parameters from the message. Unpacking the parameters is called unmarshalling.

    6.Finally, the server stub calls the server procedure. The reply traces the same steps in the reverse direction


## rpc 框架做的事
不同框架会有对以上几个过程有不同的实现。 基于以上 rpc 通信的过程，生产环境中应用 rpc 框架通常做这么几件事。
* 有对应的 IDL(Interface Description Language -- 接口定义语言) 来定义接口，并生成对应的 client 端和 server 端代码
* 序列化与反序列化
* 通信，数据在底层的传输，可以基于不同网络协议
* 不同接口方法到其对应 handle 的映射
