@[toc]

## Linux介绍
Linux 是在计算机上面运行的，那么它是一组软件还是一段程序？又或者它是操作系统或者应用程序？又或者它是在计算机软件上运行还是在计算机硬件上运行？Linux和Windows谁厉害？

来看一张很有意思的图，Linux 在喝 Windows 。。。哈哈
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210181028726.png)
众所周知，计算机主机是由一堆硬件所组成的，那么如何有效地控制这些硬件资源呢，计算机需要一个资源分配管理员，所以就有了操作系统这个概念。除了分配资源之外，还提供计算机运行所需功能，更是为工程师提供了更易开发的环境和接口。

到这里了，你大概就知道了，

***

Linux 就是【操作系统】，即【核心】与【系统呼叫】这两层，也就是【硬件】与【应用程式】中间的部分。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210182610373.png#pic_center)
***摘自《鸟哥的Linux私房菜-基础篇》第四版***

***

从上图可以看出，核心与硬件的关系密切，但是由于早期的 Linux 是针对 386 开发的，所以只是操作系统而不具备其他的应用程序，因此你还需要在 Linux 基础上安装你所需要的软件。那么它和我们知道的 Windows 是一样的嘛，可以在不同的电脑上运行？

不同种类的操作系统具有自己的核心，而硬件是由核心控制的，所以需要修改操作系统的源码才能进行【软件移植】。

## Linux与Windows

那么 Linux 与 Windows 谁厉害呢？

优缺点如下：
- 首先，个人感觉 UI 界面上 Windows 要比 Linux 更优美一些；
- 然后，Linux 软件都是【开源】的，Windows 上有免费的但很多是需要授权的；
- 接着，Linux通常通过命令行来执行相关操作，Windows 可以直接打开图形界面；
- 其次，Linux 不用补丁，并且由于其开源的特性，维护安全方面有保证，Windows 则需要经常打补丁；
- 最后，两种系统都可以提供给普通用户和商用服务器进行使用。

## 使用者与群组和其他人
#### 1）文件拥有者
对于首次接触 Linux 的朋友来说，大改会觉得奇怪，为什么有这么多使用者，分什么拥有者，群组还有其他人之类的，有什么用？

其实这是一种相当健全且好用的安全防护功能，可以在最大程度上尊重每个人的隐私权，并且根据每个人的喜好进行工作环境的个性化。让我用一个例子来说明这其中的关系。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021020554838.png#pic_center)

假设你和自己的女票写了情书，可能是微信，可能是email，现在你想把这个情书打印或者转存成文件，放在自己家里的电脑里，但是你并不希望其他人看到这个情书。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210210516302.png#pic_center)

所以你把这个文件设置成只有你才能查看和编辑，其他人只会知道这是一个有趣或者秘密的文件。

#### 2）群组

那么群组呢？其实群组也是最有用的功能之一，尤其是当你在团队开发时。一方面，你需要开放一些资源给团队的成员使用；另一个方面，你不能开放所有资源给团队成员使用。

举个例子，你的情书当然不会开放给群组使用，但是家庭相册是需要开放给每个人使用和查看的。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210211800457.png#pic_center)
这个时候你只需要开放大家查看和下载家庭相册的权利即可。但是你需要给其他人别的权力，比如大家都可以上传属于自己的文件，就像你的情书一样。同时这是一个群组，也就是说，和微信或者QQ群一样，除了家庭群组之外，你还可以拥有其他群组，比如基友，比如学校。

#### 3）其他人

其他人是什么意思呢？还是以刚才的例子为例。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021021280650.png#pic_center)
不同群组中的人之间就是其他人关系，除非大家通过共同的一个人，才能分享互相之间的资源。

#### 4）文件位置
在 Linux 系统中，默认情况下，所有的系统账号与相关信息，都记录在下面这个文件夹下 /etc/passwd。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210214107885.png#pic_center)
个人密码则是记录在 /etc/shadow 中。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210214449699.png#pic_center)
所有的组名都记录在 /etc/group 中。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210214540338.png#pic_center)

## Linux文件权限

对于上一节谈到的文件权限，作为一个重要指令，那么如何查看当前文件的归属？

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210214848661.png#pic_center)
假设以图中的主函数为例，可以看到一共分为七个部分。

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021021510485.png#pic_center)
从左向右，依次是文件权限，文件个数，文件拥有者，群组，文件大小，文件修改日期，文件名。

这里用到了一个命令行是：

```shell
ls -lah
```

具体的含义将会在下面详细介绍，具体来看一下文件权限部分的情况。

***

#### 1）文件权限

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210215541701.png#pic_center)
***摘自《鸟哥的Linux私房菜-基础篇》第四版***

***

可以看到整个部分一共分为十个位置，分别是文件类型，文件拥有者权限，群组权限，其他人权限。其中，文件类型一共分为几种：
- -：普通文件
- d：目录文件/文件夹
- c：硬件字符设备（装置文件里的串行端口设备，如键盘，鼠标<一次性读取装置>）
- b：硬件块设备（装置文件里的可供储存的接口设备<可随机存取装置>）
- s：管道文件
- l：软链接文件

