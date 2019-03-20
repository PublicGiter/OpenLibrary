# Golang Library



#### mqtt

- 链接:：https://github.com/eclipse/paho.mqtt.golang

- 描述：MQTT(消息队列遥测传输)是ISO 标准(ISO/IEC PRF 20922)下基于发布/订阅范式的消息协议。它工作在 TCP/IP协议族上，是为硬件性能低下的远程设备以及网络状况糟糕的情况下而设计的发布/订阅型消息协议，为此，它需要一个消息中间件 。
- 使用情况：
  - 如果设置AutoReconnect（掉线自动重连），函数IsConnected返回值会失效。
  - 如果不设置自动重连，自己实现自动重连可能会有描述符泄露，掉线后调用Disconnect函数会panic？
  - 如果在CallbackHandler中实现自动重连，如果CleanSession为false的话，应该在OnConnected中重新Subscribe。

#### beego

- 链接：https://github.com/astaxie/beego
- 描述：beego是一个快速开发Go应用的http框架，go 语言方面技术大牛。beego可以用来快速开发API、Web、后端服务等各种应用，是一个RESTFul的框架，主要设计灵感来源于tornado、sinatra、flask这三个框架，但是结合了Go本身的一些特性(interface、struct继承等)而设计的一个框架。
- 使用情况：
  - Controller 是通过反射生成，router中注册的Controller对象是无效的（比较坑。。）
  - beego 的 orm 不是很好用。。。

#### fsnotify

- 链接：https://github.com/fsnotify/fsnotify
- 描述：
  - When a file or directory is created, modified or removed, the Operating System can inform any applications that wish to know. This can come in handy in many situations:
  - Text editors know a file has changed externally and may offer to reload it.
  - Applications know that there are changes to backup (Time Machine, Arq) or synchronize (Dropbox).
  - Search engines (Spotlight) can update their search indexes.
  - Static site generators (Hugo) can serve up changes as they are made.
  - Development tools can rebuild code or run tests automatically.
  - To make this work, an application simply subscribes to be notified of events.
- 使用情况：
  - 不同的文本编辑器写入磁盘行为不同，可能一次保存，fsnotify监听到多个事件。
  - 其他类似的库：
    - notify: https://github.com/rjeczalik/notify
    - fsevents: https://github.com/fsnotify/fsevents

#### lua

- 链接：https://github.com/yuin/gopher-lua
- 描述：GopherLua is a Lua5.1 VM and compiler written in Go. GopherLua has a same goal with Lua: Be a scripting language with extensible semantics . It provides Go APIs that allow you to easily embed a scripting language to your Go host programs.
- 使用情况：
  - 使用JSON4库，json.decode函数不能正常解析json数据，使用dkjson可以正常解析（可能VM支持不全面）。
  - 可以与golang双向交互数据，双向函数调用。

#### javascript

- 链接：https://github.com/robertkrimen/otto
- 描述：Package otto is a JavaScript parser and interpreter written natively in Go.
- 使用情况：
  - 可以轻松与golang双向数据交互及双向函数调用。

#### python

- 链接：https://github.com/sbinet/go-python
- 描述：
  - Naive go bindings towards the C-API of CPython-2.
  - this package provides a go package named "python" under which most of the PyXYZ functions and macros of the public C-API of CPython have been exposed.
- 使用情况：
  - 不是原生golang写的，用cgo包装，把PyObject包装成对象方式。
  - 可以双向数据交互，但只能单向函数调用（go call python）。

#### modbus

- 链接：https://github.com/goburrow/modbus
- 描述：Fault-tolerant implementation of modbus protocol in Go (golang)
- 使用情况：
  - 对SlaveID参数支持不是很好，在操作（读写）前可以直接修改ClientHandler中的SlaveID，也可以创建多个handler。

