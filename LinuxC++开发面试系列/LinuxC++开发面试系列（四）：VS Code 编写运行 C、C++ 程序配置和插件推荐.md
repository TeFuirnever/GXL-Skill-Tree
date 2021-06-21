@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)
## VS Code 的gcc、g++配置
#### 1、开发环境
首先是下载并安装 VS Code，官网在这里：[https://code.visualstudio.com/](https://code.visualstudio.com/)。

一般来说，VS Code 有两个不同的发布渠道：
- 一个是稳定版（Stable），也是使用最多的版本，每个月发布一个主版本；
- 另一个是内测版（Insiders），也即 VS Code 团队在使用的版本，目标是第一时间用上自己新加的功能并及时发现问题，（**微软内部对这个做法还有个专门的名词，叫做“吃自己的狗粮” (eat your own dog food**)），每周一到周五 UTC 时间早上6点从最新的代码发布一个版本；

如果你是刚接触 VS Code ，那么还是建议稳定版（Stable），因为 Bug 相对较少，功能稳定；但如果你是使用 VS Code 有一段时间了，那还是非常推荐试一试内测版（Insiders），因为可以尽早使用最新功能，并深度参与 VS Code 产品的开发过程，甚至可以贡献代码。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615152157874.png)
下载并安装即可。

这里需要说明的是，VS Code 核心是一个高性能的轻量级编辑器，而个性化的功能则交给插件系统，所以不是IDE（集成开发环境），是需要自行安装编译器的，由于这里是 C、C++ 程序配置，即下载编译器：[MinGW-w64 - for 32 and 64 bit Windows](https://sourceforge.net/projects/mingw-w64/files/)。

不建议安装 Download Latest Version，这是个在线安装包，可能因为国内的网络环境下载失败等等。往下稍微翻一下，选最新版本中的x86_64-posix-seh。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615153728818.png)
解压之后即可获得如下文件夹。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615153834971.png)
然后将该文件夹中最关键的文件放到你想放置的目录下，比如我是系统盘。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615154024463.png)
然后按照下面的方法设置环境变量。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615154148369.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615154426381.png)
安装完记得验证一下，按 Win+R，运行 cmd，输入 gcc，应该会提示，

```c
gcc: fatal error: no input files
compilation terminated.
```

而不是“不是内部命令或外部命令”或者“无法将 "gcc" 项识别为 cmdlet、函数、脚本文件或可运行程序的名称”。

输入 gcc -v 可以显示出 gcc 的版本。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615164244743.png)
这两项验证一定要符合。

然后打开
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615164617532.png)
关于插件的配置在下一章会详细介绍，一定要装的插件是C/C++。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615191756868.png)

**补充**
- 编译器的作用是把【源代码】编译成【可执行文件】；
- 编辑器的作用是敲打并撰写【源代码】；
- 大家熟知的 VS 2013 就是一个编译器，而微软自带的记事本就是一个编辑器；
- 编辑器想要完成编译器的工作，需要一个开发环境，即 MinGW-w64，MinGW-w64 是 gcc 在 Windows 下的移植（gcc 是编译 C语言 的程序，g++ 是编译 C++ 的程序）；

#### 2、文件配置
接下来需要配置一些文件，放在工作区文件夹中，注意，路径不能有中文和引号，最好不要空格，比如我是 VS-Code-Cpp，C 和 C++ 要分别建立不同的文件夹。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615192741362.png)
不要和 MinGW-w64 放在同一个文件夹中。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615192912211.png)
首先新建文件夹，名称为 .vscode；然后创建 launch.json，tasks.json，settings.json（不是setting.json） 放到.vscode文件夹下；最后复制粘贴并修改自己的对应文件；

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061519303674.png)

**launch.json代码**
```c
// https://code.visualstudio.com/docs/cpp/launch-json-reference
{
    "version": "0.2.0",
    "configurations": [{
        "name": "(gdb) Launch", // 配置名称，将会在启动配置的下拉菜单中显示
        "type": "cppdbg", // 配置类型，对于C/C++可认为此处只能是cppdbg，由cpptools提供；不同编程语言不同
        "request": "launch", // 可以为launch（启动）或attach（附加）
        "program": "${fileDirname}/${fileBasenameNoExtension}.exe", // 将要进行调试的程序的路径
        "args": [], // 程序调试时传递给程序的命令行参数，一般设为空
        "stopAtEntry": false, // 设为true时程序将暂停在程序入口处，相当于在main上打断点
        "cwd": "${workspaceFolder}", // 调试程序时的工作目录，此为工作区文件夹；改成${fileDirname}可变为文件所在目录
        "environment": [], // 环境变量
        "externalConsole": true, // 使用单独的cmd窗口，与其它IDE一致；为false时使用内置终端
        "internalConsoleOptions": "neverOpen", // 如果不设为neverOpen，调试时会跳到“调试控制台”选项卡，你应该不需要对gdb手动输命令吧？
        "MIMode": "gdb", // 指定连接的调试器，可以为gdb或lldb。但我没试过lldb
        "miDebuggerPath": "gdb.exe", // 调试器路径，Windows下后缀不能省略，Linux下则不要
        "setupCommands": [
            { // 模板自带，好像可以更好地显示STL容器的内容，具体作用自行Google
                "description": "Enable pretty-printing for gdb",
                "text": "-enable-pretty-printing",
                "ignoreFailures": false
            }
        ],
        "preLaunchTask": "Compile" // 调试前执行的任务，一般为编译程序。与tasks.json的label相对应
    }]
}
```

