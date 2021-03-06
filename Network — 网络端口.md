## 网络端口
- #### 解除端口占用
  ```
  // windows 中查看端口占用情况
  netstat -ano

  // 通过 PID 继续查看占用端口的具体程序信息
  tasklist | findstr "{PID}"

  // 通过 PID 可以解除该进程对端口的占用
  tskill {PID}
  ```



- #### 各种通信协议的默认端口
  协议 | 默认端口
  -|-
  HTTP | 80
  HTTPS | 443
  FTP | 21
  SSH | 22
  Telnet| 23
  SMTP | 25
  POP3 | 110
  SQLServer | 1433
  Oracle | 1521
  MySQL | 3306
  Windows 远程登陆 | 3389
  Tomcat / JBoss | 8080



- #### 系统端口的 3 大类
  ##### （1）公认端口（Well Known Ports）：0 — 1023。它们紧密绑定（binding）于一些服务。通常这些端口的通讯明确表明了某种服务的协议。例如：80端口实际上总是HTTP通讯。一般不在这个范围内注册私有服务。
  ##### （2）注册端口（Registered Ports）：1024 — 49151。它们松散地绑定于一些服务。也就是说有许多服务绑定于这些端口，这些端口同样用于许多其它目的。例如：许多系统处理动态端口从1024左右开始。
  ##### （3）动态和/或私有端口（Dynamic and/or Private Ports）：49152 — 65535。理论上，不应为服务分配这些端口。实际上，机器通常从1024起分配动态端口。但也有例外：SUN的RPC端口从32768开始。
