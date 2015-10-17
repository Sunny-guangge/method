# method
文字记录笔记

1、插入到数组的最前面

NSRange range = NSMakeRange(0, newArray.count);
NSIndexSet *set = [NSIndexSet indexSetWithIndexesInRange:range];
[array insertObjects:newArray atIndexes:set];

2、添加pch文件
$(SRCROOT)/pch/pchFile.pch

3、启动mysql
localhost:~ user$ alias mysql=/usr/local/mysql/bin/mysql

localhost:~ user$ alias mysqladmin=/usr/local/mysql/bin/mysqladmin

localhost:~ user$ mysql -u root -p

4、配置openfire服务器的数据库操作：
第一次安装mysql成功之后

点击Start MySQL Server按钮，启动mysql

二、打开终端，定义mysql别名

输入alias命令

alias mysql=/usr/local/mysql/bin/mysql
回车，再输入

alias mysqladmin=/usr/local/mysql/bin/mysqladmin
三、设置mysql root帐号的密码

mysqladmin -u root password 初始密码
2.如果设置完密码后，需要修改，执行命令

mysqladmin -u root -p  password 最新密码
接着会提示输入密码，此时输入旧密码，回车

四、连接数据库

mysql -u root -p
然后提示输入密码，输入三中设置的初始密码

进入文件编辑：sudo vi 文件名

创建数据库：create database openfire

保存数据库修改：\u openfire
现实所有的数据库：show databases

删除数据库：drop database openfire;

5、使用cocoaPod
一、找到文件，输入vim Podfile；
二、开始输入i  然后输入
platform :ios, '7.0'
pod 'XMPPFramework', '~> 3.6.5'（例子）
然后开始下载输入：
pod install --verbose --no-repo-update

