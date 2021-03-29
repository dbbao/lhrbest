
# 一、巡检脚本简介

![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170658.png)

> * 目前一共包含**8**个脚本，若脚本的扩展名为“.sql”则表示该脚本为sql脚本，若脚本的扩展名为“.pl”则表示该脚本为perl脚本。
> * 对于Oracle的SQL脚本而言，脚本DB_Oracle_HC_lhr_v7.0.0_10g.sql适用于Oracle 10g数据库，脚本DB_Oracle_HC_lhr_v7.0.0_11g.sql适用于Oracle 11g的数据库，脚本DB_Oracle_HC_lhr_v7.0.0_12c.sql适用于Oracle 12c及其以上版本，这3个脚本都是**只读**版本，这3个脚本只会对数据库做查询操作，不会做DML和DDL操作，这也是很多朋友所期待的功能。
> * 脚本DB_OS_HC_lhr_v7.0.0.pl是perl脚本，执行后会对OS的信息进行收集，并且输出到html中。
> * 脚本DB_MySQL_HC_lhr_v7.0.0.sql是MySQL脚本，执行后会产生MySQL的健康检查html报告，该脚本为**只读**脚本。
> * 脚本DB_MSSQL_HC_lhr_v7.0.0_2005.sql和DB_MSSQL_HC_lhr_v7.0.0_2008R2.sql是SQL Server脚本，存在部分DDL和DML操作，执行后会产生SQL Server的健康检查html报告。脚本DB_MSSQL_HC_lhr_v7.0.0_2005.sql最低支持2005版本，而脚本DB_MSSQL_HC_lhr_v7.0.0_2008R2.sql最低支持2008R2版本。
> * 脚本DB_PG_HC_lhr_v7.0.0.sql是PG脚本，执行后会产生PostgreSQL数据库的健康检查html报告。

# 二、巡检脚本特点

>1、可以巡检Oracle、MySQL、SQL Server和PG数据库，也可以巡检Linux操作系统  
>2、脚本为绿色版、免安装、纯SQL文本  
>3、跨平台，只要有SQL*Plus、mysql、MSSQL客户端（SSMS、Navicat皆可）、psql环境即可运行脚本  
>4、脚本内容可视化，可以看到脚本内容，因此可供学习数据库使用  
>5、兼容Oracle 10g、11g、12c、18c、19c、20c、21c等高版本Oracle数据库  
>6、对Oracle 10g、11g、12c、18c、19c、20c、21c等版本分别提供了只读版（只对数据库查询，不做DDL和DML操作）  
>7、MySQL最低支持5.5版本  
>8、SQL Server最低支持2005版本  
>9、增删监控项非常方便，只需要提供相关SQL即可  
>10、一次购买，所有脚本终身免费升级  
>11、检查内容非常全面  
>12、只有1个SQL脚本，不存在嵌套调用脚本等其它问题  
>13、最终生成html文件格式的健康检查结果  
>14、对结果进行过滤，列出了数据库有问题的内容  
>15、对OS的信息提供了收集（单独脚本）  

# 三、巡检结果展示

这里只列出部分结果，其它的详细内容可以参考：https://share.weiyun.com/5lb2U2M

## 1、Oracle数据库

![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170734.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170741.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170749.png)

鼠标经过相关连接时会有相应的解释，如下图所示：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170812.jpeg)

该脚本检查的内容较多，所以我对结果进行了过滤，如下：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170819.jpeg)

点击链接即可查看结果：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170824.jpeg)

数据库基本信息一目了然：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170831.jpeg)

## 2、MySQL数据库
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170838.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170842.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170845.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170851.jpeg)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170855.png)

其它不再列举。

## 3、SQL Server数据库
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170900.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170908.jpeg)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170917.png)
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170924.jpeg)

其它不再列举。

## 4、PG数据库
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170929.png)



## 5、OS信息
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170937.jpeg)



# 四、脚本运行方式

## 1、Oracle数据库

只要有sqlplus的客户端即可。

服务器端直接运行：

```sql
sqlplus / as sysdba @DB_Oracle_HC_lhr_v7.0.0_12c.sql
```

sqlplus客户端运行：

```sql
sqlplus sys/lhr@192.168.59.130:1521/orcl as sysdba @DB_Oracle_HC_lhr_v7.0.0_12c.sql
```

## 2、MySQL数据库

首先将DB_MySQL_HC_lhr_v7.0.0.sql和pt-summary这2个脚本拷贝到有mysql客户端的Linux环境中，然后执行如下命令：

```sql
mysql -h192.168.1.63 -uroot -plhr -P3306 --html -t  -f --silent  <  DB_MySQL_HC_lhr_v7.0.0.sql
```

> 注意：
>
> 1、由于Windows下没有system命令，所以该脚本目前只能在Linux平台运行。对于Windows下的MySQL数据库，可以使用Linux平台的客户端连接到windows的服务器下进行生成报告（后期可能进行优化）。
>
> 2、客户端不要使用MariaDB的客户端，否则产生的html报告没有数据：
>
> ![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170945.jpeg)
>
> 3、客户端最低版本为5.5，否则产生的html报告没有数据。

