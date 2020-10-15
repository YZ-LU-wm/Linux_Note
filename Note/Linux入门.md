# <font color="black">Linux学习笔记<font>
## <font color="#008000">目录</font>
[TOC]
## <font color="#C0C0C0">1&nbsp;&nbsp;|&nbsp;&nbsp; 什么是shell</font>
### <font color="#008000">1.1&nbsp;&nbsp;终端（terminal）</font>
&nbsp;&nbsp;在Linux系统中，终端是程序员与计算机交互的主要方式，学习并掌握Linux的主要命令，可以灵活控制计算机。很多人是从Windows等图形操作系统转而学习Linux系统的，或许一开始不是很习惯，但是掌握Linux系统的基本指令是很有用的。

### <font color="#008000">1.2&nbsp;&nbsp;打开终端</font>
&nbsp;&nbsp;打开终端可以采取多种方式，如果你的操作系统配置了GUI,那么打开终端是容易的。主要有以下方式：
* Ubuntu中可以使用快捷键Ctrl+Alt+T打开终端。
* 可以在桌面单击鼠标右键，在弹出菜单中点击”在终端中打开“。<br>

当终端被打开后，你将看到如下信息：
```
yuzl@yuzl-virtual-machine:~$ 
```
&nbsp;&nbsp;这行信息称之为命令提示符，命令提示符由【用户名】【计算机名】【当前工作目录】【$/#】组成。其中$表示普通用户，#表示管理员用户。在Linux中不同用户对应着自己的权限，root用户权限最大，它可以对计算机各种文件进行修改、删除等操作。但是，home目录是普通用户唯一可存入文件修改文件的地方。
### <font color="#008000">1.3&nbsp;&nbsp;命令历史</font>
&nbsp;&nbsp;终端提供了一个很好的功能，如果你想查看你的命令输入历史，你可以使用上下箭头来查看。也可以使用命令`history`来查看输入历史。下面是一个用`history`命令查看历史的例子。

