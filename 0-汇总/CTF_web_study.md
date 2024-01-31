# CTF_web_study

## 一、信息获取

### （一）、文件读取

#### 1、目录扫描

目录扫描可以让我们发现这个网站存在多少个目录，多少个页面，探索出网站的整体结构。通过目录扫描我们还能扫描敏感文件，后台文件，数据库文件，和信息泄露文件，等等。

扫描的方式就是通过设置字典进行撞库匹配，探索网站的目录结构。字典需要靠平时积累，有时候会遇见一些骚气的目录，加进去就行。再就是要根据你所扫描的网站的特点构造专门的字典，所以**目录扫描的重点是字典的设置**

##### 工具

###### [御剑（两个）](https://blog.csdn.net/qq_45076423/article/details/103018509#:~:text=%E6%88%91%E4%BB%AC%E4%BD%BF%E7%94%A8%E5%BE%A1%E5%89%91%E6%89%AB%E6%8F%8F%E5%99%A8%EF%BC%8C%E4%B8%BB%E8%A6%81%E6%98%AF%E6%89%AB%E6%8F%8F%E7%BD%91%E7%AB%99%E6%95%8F%E6%84%9F%E7%9B%AE%E5%BD%95%EF%BC%8C%E5%8C%85%E6%8B%AC%E7%BD%91%E7%AB%99%E5%90%8E%E5%8F%B0%E7%AD%89%E3%80%82%20%E5%85%B6%E6%89%AB%E6%8F%8F%E5%8E%9F%E7%90%86%E4%B9%9F%E6%98%AF%E7%88%86%E7%A0%B4%EF%BC%8C%E5%8D%B3%E9%80%9A%E8%BF%87%E6%95%8F%E6%84%9F%E7%9B%AE%E5%BD%95%E7%9A%84%E5%AD%97%E5%85%B8%E5%8E%BB%E5%8C%B9%E9%85%8D%E3%80%82%20%E5%BE%A1%E5%89%91%E5%90%8E%E5%8F%B0%E6%89%AB%E6%8F%8F%E4%B9%8B%E5%89%8D%EF%BC%8C%E7%88%AC%E8%99%AB%E4%BC%9A%E8%AE%BF%E9%97%AErobots%20txt%E6%96%87%E4%BB%B6%E3%80%82,1%E3%80%81%E4%B8%8B%E8%BD%BD%E5%B9%B6%E8%A7%A3%E5%8E%8B%E6%89%93%E5%BC%80%E8%BD%AF%E4%BB%B6%202%E3%80%81%E6%89%93%E5%BC%80%E4%BB%A5%E5%90%8E%E5%9C%A8%E5%9F%9F%E5%90%8D%E8%BE%93%E5%85%A5%E6%A1%86%E4%B8%AD%E5%A1%AB%E5%85%A5%E8%A6%81%E6%89%AB%E6%8F%8F%E7%9A%84%E5%90%8E%E5%8F%B0%E5%9C%B0%E5%9D%80%203%E3%80%81%E5%9C%A8%E4%B8%8B%E9%9D%A2%E5%8F%AF%E4%BB%A5%E9%80%89%E6%8B%A9%E6%89%AB%E6%8F%8F%E7%BA%BF%E7%A8%8B%E4%BB%A5%E5%8F%8A%E6%89%AB%E6%8F%8F%E8%B6%85%E6%97%B6%E9%97%B4%EF%BC%8C%E8%BF%98%E6%9C%89%E6%96%87%E4%BB%B6%E7%B1%BB%E5%9E%8B%E7%AD%89%204%E3%80%81%E5%85%A8%E9%83%A8%E9%80%89%E6%8B%A9%E5%A5%BD%E4%BB%A5%E5%90%8E%E5%B0%B1%E5%8F%AF%E4%BB%A5%E7%82%B9%E5%87%BB%E5%BC%80%E5%A7%8B%E6%89%AB%E6%8F%8F%E4%BA%86%E3%80%82)

使用御剑扫描器，主要是扫描网站敏感目录，包括网站后台等。其扫描原理也是爆破，即通过敏感目录的字典去匹配。

御剑有好多版本，功能也稍微有些许区别，有指纹识别、后台扫描、获取真实IP、检测注入等

配置文件里面是字典，可以添加和删除。

![img](image/20200717155851578.png)

###### [dirsearch](https://blog.csdn.net/anquanzushiye/article/details/104151644)

dirsearch是一个扫描网站的目录和文件的命令行工具，推荐在kali中使用，可以使用多线程快速扫描目标站点。它可以通过自定义字典进行扫描，同时支持正则表达式和自定义扩展名。

