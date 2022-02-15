@[TOC](upload-labs)

实话实说，关于这个upload-labs，我拖了好久，主要一直不理解这是个什么东西，又该上传什么样的文件，自己一直揪着不放，特别执着...看了网上许许多多的题解，对于上传的文件多为php后缀，从而做题也按php后缀走，但就目前理解来看，上传文件应不止这一种，奈何才疏学浅..不会！
题中的文件，只是个文件，看着其他题解中，用了一句话木马什么的，可得到下图这种！
![在这里插入图片描述](https://img-blog.csdnimg.cn/d2b225be86894b008ec1a2e5a6134868.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)

我也尝试过用它做题，结果电脑拦截太负责，它既不让我上传，还删我文件（这一个多月，打开软件，电脑就上不了网；几次，打开网站，网站不安全；全盘查杀，对我近日下的软件提出警告）杀毒软件...我还是不要动了吧，怕了，怕了，还是不要在危险的边缘试探，就放弃了。
# 做题文件命名为“假装病毒”，由此就牵扯出几个问题：
## 木马，病毒，蠕虫是什么？
>木马病毒的发作要在用户的机器里运行客户端程序，一旦发作，就可设置后门，定时地发送该用户的隐私到木马程序指定的地址，一般同时内置可进入该用户电脑的端口，并可任意控制此计算机，进行文件删除、拷贝、改密码等非法操作。
木马病毒”（Trojan）属于计算机病毒的一个子分类，除了木马病毒以外还有“后门病毒”、“蠕虫病毒”等等。安全软件会检测到病毒类后会显示对应的病毒类型（如下图），一般见到病毒名里有“Trojan”的就是“木马病毒”了。

>病毒：平时一般我们所说的病毒，指的是感染型病毒，是编制者在计算机程序中插入的破坏计算机功能或者数据的代码，能影响计算机使用，能自我复制的一组计算机指令或者程序代码。其具有传播性、隐蔽性、感染性、潜伏性、可激发性、表现性或破坏性。一般病毒的生命周期：开发期→传染期→潜伏期→发作期→发现期→消化期→消亡期。与生物病毒有很多的相似的地方，比如说自我繁殖、互相传染以及激活再生等生物病毒特征等等。

>蠕虫病毒:与木马病毒有本质区别的是，蠕虫病毒是一种能够利用系统漏洞通过网络进行自我传播的恶意程序，它不需要附着在其他程序上，而是独立存在的。当形成规模、传播速度过快时会极大地消耗网络资源导致大面积网络拥塞甚至瘫痪，这可要比木马病毒恐怖多的多。
## 木马，病毒二者的区别(发现自己文件命名可能存在错误)：

>1、 病毒会传染，而木马不会传染；
2、 病毒入侵电脑后会有感觉，而木马不会，主要原因是便其开展后续“工作”；
3、 病毒主要是以“破坏”著称，而木马主要是用来盗取用户信息。

## 以汉字命名文件在Burpsuite的影响
可能由于我的是英文版，也有可能是程序自身的设定问题，汉字（而后发现用中文输入法）命名的文件在抓包时显示的均为□，对于软件不熟悉的操作者而言，会产生不必要的麻烦，就是不太好找到，其他软件以此类推！

# Pass-01
首先将PHP文件直接上传，看看有没有提示（拦截方式是什么？**前端js验证**）
>客户端 JavaScript检验（通常为检测文件拓展名）
判断方法：在浏览加载文件，但还未点击上传按钮时便弹出对话框，内容如：只允许上传 .jpg / .jpeg / .png后缀名的文件，而此时并未发送数据包。
绕过办法：
1.利用BurpSuite之类的代理工具进行抓包。
2.修改webshell后缀类型为允许上传类型。
3.抓包来拦截将其后缀名改为对应服务器可以解析的后缀名。

 **还有一种修该函数的方法,看了半天，没找到函数，现在连网址也找不到了！**       
![在这里插入图片描述](https://img-blog.csdnimg.cn/4f8419766d2e40ad9b514ae56d0f2291.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
前端js拦截了，将php文件后缀修改成合法的格式（.gif ），上传文件。在使用burpsuite抓包
![在这里插入图片描述](https://img-blog.csdnimg.cn/08f31b85fef14bf5b899b7cedf6a4470.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
再修改为.php后缀。点击铅笔图形下方按钮（本人英语废...）
![在这里插入图片描述](https://img-blog.csdnimg.cn/cfbeff6367194cc0876fcf81db65f7c6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
可从此查看，是否上传成功！
# Pass-02
尝试上传文件！未能上传!
>后端MIME验证
>服务器MIME检测：即检测Content-Type的内容(Content-Type 实体头部用于指示资源的MIME类型media type ,在响应中，Content-Type标头告诉客户端实际返回的内容的内容类型。)
绕过方法：修改类型为允许上传的类型即可。

![在这里插入图片描述](https://img-blog.csdnimg.cn/9c9af328d8874e20b8b019461fa70316.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
无提示，在界面点击查看源码，找思路。这关只是对 content-type进行判断，在burp suite中，修改content-type为允许的类型即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/8321e1883048452ebd07c4ac0d0ddba2.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
即可上传成功！
![在这里插入图片描述](https://img-blog.csdnimg.cn/211aa0aac8dd462693d9f57038d44a8b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
网上有教程显示，先把.php文件后缀改为.jpg，而后在抓包更改时在连后缀在一起改回来，嗯...似乎没必要。
**抓包时尝试发现，点击抓包后，在上传文件，虽然文件显示不能上传，但在抓包显示的代码显示中仍存在文件。**
# Pass-03
尝试上传php文件，发现这关设置了文件后缀名黑名单。
![在这里插入图片描述](https://img-blog.csdnimg.cn/c7e748358082460687871d4f97d3e0c9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
>基于黑名单检测：黑名单的安全性比白名单的安全性低很多，攻击手法自然也比白名单多。一般由个专门的blacklist，里面包含常见的危险脚本文件。
绕过办法：1.文件大小写让绕过（Php ，PhP pHp，等）
         2.黑白名单绕过（php，php2，php3，php5，phtml，asp，aspx，ascx，ashx，cer，asa，jsp，        
           jspx）cdx，\x00hh\x46php
         3.特殊文件名绕过
            1）修改数据包里的文件名为 test.php 或 test.asp_(下划线是空格)由于这种命名格式在        
               windows系统里是不允许的，所以在绕过上传之后windows系统会自动去掉.点和空格。Linux和        
               Unix中没有这个特性。
            2）::$DATA(php在windows的时候如果文件名+"::DATA"会把::DATA之后的数据当作文件流处 
               理，不会检测后缀名，且保持"::DATA"之前的文件名，其目的就是不检查后缀名)
         4.0x00截断绕过（5.2 C语言中将 \0 当作字符串的结尾）
         5. .htaccess文件攻击（结合黑名单攻击）
         6. 解析绕过
## 大小写绕过
![这张，网上搬的，为了更严谨](https://img-blog.csdnimg.cn/28313b85531b4ce994895cdae6b6a013.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
这张...网上搬的，为了更严谨，直接改就行；实在不行就下一种。
![在这里插入图片描述](https://img-blog.csdnimg.cn/ba15e0e58bed43e3bf8195149217e71d.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
注意：这两种方法都会改变文件名称。
## 双写绕过
![在这里插入图片描述](https://img-blog.csdnimg.cn/1d0508abd4594149b749ebb915c762fa.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)
与上一个不同，此文件，后缀并不会改变，只改变文件名称。
![在这里插入图片描述](https://img-blog.csdnimg.cn/6722baff9c3c4cf3980aa887c053a816.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5LuU57G9Xw==,size_20,color_FFFFFF,t_70,g_se,x_16)