```
yuzl@yuzl-virtual-machine:~$ history
1  reboot
2  sudo
```
### <font color="#008000">1.4&nbsp;&nbsp;几个简单的命令</font>
&nbsp;&nbsp;你可以输入以下命令`date`来查看计算机的日期：
```
yuzl@yuzl-virtual-machine:~$ date
2020年 10月 15日 星期四 09:56:38 CST
```
你还可以用命令`cal`查看当前月份的日历：
```
yuzl@yuzl-virtual-machine:~$ cal
      十月 2020         
日 一 二 三 四 五 六  
             1  2  3  
 4  5  6  7  8  9 10  
11 12 13 14 15 16 17  
18 19 20 21 22 23 24  
25 26 27 28 29 30 31 
```
查看磁盘剩余空间，`df`:
```
yuzl@yuzl-virtual-machine:~$ df
文件系统           1K-块     已用     可用 已用% 挂载点
udev              975304        0   975304    0% /dev
tmpfs             200696     1612   199084    1% /run
/dev/sda5       40503552  9928508 28487876   26% /
...
```
同样，使用`free`查看内存剩余量：
```
yuzl@yuzl-virtual-machine:~$ free
              总计         已用        空闲      共享    缓冲/缓存    可用
内存：     2006924      787508      460284         636      759132     1036824
交换：     1918356      464640     1453716
```
### <font color="#008000">1.5&nbsp;&nbsp;关闭终端</font>
&nbsp;&nbsp;你可以在图形界面用鼠标直接点击关闭按钮关闭终端。也可以在终端中输入`exit`来关闭终端。
```
yuzl@yuzl-virtual-machine:~$ exit
```
## <font color="#C0C0C0">2&nbsp;&nbsp;|&nbsp;&nbsp;文件系统</font>
&nbsp;&nbsp;Linux系统可以说是文件组织起来的，在Linux系统中可以说“一切都是文件”。这句话将在后续的学习中得到证明。在Linux系统中只有一个文件目录树，这可颗是一颗倒立的树。每一个文件夹都有他自己的作用。
### <font color="#008000">2.1&nbsp;&nbsp;Linux文件系统</font>
|目&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;录|作&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;用|
|--|--|
/|根目录，万物起源。
/bin|包含系统启动和运行所必须的二进制程序。
|/boot|包含Linux 内核、初始RAM磁盘映像（用于启动时所需的驱动）和启动加载程序。
/dev|这是一个包含设备结点的特殊目录。“一切都是文件”，也适用于设备。在这个目录里，内核维护着所有设备的列表。
/etc|这个目录包含所有系统层面的配置文件。它也包含一系列的shell脚本，在系统启动时，这些脚本会开启每个系统服务。这个目录中的任何文件应该是可读的文本文件。
/home|在通常的配置环境下，系统会在/home下，给每个用户分配一个目录。普通用户只能在自己的目录下写文件。这个限制保护系统免受错误的用户活动破坏。
/lib|包含核心系统程序所使用的共享库文件。这些文件与Windows 中的动态链接库相似。
|/media|在现在的Linux 系统中，/media目录会包含可移动介质的挂载点，例如USB驱动器，CD-ROMs 等等。这些介质连接到计算机之后，会自动地挂载到这个目录结点下。|
/mnt|在早些的Linux 系统中，/mnt 目录包含可移动介质的挂载点。
/opt|这个/opt 目录被用来安装“可选的”软件。这个主要用来存储可能安装在系统中的商业软件产品。
/proc|这个/proc 目录很特殊。从存储在硬盘上的文件的意义上说，它不是真正的文件系统。相反，它是一个由Linux内核维护的虚拟文件系统。它所包含的文件是内核的窥视孔。这些文件是可读的，它们会告诉你内核是怎样监管计算机的。
/root| root 帐户的家目录。
/sbin| 这个目录包含“系统”二进制文件。它们是完成重大系统任务的程序，通常为超级用户保留。
/tmp| 这个/tmp 目录，是用来存储由各种程序创建的临时文件的地方。一些配置导致系统每次重新启动时，都会清空这个目录。
/usr| 在Linux 系统中，/usr目录可能是最大的一个。它包含普通用户所需要的所有程序和文件。
/var| 除了/tmp 和/home目录之外，相对来说，目前我们看到的目录是静态的，这是说，它们的内容不会改变。/var 目录存放的是动态文件。各种数据库，假脱机文件，用户邮件等等，都位于在这里。
/var/log| 这个/var/log目录包含日志文件、各种系统活动的记录。这些文件非常重要，并且应该时时监测它们。其中最重要的一个文件是/var/log/messages。注意，为了系统安全，在一些系统中，你必须是超级用户才能查看这些日志文件。
### <font color="#008000">2.2&nbsp;&nbsp;在文件系统中跳转</font>
&nbsp;&nbsp;收先我们需要学习怎样打开一个文件夹，或者查看当前工作空间。
* pwd &nbsp;&nbsp;将打印出当前工作的目录。
* cd  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;改变路径。
* ls  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;列出指定目录中的内容。

