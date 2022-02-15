@[TOC](攻防世界 新手区 WEB)

# view source

查看一个网页的源代码，但小宁同学发现鼠标右键好像不管用了,那就F12吧！
![在这里插入图片描述](https://img-blog.csdnimg.cn/d581dfc490c74f218621482bf09c8b16.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

或者 ···→更多工具→开发人员工具→元素。
# robots

X老师上课讲了Robots协议，小宁同学却上课打了瞌睡，赶紧来教教小宁Robots协议是什么吧。
题目提示明显，但究竟什么是Robots协议？度娘一下吧！
![在这里插入图片描述](https://img-blog.csdnimg.cn/869f0ab6c8d74807aaf0ed983498cae6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

>Robots协议用来告知搜索引擎哪些页面能被抓取，哪些页面不能被抓取；可以屏蔽一些网站中比较大的文件，如：图片，音乐，视频等，节省服务器带宽；可以屏蔽站点的一些死链接。方便搜索引擎抓取网站内容；设置网站地图连接，方便引导蜘蛛爬取页面。
将Robots.txt转填图下内容，flag出现。

![在这里插入图片描述](https://img-blog.csdnimg.cn/9889bd7e8abb435fa65283b6e0fcc0a2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

# ​​​​backup

他派小宁同学去把备份文件找出来?那么什么是备份文件呐？ 放出提示了！
![在这里插入图片描述](https://img-blog.csdnimg.cn/57eae7838bcf42ddb57fa0e5679deb71.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

改成index.php.bak吧！然后就会得到一个文件。
![在这里插入图片描述](https://img-blog.csdnimg.cn/76964899980a40a6bc8f5ac0fbe6fcc1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

 记得把后缀.bak删去哦！

​
# cookie

​
X老师告诉小宁他在cookie里放了些东西,这句话，一定有用。先来度娘一下！什么是cookie？从而对于cookie有一定的了解！
>由此可得Cookie 并不是它的原意“甜饼”的意思, 而是一个保存在客户机中的简单的文本文件, 这个文件与特定的 Web 文档关联在一起, 保存了该客户机访问这个Web 文档时的信息, 当客户机再次访问这个 Web 文档时这些信息可供该文档使用。由于“Cookie”具有可以保存在客户机上的神奇特性, 因此它可以帮助我们实现记录用户个人信息的功能。

 在本学期计算机导论也有相关的表述（学好每一门都很重要）：我们经常使用浏览器，也会访问一些网站，这个网站有在你计算机内记录数据(称为cookie)的能力，从而了解到你曾经访问过该网站。然后这些cookie可被用来识别再次浏览的人并记录这些人以前的活动，以便以后更高效地处理这些人的访问（比如推荐常看的内容）。计算机上的cookie还可提供你访问网站的记录。

目前而言：主要为学习阶段，对与问题的解决，尝试解题的方法重在多样！
## 扩展
在网站，借助Google浏览器（网上是这么说的，其他浏览器也不知道行不行!我这没有其他浏览器）和EditThisCookie来解题：
首先要在扩展里添加一个EditThisCookie。利用EditThisCookie来查找Cookie值是cookie.php。
![在这里插入图片描述](https://img-blog.csdnimg.cn/acdc8f57d11f4ba1a364cf1d065a5395.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

接下来访问他！
![在这里插入图片描述](https://img-blog.csdnimg.cn/db664f9f665c4c5389682f486a6fd234.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
通过开发者工具（快捷方式F12也行，我的电脑不支持），在网络中找到cookie.php（没有就按照他的提示刷新一下），点击它，在标头中可得flag！
![在这里插入图片描述](https://img-blog.csdnimg.cn/40941bcbb0b54e5584ac66ec2e629c6b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

注意 ：此前大多flag藏在开发者工具，在元素中，这是我遇见第一个在网络中的题！
## burpsuite使用
先整个[使用教程...](https://blog.csdn.net/baidu_36124158/article/details/90906671)
绝对目前为止遇到的最复杂的使用软件（没有找到一个完整的安装教程），导致安装过程十分杂乱，关键全英看不懂，就离谱!一度以为自己的电脑坏了。
这是我遇到的一个问题，[CA证书的安装和卸载](https://blog.csdn.net/Aaron_Miller/article/details/117292591)
还有一个手动代理打开途径：![在这里插入图片描述](https://img-blog.csdnimg.cn/927c6275979745948b4ba64faa02b4b0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
言归正传，使用BurpSuite抓包查看网站Cookie信息：
![在这里插入图片描述](https://img-blog.csdnimg.cn/db9c44db697b4535b1da9bb1cf98ab43.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
Cookie对应的值是：look-here=cookie.php,接下来和第一种方法一样，访问他呗！得出页面与先前一样。
![在这里插入图片描述](https://img-blog.csdnimg.cn/d6deb763b43a47478170bf557fc1ef40.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
再抓一次，即得！（软件之间存在差别）![在这里插入图片描述](https://img-blog.csdnimg.cn/dda05f21fb68494799c8dc6dd914b0e6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

# disabled_button
老规矩，不会先[百度](https://www.w3school.com.cn/tags/att_input_disabled.asp)
>disabled 属性规定应该禁用 input 元素。
被禁用的 input 元素既不可用，也不可点击。可以设置 disabled 属性，直到满足某些其他的条件为止（比如选择了一个复选框等等）。然后，就需要通过 JavaScript 来删除 disabled 值，将 input 元素的值切换为可用。

这...又牵扯到一个问题，HTML学习不到位。
遍寻各大网站，收获如下：
>一般有两种方法
方法一:
删除代码：disabled=""
然后点击网页上的flag图标就可以得到flag了
方法二：
将disabled=""改为disabled=“false”
然后点击网页上的flag图标就可以得到flag了

首先打开开发人员工具，定位按钮的位置，双击，显示代码。找到disabled删除。
![在这里插入图片描述](https://img-blog.csdnimg.cn/d02b52d3dcf34a11afab098271d66716.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
点击空白刷新一下，按钮就可按了，点击flag按钮可得。
![在这里插入图片描述](https://img-blog.csdnimg.cn/9fdd4ccda0cf4c3ca9fbd3ada5f090ee.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# weak_auth（弱密码）
截个图，记住这种类型！
![在这里插入图片描述](https://img-blog.csdnimg.cn/e207ce237ed94999ac0d1e39dffc02a8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
还是逃不过burpsuite的使用。
与Cookie题的区别**先在登录界面，随便输入账户，密码。页面即可跳转，抓包**
![在这里插入图片描述](https://img-blog.csdnimg.cn/db5abf8734fa49bc9e8d1ce4ff16cd7a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
提示了，正确用户名。
接着如下操作（抓包）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2d75451a761c4b95b92c6ecc6e1a692a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
转换阵地（可以看一下网址对不对）
![在这里插入图片描述](https://img-blog.csdnimg.cn/45d300ae528741bba1291f76690b53c7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
要通过箭头，选中密码。
![在这里插入图片描述](https://img-blog.csdnimg.cn/0063b58a4cbe4182bb95476a14519960.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
转化阵地
![在这里插入图片描述](https://img-blog.csdnimg.cn/7bd0cc1bf13b4a158be6d51fe4c9168b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
学习一下，[burp字典_渗透中爆破字典的生成](https://blog.csdn.net/weixin_39623273/article/details/111200624)
需要到网上找常见密码，在load..中导入，点击右上按钮，开始寻找密码。
![在这里插入图片描述](https://img-blog.csdnimg.cn/fc9192d8802d4afc9305fb1b979601c8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
Length的数为437，唯一一个，输入答题界面，可得flag。

# simple_php
主要对于代码的分析理解。
由代码可得信息,a,b均为字符串类型,根据字符串转数字规则，字符串的开始部分决定了它的数字部分，该字符串的开头不是数字，则他的数字值为0，
则需满足a==0且if a为真，b不是数字且b>1234
![在这里插入图片描述](https://img-blog.csdnimg.cn/5184077a94a04e25acb220bd5e914378.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)

# get_post
X老师告诉小宁同学HTTP通常使用两种请求方法，你知道是哪两种吗？
提示告诉了，不知道，那就度娘，[这里！](https://blog.csdn.net/lenovouser/article/details/52909842)
>HTTP 请求方法. 根据 HTTP 标准，HTTP 请求可以使用多种请求方法。. HTTP1.0 定义了三种请求方法： GET, POST 和 HEAD方法。. HTTP1.1 新增了六种请求方法：OPTIONS、PUT、PATCH、DELETE、TRACE 和 CONNECT 方法。. 请求指定的页面信息，并返回实体主体。. 向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。

还是不理解post...
![在这里插入图片描述](https://img-blog.csdnimg.cn/cd2b136f82d045928bf6c6a94d0f00a5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
直接在地址栏加上?a=1

![在这里插入图片描述](https://img-blog.csdnimg.cn/bc722ec123524a5f911b6fa76d50eae7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
存在提示，关于post网上有两种方法。
## hackbar
经过查询得知，想要在网页上post，则需要使用浏览器插件hackbar 。谷歌和火狐浏览器上都有，只不过谷歌浏览器需要科学上网才能安装。（谷歌没找到，安了个火狐，两天挣扎...未果）
使用hackbar发送post请求
![在这里插入图片描述](https://img-blog.csdnimg.cn/a05dfd0266c2430b894675e30092340e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)

## burpsuite进行抓包修改(没整出来...CV的)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d7acd450badf401383fe0f9470514626.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
图示修改为POST
![在这里插入图片描述](https://img-blog.csdnimg.cn/7f406779f04d4cb48af8111472bda52b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
发包之后，就能直接拿到flag...恕我才疏学浅，没实现！我显示的是这...哪位大神知道愿意求教...
![在这里插入图片描述](https://img-blog.csdnimg.cn/950c471e75d44616bed508c6fd0a38a1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# xff_referer
>X-Forwarded-For（XFF）[链接...](https://www.cnblogs.com/huaxingtianxia/p/6369089.html)是用来识别通过HTTP代理或负载均衡方式连接到Web服务器的客户端最原始的IP地址的HTTP请求头字段。
简单地说，xff是告诉服务器当前请求者的最终ip的http请求头字段
通常可以直接通过修改http头中的X-Forwarded-For字段来仿造请求的最终ip
Referer  [链接...](https://blog.csdn.net/weixin_43639682/article/details/113879449?utm_medium=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~Rate-2.control404&depth_1-utm_source=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~Rate-2.control40)HTTP来源地址（referer，或HTTPreferer）
是HTTP表头的一个字段，用来表示从哪儿链接到当前的网页，采用的格式是URL。换句话说，借着HTTP来源地址，当前的网页可以检查访客从哪里而来，这也常被用来对付伪造的跨网站请求。

打开场景，存在提示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/1d6029fcb6e24de791302dd43fc13cca.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16) 
## burpsuit
抓包，发送到 Repeater 模块，
添加 xff 信息，X-Forwarded-For: 123.123.123.123。查看 Response 返回的信息（点一下左上角Sent）
![在这里插入图片描述](https://img-blog.csdnimg.cn/84937676e61e466f82d3d7a24c4b1e4e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
得到提示，再添加 referer 字段信息，Referer:https://www.google.com，既得
![在这里插入图片描述](https://img-blog.csdnimg.cn/7341b233600548d6b1730befe71da605.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
**注意，在图示的这软件中将文字添加在最底下的时候，好像不能查看 Response 返回的信息。**
## x-forward-for Header插件+burpsuit
添加x-forward-for Header插件，修改IP
![在这里插入图片描述](https://img-blog.csdnimg.cn/bdbe508415a64fcbbd2c0048dfc05564.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
刷新页面可得
![在这里插入图片描述](https://img-blog.csdnimg.cn/207435604fa047ed86477a80137a4781.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
 burpsuit抓包，尾行显示 x-forward-for 的部分通过插件修改完成，只需在后添加Referer:https://www.google.com，点击左上发送按钮，关闭捕获（图中深色的那个）
![在这里插入图片描述](https://img-blog.csdnimg.cn/37f84b8943c94139996d3660876d7c1e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
源网页，既可实现！
![在这里插入图片描述](https://img-blog.csdnimg.cn/b25f864ae46446c0910568fbb574dfbf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
# webshell
先不管会不会，打开，这...不是一句话木马嘛！提示可得密码：shell
![在这里插入图片描述](https://img-blog.csdnimg.cn/495085819ee74545a7e60a425d17de08.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
## antsword（蚁剑）
到网上看了看...要工具！antsword（蚁剑），菜刀等任选其一！
>蚁剑(AntSword)是一款开源的跨平台WebShell管理工具，它主要面向于合法授权的渗透测试安全人员以及进行常规操作的网站管理员。[源码+安装教程奉上](https://blog.csdn.net/qq_36235492/article/details/85713821)

![在这里插入图片描述](https://img-blog.csdnimg.cn/f6d5a34a02b74bbd99515af0046446e1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
点击添加按钮，即可出现图下
![在这里插入图片描述](https://img-blog.csdnimg.cn/545f39dedbac475ba6654186dd14eae7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
打开flag.txt 文件可得
## BurpSuite（试过...不会）
>1）拦截到页面请求，将其转到Repeater，并在最下方加入请求参数：shell = system(“find / -name ‘flag*’”);
2）查看Response，最下方有目标文件路径：
3）修改Repeater中的请求参数为：shell= system(“cat /var/www/html/flag.txt”);4）查看Response中的结果：
## HackBar（试过...也不会）
>1）在HackBar中输入相应URL和请求参数，请求参数为需要执行的shell：shell = system(“find / -name ‘flag*’”);
2）在原先的页面可以看到相应结果，在最下面即是目标文件的路径，如下图所示：
3）继续在Hackbar中执行命令：shell= system(“cat /var/www/html/flag.txt”);
4）在原页面即可查看到flag.txt中的flag内容：

和上述...不一致!
![在这里插入图片描述](https://img-blog.csdnimg.cn/6083250e71bb4b869e20d9da836bce29.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
以上两模块为[引用内容...](https://www.codenong.com/cs109750218/)
# command_execution
## 直接
先尝试ping一下本地地址127.0.0.1
![在这里插入图片描述](https://img-blog.csdnimg.cn/d3b83322c0604c0780f978de79d7b9fd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
尝试使用命令连接符，因为我们知道flag在flag.txt中，所以我们查找该文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/ec3ec969c7f64db4873793e38421edb9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
如图可得，在/home/目录下，从而输入：127.0.0.1 & cat /home/flag.txt
![在这里插入图片描述](https://img-blog.csdnimg.cn/8eb7adacfe604f6b9946812a8f796c22.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
## hackbar
没看懂，这是[链接...](https://blog.csdn.net/qq_41617034/article/details/91837257)
输入：target=127.0.0.1|cat /home/flag.txt
![在这里插入图片描述](https://img-blog.csdnimg.cn/f6848442e4604a4ea0a8ea832e143e99.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
注意输入时，cat与/有一个空格，否则不显示！
# simple_js
因为 hackbar，我用了火狐浏览器，ctrl+U可显示网页源码！
![在这里插入图片描述](https://img-blog.csdnimg.cn/0874802d3ccc4b119149d7a09cb302fe.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
>分析以上代码，有一个窗口给用户输入密码，完了直接弹窗dechiffre（h）的返回值，但是分析发现，弹窗值和用户输入完全没有关系,
>并且也没有看见什么别的提示，就一串诡异的十六进制，那么，直接上十六进制转字符串

![在这里插入图片描述](https://img-blog.csdnimg.cn/d16619e2660e416a8a21f94430d1e03e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
通过查询比较，应改为Escape/Unescape类型
![在这里插入图片描述](https://img-blog.csdnimg.cn/b0d234e039e84856a3ccb507aa4f7478.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
找个网站
![在这里插入图片描述](https://img-blog.csdnimg.cn/6ca429ddc1fd4d6da7c2e1ffb65ac5ce.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
想到ASCII表
![在这里插入图片描述](https://img-blog.csdnimg.cn/383803095dda422fa9f5ce5a1d3d2461.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
这位大佬，[直接上脚本](https://www.cnblogs.com/huazige/p/15033432.html)，我不会...