个人觉得最好的目录扫描工具

使用教程：

在终端中运行以下命令，使用kali中的dirsearch扫描目标URL

```linux
dirsearch -u <URL>
```

例如：

```
dirsearch -u http://www.baidu.com
```

更多的参数选项

```
-e：指定要排除的扩展名
例如：排除.html和.php文件
dirsearch -u http://www.baidu.com -e html,php

-f：指定要包含的拓展名
例如：只包含.html和.php文件
dirsearch -u http://www.baidu.com -f html,php

-x：指定要排除的目录
例如：排除index.php目录
dirsearch -u http://www.baidu.com -x index.php

-t：指定线程数
例如：使用50线程进行扫描
dirsearch -u http://www.baidu.com -t 50

-o：保存结果到某文件
例如：保存结果到result.txt文件
dirsearch -u http://www.baidu.com -o result.txt

-w WORDLIST：使用自定义字典
例如：设置passwd.txt为字典进行扫描
dirsearch -u http://www.baidu.com -w passwd.txt
```

汇总：

| 后缀          | 介绍                             |
| ------------- | -------------------------------- |
| -h            | 查看帮助                         |
| -u URL        | 设置url                          |
| -L URLLIST    | 设置url列表                      |
| -e EXTENSIONS | 网站脚本类型                     |
| -w WORDLIST   | 设置字典                         |
| -f            | 强制扩展字典里的每个词条         |
| -s DELAY      | 设置请求之间的延时               |
| -r            | 递归地扫描                       |
| -t            | 设置扫描线程                     |
| -x            | 排除指定的网站状态码(用逗号隔开) |
| -c            | 设置cookie                       |
| -F            | 跟随地址重定向扫描               |
| -H            | 设置请求头                       |

###### **[postman](https://zhuanlan.zhihu.com/p/401385193)**

