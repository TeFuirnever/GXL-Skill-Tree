@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)
## Linux文件权限chmod
在上一个博客（[Linux常用命令系列（一）：目录结构与文件权限](https://blog.csdn.net/TeFuirnever/article/details/113784308?spm=1001.2014.3001.5501)）中讲解了文件权限的含义以及具体代表的权限，这个博客会讲解如何修改权限以达到更大的使用灵活性和限制性。

权限的种类共三种，即字符rwx。
- r代表可读（read）
- w代表可写（write）
- x代表可执行（execute）

权限的使用者共三种，即ugo。
- u = user用户
- g = group组
- o = other其他用户和组

另外，在修改权限时，可以使用字符a。
- a = all所有

最后，修改权限的方式主要有两种，即增减权限或者赋值权限。

#### 1）增减权限

+增加权限，-去除权限

chmod u-r a.txt
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611091934547.png)

即去除 a.txt 文件的 u 使用者的 r 权限。

chmod a+r a.txt

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611090842549.png)
即增加 a.txt 文件的 所有 使用者的 r 权限。

#### 2）赋值权限

- 字母权限：rwxrwxrwx，对应数字权限：111111111
- 字母权限：---------，对应数字权限：000000000 

其中，二进制表示的，0代表没有，1代表有，因此对应的三位表示法：
|  |  |
|--|--|
|000	|0|
|001	|1|
|010	|2|
|011	|3|
|100	|4|
|101	|5|
|110	|6|
|111	|7|

chmod 264 a.txt
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611091930161.png)

即去除 a.txt 文件的 u 使用者的 r 权限，具体是 u 变为 -w- 即 010——2，g 不变 rw- 即 110——6，o 不变 r-- 即 100——4，因此变化后的赋值是 264。

chmod 664 a.txt

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611090842549.png)
即增加 a.txt 文件的 所有 使用者的 r 权限，具体是 u 变为 rw- 即 110——6，g 变为 rw- 即 110——6，o 变为 r-- 即 100——4，因此变化后的赋值是 664。

## Windows与Linux
- Windows的书写方法：C:\Windows\linux\test\a.txt
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611095032857.png)


- Linux的书写方法：/home/alubuntu/linux/test/a.txt
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611094611470.png)

- 区别：Windows有盘符，Linux没有；Windows用反斜杠，Linux用斜杠。

## 绝对路径与相对路径
Windows：

当前目录是 C:\Windows 目录，要进入 Windows 下的 System 目录：
- 相对路径的写法：cd .\system
- 绝对路径的写法：cd C:\windows\system
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611100253556.png)
Linux：

当前目录是 /home/alubuntu/linux 目录，要进入 Linux 下的 test 目录：
- 相对路径的写法：cd ./test/
- 绝对路径的写法：cd /home/alubuntu/linux/test/
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611101601715.png)

## 用户登录
sudo su 管理员登录
sudo last 查看用户登录情况
exit 如果是切换后的登录用户，退出则返回上一个登录账号
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611102133640.png)

## 日历与时间
cal 查看日历
cal -y 查看一整年日历
date 显示当前时间
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611102527422.png)

## 磁盘管理
#### ps 静态进程查看（相当于Windows程序管理器）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611103041972.png)

ps：
-a：显示终端上所有的进程，包括其他用户的进程
-u：显示进程的详细状态
-x：显示没有控制终端的进程
-w：显示加宽，以便显示更多的信息
-r：只显示正在运行的进程

ps -aux
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611103322627.png)

ps -aux | grep gedit 显示指定进程gedit 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611103417668.png)

#### top 动态进程查看
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611103112940.png)

#### kill 终止和杀死指定进程
- kill 4085		    终止进程4085
- kill -9 4173	杀死进程4173

#### 检测磁盘空间 df
- df http -h 查看文件所在文件系统的大小
#### 检测目录所占磁盘空间 du
- du http -h 查看文件目录的大小

![在这里插入图片描述](https://img-blog.csdnimg.cn/202106111113592.png)

## 程序运行
#### hello world：

./hello 运行可执行文件
./hello & 可执行文件以后台方式运行（一般服务器程序在后台运行）
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061110394768.png)

#### http：

第一步：将 http.tar.gz 上传到 linux

第二步，一步解压：tar -xzvf http.tar.gz

第三步，进入 http 目录：cd http

第四步，查看目录中的文件：ls

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611104740711.png)
第五步，编译源代码为可执行程序：make

第六步，需要设置 linux 的防火墙，开放 80 端口，如果是 ubuntu，第六步省略。

第七步，在命令模式下，切换到root用户：su

第八步，启动软件：./myhttp start

如果看到如下显示，代表成功了。
```
listen 80 success
myhttp begin
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611105725135.png)

第九步，后台启动软件：./myhttp start &

第十步，查看后台运行程序：jobs

第十一步，查看状态：./myhttp status

第十二步，停止软件：./myhttp stop 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611105906210.png)

第十三步，运行服务器的客户端：http://127.0.0.1/
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611110328694.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611110519407.png)

第十四步，编译 hello.c 为 hello.cgi：gcc a.c -o a.cgi
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611111059985.png)

第十五步，运行服务器的 hello world：http://127.0.0.1/hello.cgi
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061111083152.png)

- ctrl + z 将运行中的程序调入后台
- fg + 编号 将后台运行程序调出前台

## 开关机
- reboot 重启操作系统
- shutdown -r now 重启os，会给别人提示
- shutdown -h now 立刻关机
- shutdown -h 20:25 系统在今天的20：25关机
- shutdown -h +10 系统再过十分钟后自动关机
- init 0 关机
- init 6 重启

## 字符界面与图形界面切换
ctrl +alt +f2 切换成字符界面
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611111942201.png)

ctrl +alt +f7 切换到图形界面
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061111201342.png)

## IP地址和ping连接
查看IP地址：ifconfig
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611112217464.png)

连通某个IP地址：ping
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611112150105.png)

## vi的使用

#### 输入模式与命令模式：
- a 代表从命令模式进入输入模式，在光标当前位置后面追加
- i 代表从命令模式进入输入模式，在光标当前位置插入
- ESC 代表从输入模式进入命令模式

#### 保存文件
- :w 文件名
- :q 退出（如果文件内容被修改了，直接用 :q 退出，会提示错误，vi不允许退出）
- :wq 保存退出（:qw这样写是错误的），ZZ（shift+z+z） 保存退出
- :q! 不保存退出

#### vi文件：
- vi abc.txt 如果abc.txt存在，那么就打开这个文件，如果不存在就创建一个新文件，同时打开
- vi hello.c +5打开并跳到第五行

#### 快捷键：
- i 光标位置当前处插入文字
- o 光标位置下方开启新行
- O 光标位置上方开启新行
- I 光标所在行首插入文字
- A 光标所在行尾插入文字
- 【n】dd删除从当前行开始的n行（剪切）
- 【n】yy复制从当前行开始的n行
- p 粘贴
- u 撤销
- gg 文件第一行行首
- G 文件最后一行行首
- 【n】gg 到指定行行首

#### 查找字符：
- /main + 回车 查找指定字符串
	- n 下一个
	- N 上一个

#### 实例：

用vi写一个a.c，文件名可以自己起，但扩展名要为.c，.c代表c语言程序

```c
#include <stdio.h>

int main()
{
	printf("hello world\n");
	
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611143249688.png)