在Linux终端中命令对大小写敏感，你必须按照指定大小写输入，否则系统无法识别。
#### <font color="#008000">2.2.1&nbsp;&nbsp;打印当前工作目录</font>
语法：<br>
`pwd [option]`<br>
下面是使用pwd命令的一些例子：
```
yuzl@yuzl-virtual-machine:~$ pwd
/home/yuzl
```
参数|作用
-|-
-L|	打印 $PWD 变量的值，如果它包含了当前的工作目录
-P|	打印当前的物理路径，不带有任何的符号链接
**注意：默认情况下,pwd的行为和带-L选项一致。**
#### <font color="#008000">2.2.2&nbsp;&nbsp;改变工作目录</font>
&nbsp;&nbsp;改变shell工作目录。改变当前目录至DIR目录。默认的DIR目录是shell变量HOME的值。变量 CDPATH 定义了含有DIR的目录的搜索路径，其中不同的目录名称由冒号(:)分隔。一个空的目录名称表示当前目录。<br>
语法：<br>
`cd [-L|[-P [-e]] [-@]] [目录]`<br>
掌握一些快捷键，对工作效率的提高非常有用。对于cd命令有一些快捷键盘：<br>
1. cd&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;默认打开当前用户的家目录
2. cd&nbsp;~&nbsp;&nbsp;&nbsp;&nbsp;打开当前用户的家目录
3. cd&nbsp;-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;更改工作目录到之前的目录
4. cd&nbsp;~user_name&nbsp;&nbsp;打开指定用户的家目录
5. cd&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;打开当前工作目录
6. cd&nbsp;..&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;返回上一级目录
```
yuzl@yuzl-virtual-machine:/usr/bin$ cd
yuzl@yuzl-virtual-machine:~$ pwd
/home/yuzl
```
```
yuzl@yuzl-virtual-machine:/usr/bin$ pwd
/usr/bin
yuzl@yuzl-virtual-machine:/usr/bin$ cd ~
yuzl@yuzl-virtual-machine:~$ pwd
/home/yuzl
```
```
yuzl@yuzl-virtual-machine:/usr/bin$ cd ~
yuzl@yuzl-virtual-machine:~$ pwd
/home/yuzl
yuzl@yuzl-virtual-machine:~$ cd -
/usr/bin
```
```
uzl@yuzl-virtual-machine:/usr/bin$ cd ~yu
yuzl@yuzl-virtual-machine:/home/yu$ 
```


#### <font color="#008000">2.2.3&nbsp;&nbsp;列出工作目录中的内容</font>
&nbsp;&nbsp;由于我们大部分时间都是在跟终端打交道，而终端又没有图形界面，但是我们有又需要查看文件夹内的内容。因此，我们可以使用命令`ls [option]  [路径]`来列出文件夹中的内容。
```
yuzl@yuzl-virtual-machine:~$ ls /home/yuzl
 公共的   图片            下载   Hello.java   VMwareTools-10.3.22-15902021.tar.gz
 模板    '未命名 1.odp'   音乐   pp.py        vmware-tools-distrib
 视频     文档            桌面   snap
```
如果省略路径，那么命令`ls`将列出当前工作目录下的文件或文件夹。
```
yuzl@yuzl-virtual-machine:~$ pwd
/home/yuzl
yuzl@yuzl-virtual-machine:~$ ls
 公共的   图片            下载   Hello.java   VMwareTools-10.3.22-15902021.tar.gz
 模板    '未命名 1.odp'   音乐   pp.py        vmware-tools-distrib
 视频     文档            桌面   snap
```
命令`ls`默认不列出文夹中的隐藏文件，在Linux中，隐藏文件名以”.“开头。如果要将隐藏文件列出，那么要给命令加上参数`-a`。
```
yuzl@yuzl-virtual-machine:~$ ls -a
 .               下载            .gnupg            .ssh
 ..              音乐            Hello.java        .sudo_as_admin_successful
 公共的          桌面            .local            .viminfo
 模板            .bash_history   .mozilla          VMwareTools-10.3.22-15902021.tar.gz
 视频            .bash_logout    pp.py             vmware-tools-distrib
 图片            .bashrc         .profile          .Xauthority
'未命名 1.odp'   .cache          .python_history   .YY.txt.swp
```
下面是一些`ls`命令的参数：
短参数|长参数|作用
-|-|-
-a|--all|不隐藏任何以. 开始的项目
-A|--almost-all|列出除.及..的项目
-l||使用长格式输出项目
-d|--directory| 通常，如果指定了目录名，ls命令会列出这个目录中的内容，而不是目录本身。把这个选项与-l 选项结合使用，可以看到所指定目录的详细信息，而不是目录中的内容。
-F|--classify| 这个选项会在每个所列出的名字后面加上一个指示符。例如，如果名字是目录名，则会加上一个’/’ 字符。
-h|--human-readable|当以长格式列出时，以人们可读的格式，而不是以字节数来显示文件的大小。
-r| --reverse| 以相反的顺序来显示结果。通常，ls 命令的输出结果按照字母升序排列。
-S|| 命令输出结果按照文件大小来排序。
-t|| 按照修改时间来排序。
关于文件名的重要规则
1. 以“.” 字符开头的文件名是隐藏文件。这仅表示，ls 命令不能列出它们，用ls
-a 命令就可以了。当你创建帐号后，几个配置帐号的隐藏文件被放置在你的家
目录下。稍后，我们会仔细研究一些隐藏文件，来定制你的系统环境。另外，
一些应用程序也会把它们的配置文件以隐藏文件的形式放在你的家目录下面。
2. 文件名和命令名是大小写敏感的。文件名“File1”和“file1”是指两个不同的
文件名。
3. Linux 没有“文件扩展名”的概念，不像其它一些系统。可以用你喜欢的任何
名字来给文件起名。文件内容或用途由其它方法来决定。虽然类Unix 的操作
系统，不用文件扩展名来决定文件的内容或用途，但是有些应用程序会。
4. 虽然Linux 支持长文件名，文件名可能包含空格，标点符号，但标点符号仅限
使用“.”，“－”，下划线。最重要的是，不要在文件名中使用空格。如果你想表
示词与词间的空格，用下划线字符来代替。过些时候，你会感激自己这样做。