[关于目录扫描的使用](https://blog.csdn.net/cai_iac/article/details/81030619)即自动化接口测试

其原理就是构建js脚本进行批量发送请求，并利用js脚本进行对返回状态的分析

目前用的较少，总结一下就是会用的很厉害，不会就是不会

***

#### 2、[端口扫描](https://blog.csdn.net/qq_45555226/article/details/119420515)

一般在知道服务器开放了哪些端口后，就知道服务器开启了哪些服务，然后就可以通过所提供的这些服务的己知漏洞就可进行攻击。

原理：当一个主机向远端一个服务器的某一个端口提出建立一个连接的请求，如果对方有此项服务，就会应答，如果对方未安装此项服务时，即使你向相应的端口发出请求，对方仍无应答，利用这个原理，如果对所有熟知端口或自己选定的某个范围内的熟知端口分别建立连接，并记录下远端服务器所给予的应答，通过查看一记录就可以知道目标服务器上都安装了哪些服务。

##### 常见的端口服务:

| 端口             | 协议                                                         |
| ---------------- | ------------------------------------------------------------ |
| 21               | ftp                                                          |
| 22               | SSH                                                          |
| 23               | Telnet                                                       |
| 80               | web                                                          |
| 80-89            | web                                                          |
| 161              | SNMP                                                         |
| 389              | LDAP                                                         |
| 443              | SSL心脏滴血以及一些web漏洞测试                               |
| 445              | SMB                                                          |
| 512，513，513    | Rexec                                                        |
| 873              | Rsync未授权                                                  |
| 1025，111        | NFS                                                          |
| 1433             | MSSQL                                                        |
| 1521             | Oracle:(iSqlPlus Port:5560,7778)                             |
| 2082/2083        | cpanel主机管理系统登陆 （国外用较多）                        |
| 2222             | DA虚拟主机管理系统登陆 （国外用较多）                        |
| 2601，2604       | zebra路由，默认密码zebra                                     |
| 3128             | squid代理默认端口，如果没设置口令很可能就直接漫游内网了      |
| 3306             | MySQL                                                        |
| 3311/3312        | kangle主机管理系统登陆                                       |
| 3389             | 远程桌面                                                     |
| 4440             | rundeck 参考WooYun: 借用新浪某服务成功漫游新浪内网           |
| 5432             | PostgreSQL                                                   |
| 5900             | vnc                                                          |
| 5984             | CouchDB http://xxx:5984/_utils/                              |
| 6082             | varnish 参考WooYun: Varnish HTTP accelerator CLI 未授权<br />访问易导致网站被直接篡改或者作为代理进入内网 |
| 6379             | redis未授权                                                  |
| 7001，7002       | WebLogic默认弱口令，反序列                                   |
| 7778             | Kloxo主机控制面板登录                                        |
| 8000-9090        | 都是一些常见的web端口，有些运维喜欢把管理后台开在<br />这些非80的端口上 |
| 8080             | tomcat/WDCP主机管理系统，默认弱口令                          |
| 8080，8089，9090 | JBOSS                                                        |
| 8083             | Vestacp主机管理系统 （国外用较多）                           |
| 8649             | ganglia                                                      |
| 8888             | amh/LuManager 主机管理系统默认端口                           |
| 9200，9300       | elasticsearch 参考WooYun: 多玩某服务器ElasticSearch命令执行漏洞 |
| 10000            | Virtualmin/Webmin 服务器虚拟主机管理系统                     |
| 11211            | memcache未授权访问                                           |
| 27017，27018     | Mongodb未授权访问                                            |
| 28017            | mongodb统计页面                                              |
| 50000            | SAP命令执行                                                  |
| 50070，50030     | hadoop默认端口未授权访问                                     |



##### 工具

[御剑（端口扫描）](#御剑（两个）)

###### [nmap](https://blog.csdn.net/smli_ng/article/details/105964486)

nmap是一款非常强大的主机发现和端口扫描工具，而且nmap运用自带的脚本，还能完成漏洞检测，同时支持多平台。**一般用来攻击靶机**

**常用命令：**

| **主机发现**           |                                            |
| ---------------------- | ------------------------------------------ |
| iR                     | 随机选择目标                               |
| -iL                    | 从文件中加载IP地址                         |
| -sL                    | 简单的扫描目标                             |
| -sn                    | Ping扫描-禁用端口扫描                      |
| -Pn                    | 将所有主机视为在在线，跳过主机发现         |
| -PS[portlist]          | （TCP SYN ping） 需要root权限              |
| -PA[portlist]          | （TCP ACK ping）                           |
| -PU[portlist]          | （UDP ping）                               |
| -PY [portlist]         | （SCTP ping）                              |
| -PE/PP/PM              | ICMP回显，时间戳和网络掩码请求探测         |
| -PO[协议列表]          | IP协议Ping                                 |
| -n/-R                  | 从不执行DNS解析/始终解析[默认：有时]       |
| --dns-servers          | 指定自定义DNS服务器                        |
| --system-dns           | 使用OS的dns服务器                          |
| --traceroute           | 跟踪到每个主机的跃点路径                   |
| **扫描技术**           |                                            |
| -sS                    | 使用TCP的SYN进行扫描                       |
| -sT                    | 使用TCP进行扫描                            |
| -sA                    | 使用TCP的ACK进行扫描                       |
| -sU                    | UDP扫描                                    |
| -sI                    | Idle扫描                                   |
| -sF                    | FIN扫描                                    |
| -b<FTP中继主机>        | FTP反弹扫描                                |
| **端口规格和扫描顺序** |                                            |
| -p                     | 扫描指定端口                               |
| --exclude-ports        | 从扫描中排除指定端口                       |
| -f                     | 快速模式-扫描比默认扫描更少的端口          |
| -r                     | 连续扫描端口-不随机化                      |
| --top-ports            | 扫描<number>最常用的端口                   |
| **服务/版本探测**      |                                            |
| -sV                    | 探测服务/版本信息                          |
| --version-intensity    | 设置版本扫描强度（0-9）                    |
| --version-all          | 尝试每个强度探测                           |
| --version-trace        | 显示详细的版本扫描活动（用于调试）         |
| **操作系统扫描**       |                                            |
| -o                     | 启用os检测                                 |
| **输出**               |                                            |
| -oN                    | 标准输出                                   |
| -v                     | 信息详细级别                               |
| -oA                    | 同时输出三种主要格式                       |
| **杂项**               |                                            |
| -6                     | 启动Ipv6扫描                               |
| -A                     | 启动Os检测，版本检测，脚本扫描和traceroute |
| -V                     | 显示版本号                                 |
| -h                     | 帮助信息                                   |

***

#### 3、[路径穿梭](https://blog.csdn.net/angry_program/article/details/107855078)

- Nginx访问根目录

#### 4、敏感信息

- phpinfo

  - 了解关键变量的位置和作用

- robots.txt

  - 反爬虫文件

- 等

#### 5、源码泄露

- 网站备份文件

  - *.php.bak

  - *.php~

- 测试文件

  - tset.php

- git svn等

  - Githack

  - dvcs-ripper

- index.phps

- vim遗留文件

  - swp

  - swo

  - swm

#### 6、容器相关

- IIS短文件漏洞

#### 7、利用PHP进行文件读取

- 函数

  - scandir

  - showsource

  - readfile

  - system

    - nl

    - cat

    - system("find / -name "*flag"")

- 伪协议

### （二）、容器、框架、组件、语言等

#### 1、Wappalyzer

#### 2、JavaScript Object.getOwnPropertyNames()

## 命令执行

### 运用分隔符&或| 若无严格过滤可出现任意漏洞执行漏洞

### 反弹shell的方式

### %0A参数污染

### 过滤与bypass

- linux中{IFS}可以代替空格等

## 文件上传

### 前端绕过

- 修改网页代码

### 后端染过

- 修改MIME文件类型（Content-Type）

- 修改文件内容

  - eg：

<script language='php'>phpinfo();</script>

可用来绕过对<?php的过滤

- 修改文件头

  - GIF89a等

- 0x00绕过（截断）

- 解析漏洞

  - IIS5.x-6.x

    - 默认将asp、asa目录下的文件解析成asp文件

    - 不解析分号（；）后面的内容

    - 其他的可执行文件

      - asa

      - cer

      - cdx

  - IIS 7.0/IIS 7.5/Nginx<8.03畸形解析漏洞

  - Nginx<8.03空字节代码执行漏洞

    - 在图片中嵌入PHP代码，然后通过访问xxx.php%00jpg来执行其中的代码

  - Apache

    - 从右向左解析知道解析到认识的扩展名为止

- 上传目录修改

  - POST时的filepath字段

  - 文件本身的名字

  - ······

### 黑白名单绕过

- 大小写混合

- 双写绕过

- 特殊后缀

  - 与PHP等价的后缀：php3、php5、php7、pht、phtml等

### 配合文件包含漏洞

### CMS和编辑器漏洞

### .htaccess的利用

## 数据库相关

### SQL注入

- 过滤与bypass

  - 过滤逗号

    - join

    - limit

  - 过滤空格

    - （）

    - +

    - %0A

  - 过滤不等号

    - <>

  - 过滤limit

    - offset

  - database,table,information这些都过滤了

    - 利用Mysql自带的空间索引函数

  - 过滤select

    - 拼接构造该关键字

  - 语句固定为 order by *结尾

    - 用if进行布尔盲注

  - 添加垃圾信息

    - UNION/**/SELECT

    - /*!UNION*/ /*!SELECT*/

- 普通注入

  - 盲注

    - 时间盲注

    - 布尔盲注

  - 联合查询注入

  - 显错注入

  - 二次注入

  - HTTP头注入

    - XFF

    - Cookie

    - Referer

  - 宽字节注入

  - 万能密码

  - 堆叠注入

- 非常规注入

  - upload、insert语句

    - 盲注

  - 构造数据绕过验证

  - 异或注入

  - 利用截断

  - 脑洞注入

    - 上传的文件名

### MySQL服务器端恶意读取客户端文件漏洞

### Redis 4.x CVE

- 主从复制写shell

- Redis结合SSRF

  - SSRF

    - hash长度拓展攻击

      - HashPump

    - PHP SOAP

## 不常见考点

### 逻辑漏洞

- 用户名和密码分开验证

- 下单和扣款的先后顺序

### 并发漏洞（条件竞争）

### CSRF

### Clickjacking

### XXE漏洞

### XSCH

- crossdomain.xml的错误配置

### HEREDOC

### JSPFUCK

### web Assembly

## 越权漏洞

### 纵向

### 横向

- 改密码

## 代码审计

### XSS

- print()

- printr()

- echo

- printf()

- sprintf()

- die()

- var_dump()

- var_export()

### 代码执行

- 函数

  - eval()

  - assert()

  - preg_repace()

  - create_function()

  - array_map()

  - call_user_func()

  - call_user_func_array()

  - array_filter()

  - usort()

  - uasort()

- 过滤与bypass

  - 利用各种函数的返回值进行拼接

  - 利用^符号进行异或出想要的东西

  - 利用等价表达式

    - _

      - 空格

      - .

### 文件包含

- include()

- include_once()

- require()

- require_once()

### 文件读取（下载）

- file_get_contents()

- highlight_file()

- fopen()

- readfile()

- fread()

- fgetss()

- fgets()

- parse_ini_file()

- show_source()

- file()

### 命令执行

- system()

- shell_exec()（反引号也可代替）

- passthru()

- pcntl_exec()

- popen()

- proc_open()

### 文件上传

- move_uoloaded_file()

### 文件删除

- unlink()

- session_destroy()(老版本)

### 变量覆盖

- extract()

- parse_str

  - 没有第二个参数会引起变量覆盖

- import_request_variables()

- for each($_GET as $key=>$value) ${$key}=$value

### 弱类型比较

- ==、===、!==、!=

  - md5，sha1的==绕过

- is_numeric

  - 16进制编码绕过

- in_array

### PHP黑魔法

- md5

  - 绕过sql，md5(ffifdyop,32)=276f722736c95d99e921722cf9ed621c
    转成字符串为or'6xxx

- eval

  - 可使用分号构造出多条语句

- ereg

  - 存在%00截断

- strcmp

  - 无法处理数组并将return 0

- ascii

  - 传进去的是字符串只会截取第一个字符进行处理

- curl_setopt

  - 存在可能的SSRF

- preg_replace

  - 第二个参数使用/e模式导致代码执行

- URL decode

  - url二次编码绕过

- include

- open_basedir

  - 可绕过并进行任意文件读取

- in_array()

  - 第三个参数如果设置为FALSE,就存在注入点

- spl_get_contents

  - 配合文件上传可以getshell

- create_function()

  - 代码注入

- file_get_contents

  - 常用的伪协议绕过

- mt_rand

  - SEED相关的安全性问题

- sprintf

  - 格式化字符串漏洞

- parse_url

  - 可用于绕过某些过滤

- 几乎所有的字符串相关函数都不能处理数组，此时会返回NULL，可以用于绕过

  - ereg

  - ND5

  - sha1

  - strpos

- _wakeup

  - 反序列化时，如果表示对象属性个数的值大于真实的属性个数是就会跳过——WAKEUP()的执行

### 反序列化漏洞

- 对各种魔法函数的理解

  - _wakeup() //使用unserialize时触发

  - _sleep() //使用serialize时触发

  - _destruct() //对象被摧毁时触发

  - _construct() //对象创建时自动调用

  - _call() //在对象上下文中调用不可访问的方式时触发

  - _callStatic() //在静态的上下文中调用不可访问的方法时触发

  - _get() //用于从不可访问的属性读取数据

  - _set() //用于将数据写入不可访问的属性

  - _isset() //在不可访问的属性上调用isset()或empty（）触发

  - _unset() //在不可访问的属性上使用unset()时触发

  - _toString() //把类当作字符串使用时触发

  - _invoke() //当脚本尝试将对象调用为函数时触发

- pop链的构造

  - 寻找位点

  - 正面构造

  - 反省推理

- phar与反序列化

### 变量特性

- ignore_user_abort

  - 并发漏洞

- $_SERVER['QUERY_STRING']

  - 不会像$_GET一样进行urldecode

- disable_functions

  - 使用LD_PRELOAD进行绕过

### 未exit(),return()引发的相关问题

### 伪静态绕过

## LFI&RFI

### 问号截断

### 注意URL中pash、dir、file、pag、page、archive、p、eng、语言文件等相关关键字眼

## XSS

### CSP及其bypass

## 容器漏洞

### Nginx配置漏洞

### IIS PUT上传漏洞

### IIS 远程溢出漏洞

### Apache HTTP组件提权漏洞

### CGI 漏洞

## 基础考察

### HTTP头

- Referer

- X-Forwarded-For

- User-Agent

- Cookie

  - JWT

### HTTP内容

- 价格、金钱、数量，打折等

### URL参数

### HTTP响应码

- 302中的信息

### 检查网页源代码

### 审查元素（F12）

## 常见框架(PHP)&SSTI

### 初步筛查

- tplmap

### 常见的框架的漏洞

- Twig

- Laravel

- Thinkphp

  - 经典CVE

    - Thinkphp 5.0~5.0.23 RCE

    - Thinkphp5 5.0.22/5.1.29 远程代码执行漏洞

- Smarty

## 非PHP专题

### ASP

- ASP.NET VIEWSTATE反序列化

- web.config利用

### JAVA WEB

- Struts2框架漏洞

- Spring框架漏洞

- 反序列化漏洞

  - Hessian

  - 二进制（ObjectOutputStream）

  - JSON

  - XML

  - YAML

- JRMP安全性问题

### JavaScript框架

- SSJI (服务端JavaScript注入)

  - Node.js

  - Vue.js

### Python

- 沙箱逃逸

  - 利用内建函数执行命令

    - 也可以是命令执行的考点

  - 过滤与bypass

- 各种框架的漏洞

  - Flask

    - SESSION

      - 敏感信息泄露

      - 验证码绕过

      - SESSION伪造和对象注入漏洞

        - Codeigniter

      - 使用hash而非hmac进行签名

        - Hash长度拓展攻击

      - 任意文件读取

      - CBC字节翻转攻击

  - Tornado

  - Django

- CRLF

  - 反序列化漏洞

    - pickle模块

