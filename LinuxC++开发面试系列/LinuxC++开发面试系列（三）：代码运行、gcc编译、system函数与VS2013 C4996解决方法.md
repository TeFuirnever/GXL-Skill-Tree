@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)
## 代码讲解
如图即一个简单的 hello world 程序。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210611143249688.png)

```c
// 1、使用某个函数前，需要包含相应的头文件
// 2、可以通过man手册查询或者其他资料查询
// 3、头文件类似于菜单，头文件包含函数的声明，相当于菜单例举了菜名，函数调用，相当于点菜
// 4、<>通过包含系统的头文件（标准的头文件），""包含自定义的头文件
#include <stdio.h>

// 1、C语言由函数组成，有且仅有一个主函数
// 2、程序运行，先从main函数运行
// 3、return 0，程序正常结束
int main()
{
    // 注释：不是有效代码
    // 1、行注释， //相应的注释
    // 2、块注释，/* 相应的注释 */
    
    printf("hello world\n");
    // 1、这是一个C代码
    // 2、函数调用，printf功能往标准输出设备（屏幕）上打印内容
    // 3、\n代表换行
    
    return 0;
}
```

头文件目录：vi /usr/include/stdio.h
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061121582482.png)

## 代码运行
在上一个博客中（[LinuxC++开发面试系列（二）：权限修改、进程管理与vim](https://blog.csdn.net/TeFuirnever/article/details/117803941)）中我们给出了出版本代码 hello world，接下来，我们将就 Linux 和 Windows 两个环境下进行程序的编译。

#### 1）Linux下
运行编译的可执行程序，

0、切换目录，cd 即可

1、ls 查看目录信息

2、
	- gcc hello.c ，默认在当前路径生成 a.exe
	- gcc hello.c -o hello 生成 hello.exe

3、运行，在Linux下运行，当前路径，前面必须加 ./；非当前路径，写上完整路径即可
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612071756730.png)


#### 2）Windows 下
运行编译的可执行程序，

0、切换盘符，无需 cd

1、cd 目录

2、dir 查看目录信息

3、
	- gcc hello.c ，默认在当前路径生成 a.exe
	- gcc hello.c -o hello 生成 hello.exe
	
4、运行，在Windows下运行，无需./
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612071941420.png)

## gcc编译
C程序编译步骤：

1、预处理：gcc -E hello.c -o hello.i
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612073506547.png)

2、编译：   gcc -S hello.i -o hello.s
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612073541753.png)

3、汇编：   gcc -c hello.s -o hello.o
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061207360854.png)

4、链接：   gcc hello.o -o hello
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061207363422.png)
5、运行
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612073700736.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612073217744.png)

Linux查看需要链接的动态库：ldd
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612073733881.png)
Windows查看支持的动态库：Depends
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612075108715.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061207495770.png)

## system函数
system函数：
```c
int system(const char *command);
```

#### 实例1

01_test.c：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612091116700.png)

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    printf("before sys\n");

    // 1、需要头文件 #include <stdlib.h>
    // 2、system功能：调用外部程序
    system("ls -alh");

    printf("after sys\n");

    return 0;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612091054905.png)

#### 实例2
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612091624554.png)

02_waibu.c：
```c
#include <stdio.h>

int main()
{
    printf("我是小鲜肉，假的\n");

    printf("我是外部程序\n");

    return 0;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612091651763.png)

03_system.c：
```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    printf("before sys\n");

    // 1、需要头文件 #include <stdlib.h>
    // 2、system功能：调用外部程序
    system("./waibu");

    printf("after sys\n");

    return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612091735495.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612091601890.png)


字符编码：

1、Windows默认支持的中文编码为gbk，gb2312，ANSI

2、Linux默认支持的中文编码为utf-8（unicode）

#### 实例3
calc 计算器

vim：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612092312532.png)
vscode：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612092240656.png)

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    printf("before sys\n");

    system("calc");

    printf("after sys\n");

    return 0;
}
```
在Linux下无效：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612092021625.png)

只在Windows下有效：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612092204682.png)

## VS2013 C4996解决方法
由于微软在 VS2013 中不建议再使用c的传统库函数scanf，strcpy，sprintf等，所以直接使用这些库函数会提示C4996错误！

法一：

把这个宏定义放到.c文件的第一行
```c
#define _CRT_SECURE_NO_WARNINGS
```

法二：

把这个代码放在主函数的任意一行
```c
#pragma warning(disable:4996)
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210612092556727.png)

