# 前后端知识
## ssh
https://zhuanlan.zhihu.com/p/339808892
## 单点登录
## 单元测试
## 免密访问ssh
## 生成公私钥，将公钥存储到本地机器，然后就可以使用公钥直接ssh访问服务器，不需要输入密码。

## RESTful
- 其实是一种规范
https://www.cnblogs.com/zhangruifeng/p/13257731.html

## Devops开发运维一体化
https://zhuanlan.zhihu.com/p/310636980

## HTTP请求头
HTTP请求头用于说明是谁或什么在发送请求、请求源于何处，或者客户端的喜好及能力。服务器可以根据请求头部给出的客户端信息，试着为客户端提供更好的响应。
https://zhuanlan.zhihu.com/p/398740899


## get/post/put/delete的区别
1、GET请求向数据库发送请求数据的请求，获取信息。 此请求与数据库中的select操作类似，只是用于检查数据，而不修改或增加数据。 不影响资源的内容。 也就是说，这个要求不会产生副作用。 不管操作多少次，结果都是一样的。
  2、与GET不同，PUT请求向服务器端发送数据，改变信息。 此请求用于修改数据内容，就像数据库的update操作一样，但不会增加数据类型等。 也就是说，无论进行多少次PUT操作，其结果都不会改变。
  3、POST请求同PUT请求类似，都是向服务器端发送数据，但该请求会改变数据类型等资源，创建新的内容，就像数据库的insert操作一样。 目前，大多数提交操作都是开机自检要求的。
  4、DELETE请求顾名思义，是为了删除某个资源，该请求就像数据库中的DELETE操作一样。
  如上所述，既然PUT和POST操作都向服务端发送数据，那么这两者有什么区别呢？ POST主要作用于一个集合资源上的( url )，PUT主要作用于一个具体资源上的( url/xxx )，通俗地说，如果url在客户端可以确定，则使用PUT，否则使用POST

## http协议
●Http是无状态的协议，服务器不能记录浏览器的访问状态，也就是说服务器不能区分两次请求是否是同一个客户端，这样的设计严重阻碍了web程序的设计。
●Cookie是解决Http协议无状态的方案之一。
●Cookie实际上就是服务器保存在浏览器上的一段信息，浏览器有了Cookie之后，每次向服务器发送请求时都会将该信息发送给服务器，服务器在收到请求之后，就可以根据该信息处理请求。

## 用户认证方式
- 所谓用户认证（Authentication），就是让用户登录，并且在接下来的一段时间内让用户访问网站时可以使用其账户，而不需要再次登录的机制。
http://blog.leapoahead.com/2015/09/07/user-authentication-with-jwt/

- 可别把用户认证和用户授权（Authorization）搞混了。用户授权指的是规定并允许用户使用自己的权限，例如发布帖子、管理站点等。
- 基于token ，jwt属于其中一种
- 基于session
https://blog.csdn.net/qq_53267860/article/details/123238821?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-123238821-blog-113962652.235^v36^pc_relevant_default_base3&spm=1001.2101.3001.4242.1&utm_relevant_index=3

## session+cookie的会话保持技术


## cookie和session的区别
https://blog.csdn.net/m0_65421722/article/details/127813102
cookie和session都是用来跟踪浏览器用户身份的会话方式。


## jwt
JWT只是一个令牌格式而已，你可以把它存储到Cookie，也可以存储到localstorage，没有任何限制！同样的，对于传输，你可以使用任何传输方式来传输JWT，一般来说，我们会使用HTTP消息头来传输它。
流程
1.首先，前端通过Web表单将自己的用户名和密码发送到后端的接口，这个过程一般是一个POST请求。建议的方式是通过SSL加密的传输(HTTPS)，从而避免敏感信息被嗅探
2.后端核对用户名和密码成功后，将包含用户信息的数据作为JWT的Payload，将其与JWT Header分别进行Base64编码拼接后签名，形成一个JWT Token，形成的JWT Token就是一个如同lll.zzz.xxx的字符串
3.后端将JWT Token字符串作为登录成功的结果返回给前端。前端可以将返回的结果保存在浏览器中，退出登录时删除保存的JWT Token即可
4.前端在每次请求时将JWT Token放入HTTP请求头中的Authorization属性中(解决XSS和XSRF问题)
5.后端检查前端传过来的JWT Token，验证其有效性，比如检查签名是否正确、是否过期、token的接收方是否是自己等等
6.验证通过后，后端解析出JWT Token中包含的用户信息，进行其他逻辑操作(一般是根据用户信息得到权限等)，返回结果

## Reactive Programming 敏捷开发


# golang
Golang中一个完整的http服务，包括注册路由，开启监听，处理连接，路由处理函数。
●路由注册：建立URL路径与处理器函数（也可以叫控制器函数）的对应关系。https://blog.csdn.net/gz_hm/article/details/123059990
●分组路由：把同样模块的功能安排到一个分组中 / 支持多个api版本。https://blog.csdn.net/gz_hm/article/details/123059990



- handler router
- 处理器
- 路由器
- gin