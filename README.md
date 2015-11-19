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

使用加参数的命令：
pod install –verbose –no-repo-update
或者
pod update –verbose –no-repo-update

pod install --verbose --no-repo-update

6、设置行间距、字间距
//设置字间距
UniChar characterSpacing = 3;

NSMutableAttributedString *attributedString = [[NSMutableAttributedString alloc] initWithString:person];
[attributedString removeAttribute:(id)kCTKernAttributeName range:NSMakeRange(0, attributedString.length)];
CFNumberRef num =  CFNumberCreate(kCFAllocatorDefault,kCFNumberSInt8Type,&characterSpacing);
[attributedString addAttribute:(id)kCTKernAttributeName value:(__bridge id)num range:NSMakeRange(0, attributedString.length)];
CFRelease(num);

//设置行间距
UIFont *font = [UIFont systemFontOfSize:12];
NSMutableParagraphStyle *paragraphStyle1 = [[NSMutableParagraphStyle alloc] init];
paragraphStyle1.paragraphSpacing = 10;//段与段之间的距离
paragraphStyle1.lineSpacing = 10;//行与行之间的距离
paragraphStyle1.alignment = NSTextAlignmentLeft;//文字的显示方式：巨左、居中、居右
paragraphStyle1.firstLineHeadIndent = 50.0;
[attributedString addAttribute:NSParagraphStyleAttributeName value:paragraphStyle1 range:NSMakeRange(0, attributedString.length)];

//设置字体大小（必须设置，否则计算出来的cell的高度不准确）
[attributedString addAttribute:NSFontAttributeName value:font range:NSMakeRange(0, attributedString.length)];

self.AttributedStringperson = attributedString;


然后计算整个文字所占的位置大小：
CGSize contentSize = [person.AttributedStringperson boundingRectWithSize:CGSizeMake(maxW, MAXFLOAT) options:NSStringDrawingUsesLineFragmentOrigin | NSStringDrawingUsesFontLeading context:nil].size;

7、关于block的用法

How Do I Declare A Block in Objective-C?

1、As a local variable:

returnType (^blockName)(parameterTypes) = ^returnType(parameters) {...};
As a property:

@property (nonatomic, copy) returnType (^blockName)(parameterTypes);
As a method parameter:

- (void)someMethodThatTakesABlock:(returnType (^)(parameterTypes))blockName;
As an argument to a method call:

[someObject someMethodThatTakesABlock:^returnType (parameters) {...}];
2、As a typedef:

typedef returnType (^TypeName)(parameterTypes);
TypeName blockName = ^returnType(parameters) {...};
This site is not intended to be an exhaustive list of all possible uses of blocks.
If you find yourself needing syntax not listed here, it is likely that a typedef would make your code more readable.

Unable to access this site due to the profanity in the URL? http://goshdarnblocksyntax.com is a more work-friendly mirror.


8、设置tableview中个人信息页面分框之间的缝隙
- (nullable UIView *)tableView:(UITableView *)tableView viewForFooterInSection:(NSInteger)section
{
UITableViewHeaderFooterView *view = [tableView dequeueReusableHeaderFooterViewWithIdentifier:@"FotterView"];
if (view == nil) {
view = [[UITableViewHeaderFooterView alloc] initWithReuseIdentifier:@"FotterView"];
[view setBackgroundView:[UIView new]];
}
return view;
}

- (CGFloat) tableView:(UITableView *)tableView heightForFooterInSection:(NSInteger)section
{
tableView.tableFooterView.backgroundColor = [UIColor redColor];

return 20.0f;
}
第一组数据为空，作为顶部的空得部分

9、NSDictionary *infoDictionary = [[NSBundle mainBundle] infoDictionary];
CFShow(infoDictionary);
// app名称
NSString *app_Name = [infoDictionary objectForKey:@"CFBundleDisplayName"];
// app版本
NSString *app_Version = [infoDictionary objectForKey:@"CFBundleShortVersionString"];
// app build版本
NSString *app_build = [infoDictionary objectForKey:@"CFBundleVersion"];

10、在iOS 7中，苹果引入了一个新的属性，叫做[UIViewController setEdgesForExtendedLayout:]，它的默认值为UIRectEdgeAll。当你的容器是navigation controller时，默认的布局将从navigation bar的顶部开始。这就是为什么所有的UI元素都往上漂移了44pt。
修复这个问题的快速方法就是在方法- (void)viewDidLoad中添加如下一行代码：
1
self.edgesForExtendedLayout = UIRectEdgeNone;

解决tableview在iOS7和iOS之上的frame的设置问题
