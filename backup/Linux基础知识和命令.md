## 1.为什么要学习Linux，Linux在工作中用来干什么？

1. Linux在工作中主要用于环境部署（程序代码包  .jar  .war）-->部署到服务器上-->有页面或者是app端
2. 使用服务器获取日志，协助定位问题

## 2.计算机组成

### 2.1硬件

- 显示器 、鼠标 、键盘 、主机（主板  内存条   网卡  显卡 声卡   CPU：核   电源   风扇）

### 2.2操作系统

1. PC端：x86   32位操作系统，x86-64  64位操作系统
2. 手机端：arm 32位操作系统，arm64  64位操作系统
3. Windows、MacOS、dos、Linux、Andorid、ios、鸿蒙
4. 语言：c语言 、java语言、python-->解释器或者是编译器-->转换成计算机能识别的二进制代码程序代码-->指令      数据

### 2.3应用软件

- web端-->app端（qq、微信、淘宝、美团、手机银行app）-->小程序（微信小程序、支付宝小程序）-->嵌入式设备与App交互


## 3.Linux操作系统

1. Linux内核（由linus开发出）-->放到开源平台-->图标（企鹅）、名字linux，没有图形化界面，纯命令界面

2. 小巧、功能全、安全、多用户多任务的操作系统

3. 发行版本：RedHat、Debian、Arch、openSUSE、CentOS、Ubuntu等

4. 客户端系统：Windows、Android、IOS、Harmony、个人用Linux

5. 服务端系统：99%Linux

6. 服务器：365天*24小时运行、服务器的本质也是电脑，是功能更加强大的电脑

7. 学校一般自建服务器（托管官网、学生数据等）

8. 中小型公司租云服务器：阿里云、腾讯云、百度云

9. 大型公司自建服务器，提供云服务器资源

## 4.电脑装多系统

- VM虚拟机：在宿主机中独立出一块空间（CPU，内存，网卡，显卡，声卡）
- 镜像文件：后缀为.iso的操作系统文件

## 5.软件的安装

-   安装的路径中不要出现中文，或者是特殊符号   it-install(错误示范)

-   安装路径中只能有字母或下划线

-    D:\it_install、D:\vm_install

## 6.远程连接、换源、安装软件包

### 6.1使用ip  addr命令查看IP地址

### 6.2如果不能上网，解决办法？

```shell
cd /etc/sysconfig/network-scripts
vi ifcfg-ens33#后半网卡名可不同
```
-   进入后将光标移动到最下面，然后输入"i"

-   将最后一行的no修改为yes，再点击键盘左上角的ESC，输入:wq!再按回车（按ZZ也可）

### 6.3如果源不可用，解决办法？

```shell
#CentOS7换源
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```
### 6.4出现command  not  found如何解决？

  - 尝试安装使用的命令、例：`yum install ifconfig`
  - 提示包不存在可使用yum search 命令、例：`yum search ifconfig`

### 6.5yum的作用

```shell
#在线下载并安装
yum search 安装包的包名
yum -y install 安装包名
```

## 7.Linux文件管理系统

```shell
#目录结构树
/etc     存放配置相关的文件      /etc/profile 环境变量 /etc/sysconfig/newrok-Scripts 网卡配置
/bin     存放的是可执行的命令文件     启动服务器
/sbin    存放的是root用户的可执行的命令文件
/root    是root用户的家目录
/home    是普通用户的家目录
/opt     存放的是临时文件相关的一些目录
/mnt     存放的是挂载文件相关的目录
```

## 8.Linux基本命令

### 8.1目录相关的命令

```shell
'创建文件夹' mkdir 文件夹名1
'创建多个文件夹' mkdir 文件夹1 文件夹2
'创建多层级的文件' mkdir -p A/B
'删除空文件夹' rmdir 文件夹名
'删除非空的文件夹' rm -r 非空目录名
'强制删除非空文件夹' rm -rf 非空的目录名 
'复制文件夹到指定的目录' cp -r 要复制的文件 复制到哪里去
'剪切文件到指定的目录' mv 要剪切的文件 剪切到哪里去
'重命名' mv 要重命名的文件夹/文件 新的文件夹/文件的名字
```

###  8.2编写路径

-  绝对路径：一次到达，从根目录开始写、例：`/etc/ssh/sshd_config`
-  相对路径：相对与当前目录而言、例：`../home/hanli`(假设当前目录为root)

### 8.3文件相关的命令

```shell
'创建文件' touch 文件1
'创建多个文件' touch f2 f3
'弹出提示信息删除文件' rm 文件名  
'强制删除文件' rm -f 文件名
'复制文件' cp 要复制的文件 复制到哪里去
'剪切文件' mv 要剪切的文件 剪切到哪里去
'覆盖写如内容到文件中'
echo "i love linux" > f1
echo "i love python" > f1
'追加写内容到指定的文件' echo "i love oracle" >> f1
```

```shell
'查看文件的内容'
cat 查看小文件
cat -n 文件名 #n不能代表代表任意数字
more 文件名
less 文件名 #按照屏幕比例显示内容，可以输入next进行翻页
head -n 文件名 #查看文件的前n行，n代表的任意数字
tail -n 文件名 #查看文件的最后n行，n代表任意数字
n 文件名 #带行号显示文件的所有内容
'查看一个文件的第3行到第5行' sed -n 'n1,n2p' 文件名  #n1和n2代表的是两个数字
'查看一个文件的第3行到第5行' head -5 文件名 | tail -3
'查看文件的第5行' sed -n '5p' 文件名
```

### 8.4打包压缩相关的命令

### 8.5进程服务相关的命令

### 8.6权限相关的命令

### 8.7其他的常用命令

```shell
cd 'change directory' '切换目录'
cd .. '切换到上一级目录'
cd ../.. '切换到上上一级目录'
cd / '切换到根目录'
cd ~ '切换到家目录'
cd - '切换到上次目录'
. '代表的是当前目录'
.. '代表的是上级目录'
ls 'list' '列出所有文件'
ls -a '显示所有的文件' #all: 所有的文件的包括了隐藏
ls -l '显示文件的详细信息'
ls -al '显示所有文件的详细信息'
pwd 'print work directory' '打印当前工作目录'
tree '树形结构展示当前目录下的所有文件或文件夹'
```