# 百行go代码构建p2p聊天室

基于以太坊的whisper,可以很方便的进行p2p通信. 完全不需要服务器.

## 1. 上手使用
whisperv5是专门为以太坊上的DAPPS通信构建的,这里直接拿来做聊天系统了.
先说用法,来感受一下完全匿名的P2p聊天系统.
在终端运行p2pmessage.exe,然后等待出现.
`Connected to peer,you can type message now.`,这时候你就已经连接到whisper的p2p网络中了. 有可能你需要几分钟才能成功.
你可以收到来自别人的消息,也可以发送消息给别人.
你可以同时在不同的机器上启动程序来感受一下结果.
```
2017-09-11 11:31:18 <mine>: hello
input ~Q to quit>
2017-09-11 11:33:10 [182cbbaac94313b3b96b25d9c9a0a1adea4519e9]: who am i
```
第一行是收到了我发送的消息,第二行是提示输入,第三行是收到了182cbbaac94313b3b96b25d9c9a0a1adea4519e9发来的消息.
其中182cbbaac94313b3b96b25d9c9a0a1adea4519e9是结点标识.

## whisper 原理

接入whisper网络中的节点,在收到任何消息会首先验证一下工作量(可以参考bitmessage),如果没问题然后就转发.
同时也会看看是不是发送给我的,如果是就告诉用户.
至于怎么知道是不是发送给我的,有多种方式,这里只使用主题以及密码匹配.
也就是说,必须是我感兴趣的主题,同时加密的密码也是我指定的.那就可以愉快的聊天了.
当然,我没办法知道对方是谁,除非他告诉我.

## 源码解读