### <font color="#008000">2.3&nbsp;&nbsp;操作文件及文件夹</font>
&nbsp;&nbsp;和Windows等其他系统一样，Linux系统中也可以操作文件及文件夹。在日常工作中对文件及文件夹的操作是非常重要的。无论你是复制、移动、删除、重命名文件及文件夹都可以通过命令来实现。
#### <font color="#008000">2.3.1&nbsp;&nbsp;通配符</font>
&nbsp;&nbsp;在开始使用命令之前，我们需要介绍一个使命令行如此强大的shell特性。因为shell频繁地使用文件名，shell提供了特殊字符来帮助你快速指定一组文件名。这些特殊字符叫做通配符。使用通配符（也以文件名代换著称）允许你依据字符的组合模式来选择文件名。下表列出这些通配符以及它们所选择的对象：

通配符|通配符意义
-|-
*| 匹配任意多个字符（包括零个或一个）
? |匹配任意一个字符（不包括零个）
[characters]| 匹配任意一个属于字符集中的字符
[!characters]| 匹配任意一个不是字符集中的字符
[[:class:]]| 匹配任意一个属于指定字符类中的字符

最常使用的字符类：
字符类|字符类意义
-|-
[:alnum:]| 匹配任意一个字母或数字
[:alpha:]|匹配任意一个字母
[:digit:]| 匹配任意一个数字
[:lower:]| 匹配任意一个小写字母
[:upper:]|匹配任意一个大写字母
普遍使用的字符类
借助通配符，为文件名构建非常复杂的选择标准成为可能。下面是一些类型匹配的范例:
模式|匹配对象
-|-
*| 所有文件
g*| 文件名以“g”开头的文件
b*.txt| 以”b” 开头，中间有零个或任意多个字符，并以”.txt” 结尾的文件
Data???| 以“Data”开头，其后紧接着3 个字符的文件
[abc]*| 文件名以”a”,”b”, 或”c” 开头的文件
BACKUP.[0-9] [0-9][0-9]|以”BACKUP.” 开头，并紧接着3 个数字的文件
[[:upper:]]*| 以大写字母开头的文件
[![:digit:]]*| 不以数字开头的文件
下面是一些实际环境中使用的例子：<br>
列出根目录下所有的文件及文件夹：
```
yuzl@yuzl-virtual-machine:/$ ls *
swapfile

bin:
'['                                   min12xxw
 aa-enabled                           minfo
 aa-exec                              mkdir
...
```
列出/usr/bin目录下所有以ac开头的文件：
```
yuzl@yuzl-virtual-machine:/usr/bin$ ls -l ac*
-rwxr-xr-x 1 root root 22912 3月   5  2020 aconnect
-rwxr-xr-x 1 root root 19016 11月 28  2019 acpi_listen
```
列出/usr/bin目录下所有以大写字母开头的文件及文件夹：
```
yuzl@yuzl-virtual-machine:/usr/bin$ ls -l [[:upper:]]*
lrwxrwxrwx 1 root root      11 10月 13 05:03 GET -> lwp-request
lrwxrwxrwx 1 root root      11 10月 13 05:03 HEAD -> lwp-request
lrwxrwxrwx 1 root root      11 10月 13 05:03 POST -> lwp-request
```
#### <font color="#008000">2.3.2&nbsp;&nbsp;创建目录</font>
&nbsp;&nbsp;在Linux系统中使用命令`mkdir`创建命令，下面的例子将在用户家目录中创建一个名为”test“的文件夹。
```
yuzl@yuzl-virtual-machine:~$ ls
 公共的   图片            下载   Hello.java   snap
 模板    '未命名 1.odp'   音乐   Hello.py     VMwareTools-10.3.22-15902021.tar.gz
 视频     文档            桌面   pp.py        vmware-tools-distrib
yuzl@yuzl-virtual-machine:~$ mkdir test
yuzl@yuzl-virtual-machine:~$ ls
 公共的  '未命名 1.odp'   桌面         snap
 模板     文档            Hello.java   test
 视频     下载            Hello.py     VMwareTools-10.3.22-15902021.tar.gz
 图片     音乐            pp.py        vmware-tools-distrib
```
使用该命令也可以同时创建多个文件夹：
```
yuzl@yuzl-virtual-machine:~$ mkdir test1 test2
yuzl@yuzl-virtual-machine:~$ ls
 公共的  '未命名 1.odp'   桌面         snap    VMwareTools-10.3.22-15902021.tar.gz
 模板     文档            Hello.java   test    vmware-tools-distrib
 视频     下载            Hello.py     test1
 图片     音乐            pp.py        test2
```
#### <font color="#008000">2.3.3&nbsp;&nbsp;移动或重命名文件及目录</font>
&nbsp;&nbsp;重命名文件可以使用命令`mv`来实现：<br>
语法格式：<br>
```
mv filename1 filename2
```
下面是使用示例:
```
yuzl@yuzl-virtual-machine:~/test$ ls
Hello.java
yuzl@yuzl-virtual-machine:~/test$ mv Hello.java HelloWorld.java
yuzl@yuzl-virtual-machine:~/test$ ls
HelloWorld.java
```
该命令也可以修改目录名：
```
yuzl@yuzl-virtual-machine:~/test$ ls
HelloWorld.java  yuh
yuzl@yuzl-virtual-machine:~/test$ mv yuh yul
yuzl@yuzl-virtual-machine:~/test$ ls
HelloWorld.java  yul
```
#### <font color="#008000">2.3.3&nbsp;&nbsp;移动文件及目录</font>
&nbsp;&nbsp;Linux系统中移动文件及目录同样使用命令mv，语法格式：
```
mv filename directory
```
```
yuzl@yuzl-virtual-machine:~/test$ ls 
yul
yuzl@yuzl-virtual-machine:~/test$ mv /home/yuzl/HelloWor* /home/yuzl/test
yuzl@yuzl-virtual-machine:~/test$ ls
HelloWorld.java  yul
```
移动目录：
```
yuzl@yuzl-virtual-machine:~/test$ ls
HelloWorld.java  yul
yuzl@yuzl-virtual-machine:~/test$ mv /home/yuzl/test1 /home/yuzl/test
yuzl@yuzl-virtual-machine:~/test$ ls
HelloWorld.java  test1  yul
```
