# thrift
    thrift 是一个跨语言的 rpc 框架, 它通过接口定义语言来进行代码生产,生成相应的 client 端和 server 端代码，由这些生成代码来与底层的相互调用，包括序列化和通信。

## 主要结构
 ![](https://upload.wikimedia.org/wikipedia/commons/d/df/Apache_Thrift_architecture.png)


 * Service Client／Server 这里的代码都是通过 IDL 生成出来的，业务层把传入的参数传到这里，再进去 TProtocol 协议层去处理数据。 或者从 TProtocol 那里接受到了数据，传给业务层去处理。
 * TProtocol 这里负责对不同结构的数据进行处理，按照数据的类型进行写入或者读取。
 * TTransport 负责以字节流的方式来处理接受或者发送数据
 * input/output 最底层负责数据的最终传输，以 socket 或者其他不同方式与网络层交互


 




参考资料 
    http://zheming.wang/blog/2014/08/28/94D1F945-40EC-45E4-ABAF-3B32DFFE4043/