**tasks.json代码**
```c
// https://code.visualstudio.com/docs/editor/tasks
{
    "version": "2.0.0",
    "tasks": [{
        "label": "Compile", // 任务名称，与launch.json的preLaunchTask相对应
        "command": "g++",   // 要使用的编译器，C++用g++
        "args": [
            "${file}",
            "-o",    // 指定输出文件名，不加该参数则默认输出a.exe，Linux下默认a.out
            "${fileDirname}/${fileBasenameNoExtension}.exe",
            "-g",    // 生成和调试有关的信息
            "-m64",  // 不知为何有时会生成16位程序而无法运行，此条可强制生成64位的
            "-Wall", // 开启额外警告
            "-static-libgcc",     // 静态链接libgcc，一般都会加上
            "-fexec-charset=GBK", // 生成的程序使用GBK编码，不加这条会导致Win下输出中文乱码；繁体系统改成BIG5
            "-D__USE_MINGW_ANSI_STDIO", // 用MinGW写C时留着，否则不需要，用于支持printf的%zd和%Lf等
        ], // 编译的命令，其实相当于VSC帮你在终端中输了这些东西
        "type": "process", // process是把预定义变量和转义解析后直接全部传给command；shell相当于先打开shell再输入命令，所以args还会经过shell再解析一遍
        "group": {
            "kind": "build",
            "isDefault": true // 不为true时ctrl shift B就要手动选择了
        },
        "presentation": {
            "echo": true,
            "reveal": "always", // 执行任务时是否跳转到终端面板，可以为always，silent，never。具体参见VSC的文档，即使设为never，手动点进去还是可以看到
            "focus": false,     // 设为true后可以使执行task时焦点聚集在终端，但对编译C/C++来说，设为true没有意义
            "panel": "shared"   // 不同的文件的编译信息共享一个终端面板
        },
        "problemMatcher":"$gcc" // 捕捉编译时终端里的报错信息到问题面板中，修改代码后需要重新编译才会再次触发
        // 本来有Lint，再开problemMatcher就有双重报错，但MinGW的Lint效果实在太差了；用Clangd可以注释掉
    }]
}
```

**settings.json代码**
```c
{
    "files.defaultLanguage": "c", // ctrl+N新建文件后默认的语言
    "editor.formatOnType": true,  // 输入分号(C/C++的语句结束标识)后自动格式化当前这一行的代码
    "editor.suggest.snippetsPreventQuickSuggestions": false, // clangd的snippets有很多的跳转点，不用这个就必须手动触发Intellisense了
    "editor.acceptSuggestionOnEnter": "off", // 我个人的习惯，按回车时一定是真正的换行，只有tab才会接受Intellisense
    // "editor.snippetSuggestions": "top", // （可选）snippets显示在补全列表顶端，默认是inline

    "code-runner.runInTerminal": true, // 设置成false会在“输出”中输出，无法输入
    "code-runner.executorMap": {
        "c": "gcc '$fileName' -o '$fileNameWithoutExt.exe' -Wall -O2 -m64 -lm -static-libgcc -fexec-charset=GBK -D__USE_MINGW_ANSI_STDIO && &'./$fileNameWithoutExt.exe'",
        "cpp": "g++ '$fileName' -o '$fileNameWithoutExt.exe' -Wall -O2 -m64 -static-libgcc -fexec-charset=GBK && &'./$fileNameWithoutExt.exe'"
        // "c": "gcc $fileName -o $fileNameWithoutExt.exe -Wall -O2 -m64 -lm -static-libgcc -fexec-charset=GBK -D__USE_MINGW_ANSI_STDIO && $dir$fileNameWithoutExt.exe",
        // "cpp": "g++ $fileName -o $fileNameWithoutExt.exe -Wall -O2 -m64 -static-libgcc -fexec-charset=GBK && $dir$fileNameWithoutExt.exe"
    }, // 右键run code时运行的命令；未注释的仅适用于PowerShell（Win10默认）和pwsh，文件名中有空格也可以编译运行；注释掉的适用于cmd（win7默认）、PS和bash，但文件名中有空格时无法运行
    "code-runner.saveFileBeforeRun": true, // run code前保存
    "code-runner.preserveFocus": true,     // 若为false，run code后光标会聚焦到终端上。如果需要频繁输入数据可设为false
    "code-runner.clearPreviousOutput": false, // 每次run code前清空属于code runner的终端消息，默认false
    "code-runner.ignoreSelection": true,   // 默认为false，效果是鼠标选中一块代码后可以单独执行，但C是编译型语言，不适合这样用
    "code-runner.fileDirectoryAsCwd": true, // 将code runner终端的工作目录切换到文件目录再运行，对依赖cwd的程序产生影响；如果为false，executorMap要加cd $dir

    "C_Cpp.clang_format_sortIncludes": true, // 格式化时调整include的顺序（按字母排序）
}
```

