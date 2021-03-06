# HTTP 协议
#### HTTP 基本概念
- #### 超文本传输协议(Hypertext Transfer Protocol，简称HTTP)，与 FTP 、Telnet、SMTP 等协议一样，是应用层协议。

- #### 1997年1月，HTTP/1.1 版本发布，相比 1.0 版本它进一步完善了 HTTP 协议，直到现在还是最流行的版本。

- #### HTTP/1.1 版本最大的变化，就是引入了持久连接（persistent connection），即 TCP 连接默认不关闭，可以被多个请求复用，不需要明确声明 Connection: keep-alive。客户端和服务器发现对方一段时间没有活动，都可以主动关闭连接。不过，规范的做法是，客户端在最后一个请求时，发送Connection: close，明确要求服务器关闭TCP连接。







---
#### Content-Type
Content-Type类型 | 浏览器处理方式
--|--
text/html | 作为html文档
text/plain | 无格式正文，不解析直接输出






---
#### HTTP 请求报文
![请求报文结构](https://github.com/StRothschild/NetWork/blob/master/resource/NetWork%20%E2%80%94%20HTTP%20%E8%AF%B7%E6%B1%82%E4%BD%93%E7%BB%93%E6%9E%84.jpg?raw=true)

#### 1. 请求行
  - #### 方法 URI 协议/版本（GET https://github.com:80/ HTTP/1.1）
  - #### 十分类似于 XMLHttpRequest 中的 xhr.open(method, url, isAsync)

#### 2. 请求首部(Request Header)
  - ##### Host：目标域名，例如 www.baidu.com
  - ##### User-Agent：Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.7.6)
  - ##### Accept：text/plain, text/html
  - ##### Accept-Charset：utf-8
  - ##### Accept-Encoding：gzip, deflate, sdch, br
  - ##### Accept-Language：zh-CN,zh;q=0.8
  - ##### Connection：close
  - ##### Cookie：HTTP 请求发送时，会把保存在该请求域名下的所有 cookie 值一起发送给 web 服务器
  - ##### Referer：这个单词是 HTTP 规范拼错了，正确的单词是 referrer。这个属性表示发出该请求的页面 url。

  - ##### Content-Type：表示内容的类型，比如 application/x-www-form-urlencoded 表示表单类型的数据，还有 text/plain 等类型
  - ##### Content-Length：请求消息正文的长度，GET 请求时为 0
  - ##### Cache-Control：no-cache
  - ##### Date：浏览器消息发出的时间




#### 3. 空行
  ##### 即使第四部分的请求数据为空，也必须有空行。

#### 4. 请求体(Request body)
  ##### 请求数据，可以为空






---
#### HTTP 响应报文
![响应报文结构](https://github.com/StRothschild/NetWork/blob/master/resource/NetWork%20%E2%80%94%20HTTP%20%E5%93%8D%E5%BA%94%E4%BD%93%E7%BB%93%E6%9E%84.png?raw=true)

#### 1. 响应行
  - #### 协议/版本 状态码 状态说明（HTTP/1.1 200 OK）

#### 2. 响应首部(Response Header)
  - ##### Content-Type: text/html
  - ##### Content-Length: 响应体的长度
  - ##### Cache-Control: no-cache
  - ##### Date: 原始服务器消息发出的时间
  - ##### Expires: 响应过期的日期和时间
  - ##### Last-Modified: 请求资源的最后修改时间
  - ##### Content-Disposition: 指示响应的内容该以何种形式展示，是以内联的形式（即网页或者页面的一部分，值为 inline, 是默认值），还是以附件的形式下载并保存到本地（attachment 或者 attachment;filename="fileName"）。



#### 3. 空行
  ##### 即使第四部分的请求数据为空，也必须有空行。

#### 4. 响应体(Response body)
  ##### 返回的数据，可以为空






---
#### HTTP 请求方法
#### HTTP 请求方法主要有十多种，这些方法中，常用的有 POST、GET、PUT、DELETE。除了 GET 方法外，其他几个方法区别不大，甚至可以混用。要区分他们的用法，主要看请求的目的。这类似于 HTML 中标签语义化的概念。

- PUT（增）
- DELETE（删）
- POST（改）
- GET（查）
- HEAD（ HEAD 与 GET 十分相似，只不过 HEAD 请求只返回响应头，而不会发送响应内容。当我们只需要查看某个资源的状态的时候，使用 HEAD 是非常高效的，因为在传输的过程中省去了资源内容）
- OPTIONS
- TRACE
- CONNECT

- PATCH
- COPY
- MOVE
- LINK
- UNLINk
- WRAPPED
- Extension-mothed






---
#### GET 与 POST 的区别

  - 从 HTTP 协议的角度来看，不同的 method 之间最重要的是语义之间的区别，这个概念很类似与 HTML 标签。GET 代表的语义是 查询资源，而 POST 的语义是修改资源。

  - GET 可以使用缓存文件（304）；POST 无法使用缓存文件，因为它主要用于更新服务器上的文件或数据库。

  - 通过 GET 提交的数据必须放在 URL 中；而通过 POST 提交的数据放在请求体中。

  - GET 方式提交的数据最多只能是 1024 字节；而 POST 理论上没有限制，可传较大量的数据。

  - 通过 GET 提交数据，信息明文出现在 URL 上，所以有可能通过浏览器的页面缓存，或是历史纪录造成数据泄露。除此之外，使用GET提交数据还可能会造成 Cross-site request forgery 攻击。

  - GET 和 POST 都是明文传输，可能被抓包，所以都不安全。想要安全最好进行加密传输，就是用 HTTPS。





---
#### HTTP 状态码（status）
##### status 状态码由三位数字组成，第一位数字表示响应的类型，常用的状态码有五大类如下所示：

- #### 1xx：信息，服务器收到请求，需要请求者继续执行操作;

- #### 2xx：成功，操作被成功接收并处理;

- #### 3xx：重定向，需要进一步的操作以完成请求;

- #### 4xx：客户端错误，请求包含语法错误或无法完成请求;

- #### 5xx：服务器错误，服务器在处理请求的过程中发生了错误;

##### 常见的状态码及含义如下所示：
- #### 200 OK：表示客户端请求成功;

- #### 304 Not Modified：表示服务器告诉客户端，原来缓存的的资源没有过期，还可以继续使用;

- #### 400 Bad Request：表示客户端请求有语法错误，不能被服务器所理解;
- #### 401 Unauthonzed：表示请求未经授权，该状态代码必须与 WWW-Authenticate 报头域一起使用;
- #### 403 Forbidden：表示服务器收到请求，但是拒绝提供服务，通常会在响应正文中给出不提供服务的原因;
- #### 404 Not Found：表示请求的资源不存在，例如，输入了错误的URL;

- #### 500 Internal Server Error：表示服务器发生不可预期的错误，导致无法完成客户端的请求;
- #### 501 Not Implemented： 表示服务器无法识别或不支持当前请求所需要的资源;
- #### 503 Service Unavailable：表示服务器当前不能够处理客户端的请求，在一段时间之后，服务器可能会恢复正常;



---
#### 参考
http://tools.jb51.net/table/http_request_method
