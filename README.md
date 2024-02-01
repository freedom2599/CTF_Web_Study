# WEB

## 信息收集

### 基础信息

- HTTP头

	- Referer

	- X-Forwarded-For

	- User-Agent

	- Cookie

		- JWT

- HTTP内容

	- 价格、金钱、数量，打折等

- URL参数

- HTTP响应码

	- 302中的信息

- 审查元素（F12）

- 检查网页源代码

### 文件读取

- 目录扫描

	- 御剑（两个）

		- [御剑的使用](https://blog.csdn.net/qq_45076423/article/details/103018509#:~:text=%E6%88%91%E4%BB%AC%E4%BD%BF%E7%94%A8%E5%BE%A1%E5%89%91%E6%89%AB%E6%8F%8F%E5%99%A8%EF%BC%8C%E4%B8%BB%E8%A6%81%E6%98%AF%E6%89%AB%E6%8F%8F%E7%BD%91%E7%AB%99%E6%95%8F%E6%84%9F%E7%9B%AE%E5%BD%95%EF%BC%8C%E5%8C%85%E6%8B%AC%E7%BD%91%E7%AB%99%E5%90%8E%E5%8F%B0%E7%AD%89%E3%80%82%20%E5%85%B6%E6%89%AB%E6%8F%8F%E5%8E%9F%E7%90%86%E4%B9%9F%E6%98%AF%E7%88%86%E7%A0%B4%EF%BC%8C%E5%8D%B3%E9%80%9A%E8%BF%87%E6%95%8F%E6%84%9F%E7%9B%AE%E5%BD%95%E7%9A%84%E5%AD%97%E5%85%B8%E5%8E%BB%E5%8C%B9%E9%85%8D%E3%80%82%20%E5%BE%A1%E5%89%91%E5%90%8E%E5%8F%B0%E6%89%AB%E6%8F%8F%E4%B9%8B%E5%89%8D%EF%BC%8C%E7%88%AC%E8%99%AB%E4%BC%9A%E8%AE%BF%E9%97%AErobots%20txt%E6%96%87%E4%BB%B6%E3%80%82,1%E3%80%81%E4%B8%8B%E8%BD%BD%E5%B9%B6%E8%A7%A3%E5%8E%8B%E6%89%93%E5%BC%80%E8%BD%AF%E4%BB%B6%202%E3%80%81%E6%89%93%E5%BC%80%E4%BB%A5%E5%90%8E%E5%9C%A8%E5%9F%9F%E5%90%8D%E8%BE%93%E5%85%A5%E6%A1%86%E4%B8%AD%E5%A1%AB%E5%85%A5%E8%A6%81%E6%89%AB%E6%8F%8F%E7%9A%84%E5%90%8E%E5%8F%B0%E5%9C%B0%E5%9D%80%203%E3%80%81%E5%9C%A8%E4%B8%8B%E9%9D%A2%E5%8F%AF%E4%BB%A5%E9%80%89%E6%8B%A9%E6%89%AB%E6%8F%8F%E7%BA%BF%E7%A8%8B%E4%BB%A5%E5%8F%8A%E6%89%AB%E6%8F%8F%E8%B6%85%E6%97%B6%E9%97%B4%EF%BC%8C%E8%BF%98%E6%9C%89%E6%96%87%E4%BB%B6%E7%B1%BB%E5%9E%8B%E7%AD%89%204%E3%80%81%E5%85%A8%E9%83%A8%E9%80%89%E6%8B%A9%E5%A5%BD%E4%BB%A5%E5%90%8E%E5%B0%B1%E5%8F%AF%E4%BB%A5%E7%82%B9%E5%87%BB%E5%BC%80%E5%A7%8B%E6%89%AB%E6%8F%8F%E4%BA%86%E3%80%82)

	- dirsearch

		- [使用方法](https://blog.csdn.net/anquanzushiye/article/details/104151644)

	- postman

		- [安装使用](https://zhuanlan.zhihu.com/p/401385193)

		- [对于目录扫描的使用](https://blog.csdn.net/cai_iac/article/details/81030619)

- 敏感信息

	- phpinfo

		- 了解关键变量的位置和作用

	- robots.txt

		- 反爬虫文件

	- 等

- 源码泄露

	- 备份文件下载

		- *.php.bak

		- *.php~

		- .DS_Store

	- 测试文件

		- tset.php

	- Git泄露

		- Githack

		- log

		- Stash

		- Index

		- dvcs-ripper

	- SVN泄露

	- HG泄露

	- vim遗留文件

		- swp

		- swo

		- swm

- 利用PHP进行文件读取

	- 函数

		- scandir

		- showsource

		- readfile

		- system

			- nl

			- cat

			- system("find / -name "*flag"")

	- 伪协议

## XSS漏洞

### CSP及其bypass

### 代码审计

- print()

- printr()

- echo

- printf()

- sprintf()

- die()

- var_dump()

- var_export()

## PHP特性

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

### 弱类型比较

- ==、===、!==、!=

	- md5，sha1的==绕过

- is_numeric

	- 16进制编码绕过

- in_array

## 文件上传漏洞

### 前端绕过

- 修改网页代码

### 后端绕过

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

### 代码审计

- move_uoloaded_file()

## 文件包含漏洞

### 代码审计

- include()

- include_once()

- require()

- require_once()

## 文件读取漏洞

### [路径穿梭](https://blog.csdn.net/angry_program/category_9990662.html)

### 代码审计

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

## 命令执行漏洞

### 运用分隔符&或| 若无严格过滤可出现任意漏洞执行漏洞

### 反弹shell的方式

### %0A参数污染

### 过滤与bypass

- linux中{IFS}可以代替空格等

### 代码审计

- 代码执行

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

- 命令执行

	- system()

	- shell_exec()（反引号也可代替）

	- passthru()

	- pcntl_exec()

	- popen()

	- proc_open()

## SQL注入

### 过滤与bypass

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

### 普通注入

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

### 非常规注入

- upload、insert语句

	- 盲注

- 构造数据绕过验证

- 异或注入

- 利用截断

- 脑洞注入

	- 上传的文件名

### 数据库相关

- MySQL服务器端恶意读取客户端文件漏洞

- Redis 4.x CVE

	- 主从复制写shell

	- Redis结合SSRF

		- SSRF

			- hash长度拓展攻击

				- HashPump

			- PHP SOAP

## 反序列化漏洞

### PHP反序列化漏洞

- 对各种魔法函数的理解

	- _wakeup() //使用unserialize时触发

		- 反序列化时，如果表示对象属性个数的值大于真实的属性个数是就会跳过——WAKEUP()的执行

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

### ASP.NET VIEWSTATE反序列化

### JAVA WEB反序列化漏洞

- Hessian

- 二进制（ObjectOutputStream）

- JSON

- XML

- YAML

### python反序列化漏洞

- pickle模块

- CRLF

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

## 模板注入漏洞

## 其他考点

### 非PHP专题

- ASP

	- web.config利用

- JAVA WEB

	- Struts2框架漏洞

	- Spring框架漏洞

	- JRMP安全性问题

- JavaScript框架

	- SSJI (服务端JavaScript注入)

		- Node.js

		- Vue.js

- Python

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

### 容器漏洞

- 容器、框架、组件、语言等

	- Wappalyzer

	- IIS短文件漏洞

	- JavaScript Object.getOwnPropertyNames()

- Nginx配置漏洞

- IIS PUT上传漏洞

- IIS 远程溢出漏洞

- Apache HTTP组件提权漏洞

- CGI 漏洞

### LFI&RFI

- 问号截断

- 注意URL中pash、dir、file、pag、page、archive、p、eng、语言文件等相关关键字眼

### 越权漏洞

- 纵向

- 横向

	- 改密码

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

## 代码审计

### 文件删除

- unlink()

- session_destroy()(老版本)

### 变量覆盖

- extract()

- parse_str

	- 没有第二个参数会引起变量覆盖

- import_request_variables()

- for each($_GET as $key=>$value) ${$key}=$value

### 变量特性

- ignore_user_abort

	- 并发漏洞

- $_SERVER['QUERY_STRING']

	- 不会像$_GET一样进行urldecode

- disable_functions

	- 使用LD_PRELOAD进行绕过

### 未exit(),return()引发的相关问题

### 伪静态绕过

## WEB攻防

### [端口扫描](https://blog.csdn.net/qq_45555226/article/details/119420515)

- nmap

	- [使用方法](https://blog.csdn.net/smli_ng/article/details/105964486)