接下来的字符rwx分别是什么意思呢？
- r代表可读（read）
- w代表可写（write）
- x代表可执行（execute）

需要注意的是，这三种权限的相对位置不会发生改变，如果没有该权限，那么该位置是 - 。

#### 2）文件个数

每个文件都会和其他文档之间构建一个文件系统，这里需要注意的是，对于文件夹来说，至少连接数是2。其实表示的就是当前文件夹下的文件夹个数，所以记得算上下面两个。
- .代表当前目录
- ..代表上一级目录


#### 3）文件拥有者

#### 4）群组

这两项可能决定了当前文件在不同人手里的权限，可以通过一个命令进行查询。

#### 5）文件大小

该项表示文件大小，默认单位是bytes。如果想要变成带单位的表示，只需要加上 -h 即可。这里文件较小，所以差别较小。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210224852476.png#pic_center)

#### 6）文件修改日期
如果想要显示详细时间的话，使用命令 ll 即可。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210210225754678.png#pic_center)
如果该文件的修改时间距离现在太久，那么只会显示年份。

#### 7）文件名
除了 . 和 .. 之外，就是正常的文件名。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213223033853.png#pic_center)
特殊文件会有相应的尾缀来表示其打开或运行方式。

## whoami命令
如果想要查看自身用户，可以使用 `whoami` 命令用于显示自身用户名称，相当于执行 `id -un` 指令。

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021322434266.png#pic_center)

## ls命令
```
Linux命令格式
command [-options] [parameter1] ...
```

ls -a 显示所有文件及目录 (. 开头的隐藏文件也会列出)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021322544915.png#pic_center)

ls -l 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213225558433.png#pic_center)

ls -A 同 -a ，但不列出 "." (目前目录) 及 ".." (父目录)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021322580935.png#pic_center)

ls -F 在列出的文件名称后加一符号；例如可执行档则加 "*", 目录则加 "/"

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213225916504.png#pic_center)

ls -R 若目录下有文件，则以下之文件亦皆依序列出

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213230020834.png#pic_center)

ls --help 帮助文档

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213230226182.png#pic_center)