## 3、SQL Server数据库

需要使用SQL Server Management Studio (SSMS)或Navicat for SQLServer客户端软件，直接运行脚本，然后将输出结果保存为html文件即可。

脚本DB_MSSQL_HC_lhr_v7.0.0_2005.sql和DB_MSSQL_HC_lhr_v7.0.0_2008R2.sql是SQL Server脚本，存在部分DDL和DML操作，执行后会产生SQL Server的健康检查html报告。脚本DB_MSSQL_HC_lhr_v7.0.0_2005.sql最低支持2005版本，而脚本DB_MSSQL_HC_lhr_v7.0.0_2008R2.sql最低支持2008R2版本。

![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170949.png)



## 4、PG数据库

需要有psql客户端，运行方式如下：

```sql
psql -U postgres -h 192.168.66.35 -p 54324 -d postgres -W -H -f D:\DB_PG_HC_lhr_v7.0.0.sql > d:\a.html
```

输入密码，回车即可。

> 注意：
>
> 1、该脚本的字符集为utf8，请使用utf8格式打开该文件。

## 5、OS信息

操作系统信息的收集是perl脚本，运行方式如下所示。

```sql
[root@OCPLHR lhr]# ll
total 28
-rw-r--r-- 1 oracle oinstall 25791 Jul 10 17:15 DB_OS_HC_lhr_v7.0.0.pl
[root@OCPLHR lhr]# perl DB_OS_HC_lhr_v7.0.0.pl 
[root@OCPLHR lhr]# ll
total 56
-rw-r--r-- 1 oracle oinstall 25791 Jul 10 17:15 DB_OS_HC_lhr_v7.0.0.pl
-rw-r--r-- 1 root   root     26289 Jul 10 17:19 LHR_OSCHECK_REPORT_OCPLHR_20190710171939.html
[root@OCPLHR lhr]# 
```



# 五、其它问题

请看视频《小麦苗数据库健康检查脚本使用说明.wmv》或阅读《【DB健康巡检（Oracle+MySQL+MSSQL+OS）】小麦苗巡检脚本使用说明_LHR.pdf》，下载地址为：https://share.weiyun.com/5lb2U2M 。

视频观看地址：https://v.qq.com/x/page/m3007wsp4o7.html



# 六、软件著作权登记证书

小麦苗编写的该巡检系统已申请“**中华人民共和国国家版权局计算机软件著作权登记证书**”，请购买的朋友不要随意传播，否则将追究法律责任，谢谢。

相关证书见下图：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201170955.png)

# 七、购买方式

目前售价**99**元，包括Oracle+MySQL+SQL Server+OS+PG的脚本，**后续免费优化，加量不加价**，支持以下购买方式：

1、微信红包，请加我微信：db_bao，或用微信扫描以下二维码加麦老师微信：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201171006.png)

2、QQ红包，请加我QQ：646634621，或用QQ扫以下二维码加我QQ：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201171010.png)

 

3、微店购买连接：https://k.weidian.com/o5iECboc  

我的微店的二维码如下所示：
![](https://gitee.com/lhrbest/pic/raw/master/img/20210201171024.png)





**About Me**

***
> ● 本文作者：小麦苗，部分内容整理自网络，若有侵权请联系小麦苗删除
> ● 本文在个人微 信公众号（[DB宝](https://mp.weixin.qq.com/s/36ahcv7o8u67NcxGSGO5WQ)）上有同步更新
> ● QQ群号： 230161599 、618766405，微信群私聊
> ● 个人QQ号（646634621），微 信号（db_bao），注明添加缘由
> ● 于 2021年2月 在西安完成
> ● 最新修改时间：2021年2月
> ● 版权所有，欢迎分享本文，转载请保留出处
> ***
> ●小麦苗的微店： [https://weidian.com/?userid=793741433](https://weidian.com/?userid=793741433)
> ●小麦苗出版的数据库类丛书： [http://blog.itpub.net/26736162/viewspace-2142121/](http://blog.itpub.net/26736162/viewspace-2142121/)
> ●小麦苗OCP、OCM、高可用、DBA学习班（Oracle、MySQL、NoSQL）： [http://blog.itpub.net/26736162/viewspace-2148098/](http://blog.itpub.net/26736162/viewspace-2148098/)
> ●数据库笔试面试题库及解答： [https://mp.weixin.qq.com/s/Vm5PqNcDcITkOr9cQg6T7w](https://mp.weixin.qq.com/s/Vm5PqNcDcITkOr9cQg6T7w)
>
> ***
> 使用微信客户端扫描下面的二维码来关注小麦苗的微信公众号（[DB宝](https://mp.weixin.qq.com/s/Vm5PqNcDcITkOr9cQg6T7w)）及QQ群（DBA宝典）、添加小麦苗微信， 学习最实用的数据库技术。
> ![](https://gitee.com/lhrbest/pic/raw/master/img/20210201171033.png)
>
> ***