下面编写代码，执行编译，进行调试。

- 新建源代码文件，如果是 C语言 的源代码，则后缀是 .c，如果是 C++，则是 .cpp。
- 源代码文件最好保存在工作区的 .vscode 文件夹外，可以自行创建文件夹，但路径里（包括文件名）不要含有中文和引号，最好不要有空格。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615194113525.png)

- 按Alt+Shift+F（或者用右键菜单）可以格式化代码；
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615194230972.png)

- 按 F5 为编译加调试，Ctrl+F5 为运行但不调试；
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615194403828.png)
- 加断点在列号前面点一下，右键可以加条件断点；
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615194527846.png)

- 加在 cout 函数处，就可以在输出时停下来进行调试：F5 是继续，F10 是单步跳过，F11 是单步调试，shift+F11 是单步跳出，Ctrl+shift+F5 是重新开始，shift+F5 是停止；
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061519474884.png)

- 左边有个调试栏，可以看到变量的值，如果没有可以手动添加，或在代码里选中右键直接添加；
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615195249748.png)

编写或复制代码：

```cpp
#include <iostream>

using namespace std;

int main()
{
    cout << "hello, world!" << endl;
    system("pause");
    return 0;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615203150642.png)
输出 hello world！
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615203220328.png)
#### 3、快捷键

> 编辑器与窗口管理
> - 打开新窗口： Ctrl+Shift+N
> - 关闭窗口： Ctrl+Shift+W
> - 同时打开的多个文件之间切换： Ctrl+Tab
> - 新建文件： Ctrl+N

> 格式调整
> - 代码行缩进： Ctrl+[ 、 Ctrl+] 或者 shift+Tab、Tab
> - 都懂： Ctrl+C 、 Ctrl+V 
> - 代码格式化： Shift+Alt+F，或 Ctrl+Shift+P 后输入 format code
> - 向上向下移动一行： Alt+Up 或 Alt+Down
> - 向上向下复制一行： Shift+Alt+Up 或 Shift+Alt+Down
> - 向上向下插入一行： Ctrl+Shift+Enter 或 Ctrl+Enter

> 光标相关
> - 移动到行首： Home
> - 移动到行尾： End
> - 移动到文件开头： Ctrl+Home
> - 移动到文件结尾： Ctrl+End
> - 选择从行首到光标处： Ctrl+Shift+Home
> - 选择从光标到行尾： Ctrl+Shift+End

> 重构代码
> - 重命名：选中后按 F2，输入新名字，回车，则所有引用也都同步更新
> - 跳转到下一个 Error 或 Warning：F8 逐个跳转

> 查找替换
> - 查找： Ctrl+F
> - 查找替换： Ctrl+H
> - 整个文件夹查找: Ctrl+Shift+F

> 显示相关
> - 全屏：F11
> - 侧边栏显/隐： Ctrl+B
> - 显示资源管理器： Ctrl+Shift+E
> - 显示搜索： Ctrl+Shift+F
> - 显示 Git： Ctrl+Shift+G
> - 显示 Debug： Ctrl+Shift+D
> - 显示 Output： Ctrl+Shift+U

> 其他
> - 自动保存：File -> AutoSave，或者 Ctrl+Shift+P，输入 auto

> 自定义
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615221807716.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021061522190321.png)

## VS Code 插件推荐
- Bracket Pair Colorizer 括号高亮。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615201911444.png)

- C/C++ C 语言和 C++ 的补全和debug。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615201933281.png)

- Chinese (Simplified) Language Pack for Visual Studio Code 汉化
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202111518.png)

- Code Runner 右键即可编译运行单文件，无法Debug
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202245679.png)

- Code Spell Checker 代码错误检查
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202330824.png)

- Indenticator 优化缩进
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202525848.png)

- One Dark Pro 暗色调主题
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202614442.png)

- Path Intellisense 补全路径名字
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202707772.png)

- Tabnine AI Code Completion for all major programming languages, autocomplete JavaScript, Python, TypeScript, PHP, Go, Java, Ruby, C/C++, HTML/CSS, C#, Rust, SQL, Bash, Kotlin, React, Swift, Scala, Sas 通过机器学习自动补全代码
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202730578.png)

- vscode-icons 图标美化
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210615202854895.png)