```
man ls 
空格：显示手册页的下一屏
Enter键：一次滚动手册页的一行
b：回滚一屏
f：前滚一屏
q：推出man命令
h：列出所有功能键
/word 搜索word字符串
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213230335188.png#pic_center)

ls -h以人能看懂的方式显示

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210213230524328.png#pic_center)

ls + 指定文件名，显示指定文件是否存在
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021421174122.png#pic_center)


#### 1）重定向 >
ls > test.txt
- 存在，覆盖
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021421283062.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214212846531.png#pic_center)

- 不存在，新建
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021421313935.png#pic_center)

#### 2）追加 >
ls >> text.txt
- 存在，添加
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214214203948.png#pic_center)
- 不存在，新建
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214214426288.png#pic_center)

#### 3）正则化匹配

*，？ 通配符

其中 * 是代表多个字符的匹配，？ 是代表某一个字符的匹配。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214215010387.png#pic_center)

## 快捷键命令

Tab键可以自动补全

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214215552340.png#pic_center)

方向键可以回溯历史

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214215942879.png#pic_center)

history可以看看历史

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214220028530.png#pic_center)

clear 清屏

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214220809894.png#pic_center)
file world 查看文件类型

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215153547732.png#pic_center)

which 在环境变量$PATH设置的目录里查找符合条件的文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215161938946.png#pic_center)

du ./目录 -h 查看某个目录大小

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215162307758.png#pic_center)


## 管道命令

| 管道
grep 关键字过滤

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021422112231.png#pic_center)
可以与多种命令进行结合

grep [0-9]abs[0-9] test.txt -n 查找4abc5

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214223934206.png#pic_center)
与 grep .abs. test.txt -n 等价

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214223953713.png#pic_center)

grep ^1 test.txt 搜寻以1开头
grep 1$ test.txt 搜寻以1结尾

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214224249539.png#pic_center)


## cd命令
cd 切换主目录

cd ~ 切换主目录

cd . 切换当前目录

cd .. 切换上级目录

cd - 切换上一个目录
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214221331317.png#pic_center)

## mkdir命令
mkdir abs 创建abs目录

mkdir ./a/b/c -p 递归创建目录

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214221537523.png#pic_center)

## rmdir命令

rmdir abs 删除空文件夹
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214221719950.png#pic_center)

## rm命令

rm abs -r 删除目录
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021422194623.png#pic_center)

rm 1.c 删除文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214222152531.png#pic_center)

rm * -rf 删除所有，递归，无提示

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021422234022.png#pic_center)

rm *.png -rf 和 rm * .png -rf
- rm *.png -rf 是删除所有的png格式文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214222533442.png#pic_center)
- rm * .png -rf 是删除所有文件和所有的png格式文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214222625110.png#pic_center)

rm 1.c -i 人性化询问
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214222928787.png#pic_center)

## ln命令

ln -s 创建一个软链接，相当于快捷方式。删除源文件，软链接置零

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021422471744.png#pic_center)
如果没有参数，ln默认创建的是硬链接。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214224853459.png#pic_center)

修改源文件，硬链接也修改

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210214225122135.png#pic_center)

硬链接只能链接普通文件，不能链接目录。


## find命令

find可以递归查找指定目录下所有子目录
- find ./ -name b.txt   在当前目录下查找名字叫b.txt的文件
- find ./ -name test.txt   在当前目录下查找名字叫test.txt的文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021515042333.png#pic_center)

find ./ -size 4k/+4k/-4k 在当前目录下寻找大小等于/大于/小于4k的文件（k小写，M大写）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215150910952.png#pic_center)

find ./ -size +1k -size -3k 在当前目录下寻找大小大于1k小于3k的文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215151223898.png#pic_center)

find ./ -perm 0777 在当前目录下寻找权限为777的文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215151434416.png#pic_center)

## cp命令

cp hello.c mike.c 复制hello.c为mike.c

![在这里插入图片描述](https://img-blog.csdnimg.cn/202102151519543.png#pic_center)

cp test/ mike -r 复制test目录为mike目录

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215152302933.png#pic_center)

cp hello.c result.c -v 能看到复制的进度

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215152505968.png#pic_center)

## mv命令
mv hello.c test 移动并改名
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215152857194.png#pic_center)

mv hello.c a.c 移动并改名
mv a.c amd 移动并改名
 
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215153245877.png#pic_center)

## tar命令

tar -cvf abc.tar abc 把abc这个目录打包，生成一个文件名字叫abc.tar

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215154101343.png#pic_center)

tar -xvf abc.tar 把abc.tar这个文件中所有的文件提取出来

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021515451945.png#pic_center)

tar -xvf abc.tar -C mike 指定解压目录

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215155200148.png#pic_center)

tar只负责把多个文件打包，而不负责压缩

其中，-c 创建 -x 解压 -v 进度 -f 文件名

## gzip命令
gzip 【-r】 abc.tar 把abc.tar文件压缩为abc.tar.gz

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215155552323.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215155734636.png#pic_center)

gzip -d abc.tar.gz 把abc.tar.gz解压为abc.tar

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215155651900.png#pic_center)

tar -czvf abc.tar.gz 所需文件，一步到位，从普通文件之间变成tar.gz

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215160036887.png#pic_center)

tar -xzvf abc.tar.gz 一步到位，从tar.gz变成普通文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215160222202.png#pic_center)

## bzip命令
bzip2 abc.tar 压缩文件为abc.tar.bz2

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215160521442.png#pic_center)

bzip2 -d abc.tar.bz2 解压缩文件为abc.tar

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215160636918.png#pic_center)

tar -cjvf abc.tar.bz2 所需文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021516112310.png#pic_center)

tar -xjvf abc.tar.bz2

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215161216791.png#pic_center)

## zip命令
zip -r abc.zip abc.tar 把abc.tar压缩为abc.zip

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215161430607.png#pic_center)

unzip abc.zip abc.tar 把abc.zip解压为abc.tar

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215161543970.png#pic_center)

## su命令
#### 1）ubuntu设置root用户密码的方法

ubuntu系统在安装的时候没有设置过root用户的密码，或者设置了密码都可以：
- sudo passwd root
- 提示你输入当前用户的密码
- 输入你当前用户的密码
- 提示你输入root用户的密码，要输两遍

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215162528541.png#pic_center)

#### 2）切换用户
su -
再输入root密码就可以了
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021021516261483.png#pic_center)

#### 3）新建用户
useradd -d /home/abc abc -m 新建一个用户，用户名叫abc

passwd abc 修改abc用户的密码
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215163537382.png#pic_center)
- -d的意思是指定用户的主目录
- 什么是主目录？每个用户都有一个家，这个家其实是一个目录，用户登陆的时候默认的当前目录。所有的用户都需要有一个主目录，普通用户的主目录一般是在/home目录下。用户名和主目录的名字是一样的。
- -m的意思是，如果主目录不存在，那么就自动创建这个目录
- 如果创建用户的时候，没有指定用户所属的组名，那么系统会自动创建一个和用户名一样的组名，并且自动的把这个用户放到同名的组里
- 创建完用户，紧接着就要修改用户密码


su不加-，只是切换用户，但不改变当前目录
su - ,切换用户，同时将当前目录切换到目标用户的主目录
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210215164239762.png#pic_center)


#### 4）删除用户
userdel abc
删除abc这个用户，但不会自动删除abc的主目录

userdel -r abc
删除abc用户，同时自动删除用户的主目录

