# Linux基础知识和命令

# 1.为什么要学习Linux，Linux在工作中用来干什么？

1. Linux在工作中主要用于环境部署（程序代码包  .jar  .war）-->部署到服务器上-->有页面或者是app端
2. 使用服务器获取日志，协助定位问题

# 2.计算机组成

## 2.1硬件

- 显示器 、鼠标 、键盘 、主机（主板  内存条   网卡  显卡 声卡   CPU：核   电源   风扇）

## 2.2操作系统

1. PC端：x86   32位操作系统，x86-64  64位操作系统
2. 手机端：arm 32位操作系统，arm64  64位操作系统
3. Windows、MacOS、dos、Linux、Andorid、ios、鸿蒙
4. 语言：c语言 、java语言、python-->解释器或者是编译器-->转换成计算机能识别的二进制代码程序代码-->指令      数据

## 2.3应用软件

- web端-->app端（qq、微信、淘宝、美团、手机银行app）-->小程序（微信小程序、支付宝小程序）-->嵌入式设备与App交互


# 3.Linux操作系统

1. Linux内核（由linus开发出）-->放到开源平台-->图标（企鹅）、名字linux，没有图形化界面，纯命令界面

2. 小巧、功能全、安全、多用户多任务的操作系统

3. 发行版本：RedHat、Debian、Arch、openSUSE、CentOS、Ubuntu等

4. 客户端系统：Windows、Android、IOS、Harmony、个人用Linux

5. 服务端系统：99%Linux

6. 服务器：365天*24小时运行、服务器的本质也是电脑，是功能更加强大的电脑

7. 学校一般自建服务器（托管官网、学生数据等）

8. 中小型公司租云服务器：阿里云、腾讯云、百度云

9. 大型公司自建服务器，提供云服务器资源

# 4.电脑装多系统

- VM虚拟机：在宿主机中独立出一块空间（CPU，内存，网卡，显卡，声卡）
- 镜像文件：后缀为.iso的操作系统文件

# 5.软件的安装

-   安装的路径中不要出现中文，或者是特殊符号   it-install(错误示范)

-   安装路径中只能有字母或下划线

-    D:\it_install、D:\vm_install

# 6.远程连接、换源、安装软件包

## 6.1使用`ip address`or`ifconfig`命令查看IP地址

## 6.2如果不能上网，解决办法？

```shell
cd /etc/sysconfig/network-scripts
vi ifcfg-ens33#后半网卡名可不同
```
-   进入后将光标移动到最下面，然后输入`i`

-   将最后一行的no修改为yes，再点击键盘左上角的ESC，输入`:wq!`再按回车（按ZZ也可）

## 6.3如果源不可用，解决办法？

```shell
#CentOS7换源
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```
## 6.4出现command  not  found如何解决？

  - 尝试安装使用的命令、例：`yum install ifconfig`
  - 提示包不存在可使用yum search 命令、例：`yum search ifconfig`

## 6.5yum的作用

```shell
#在线下载并安装
yum search 安装包的包名
yum -y install 安装包名
```

## 6.6linux获取文件

1. 使用ftp进行上传
2. 在linux使用rz命令
3. 在线下载

```shell
wget  [URL] --->文件保存为原始文件名
curl -O [URL] --->文件保存为原始文件名
curl -o [filename] [URL] --->文件保存并重命名为[filename]
```

# 7.Linux文件管理系统

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

# 8.Linux基本命令

## 8.1目录相关的命令

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

##  8.2编写路径

-  绝对路径：一次到达，从根目录开始写、例：`/etc/ssh/sshd_config`
-  相对路径：相对与当前目录而言、例：`../home/hanli`(假设当前目录为root)

## 8.3文件相关的命令

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
nl 文件名 #带行号显示文件的所有内容
'查看一个文件的第3行到第5行' sed -n 'n1,n2p' 文件名  #n1和n2代表的是两个数字
'查看一个文件的第3行到第5行' head -5 文件名 | tail -3
'查看文件的第5行' sed -n '5p' 文件名
```

## 8.4vi/vim编辑器

- vi编辑器模式：命令模式，末行模式，编辑模式
- 默认进入的是命令模式（只读）-->`i`或`a`或`o`-->编辑模式：输入内容
- 编辑模式-->按键盘左上角`ESC`-->命令模式
- 命令模式下-->输入`:`-->末行模式：保存退出、强制退出、保存不退出

```shell
vi 文件名
'打开一个文件，并把光标定位到161行' vi +161 文件名

'命令模式下的命令'
大写G '跳转到行尾'
小写gg '跳转到行首'
ngg 'n代表任意数字,第n行行首'
yy '复制一行'
nyy '复制n行'
p '粘贴'
dd '删除'
ndd '删除n行'
大写ZZ '保存并退出'

'末行模式下的命令'
:set number '显示行号'
:set nonumber '取消行号'
:wq '保存退出'
:q! '强制退出'
:wq! '保存并强制退出'
:1,$s/旧字符/新字符/g '把第一行到最后一行的所有的旧字符修改为新字符'
:1,3s/旧字符/新字符/g '把第一行到第三行的所有的旧字符修改为新字符'
:4s/旧字符/新字符/g '把第四行的所有的旧字符修改为新字符'
:1,$s/旧字符/新字符 '把第一行到最后一行的第一个旧字符修改为新字符'
```

## 8.5打包压缩相关的命令

```shell
#打包：可以对文件也可以对文件夹进行打包
tar -cvf T.tar 要打包的文件/文件夹 'c：create f：file v：verbose 过程' '打包'

#压缩：压缩只能对文件，对包进行压缩
gzip 文件 '创建压缩包'
gunzip xxx.gz '默认解压到当前目录'
gzip -d xxx.gz '解压缩，解压成功后删除xxx.gz文件'
zip 文件 '创建压缩包'
unzip xxx.zip '默认解压到当前目录'

#打包压缩：
tar -czvf T.tar.gz 文件 文件夹1 文件2 文件夹2 'z：gzip 压缩' '创建压缩包'
tar -xzvf T.tar.gz '默认解压到当前目录'
tar -tzvf T.tar.gz '查看压缩文件'
tar -xzvf T.tar.gz -大写C 目录 '解压缩到指定的目录'
```

## 8.6进程服务相关的命令

### 8.6.1程序和进程的区别？

- 程序是死的
- 进程：正在运行的程序(动态的)
- 杀进程而不是杀程序

```shell
'关闭防火墙的命令' systemclt stop firewalld #d代表的是进程，暂时关闭，重启防火墙默认开启
systemctl restart firewalld #重启防火墙服务
systemctl disable firewalld #关闭防火墙开机自启
systemctl enable firewalld #防火墙开机自启(默认开启)
systemclt start mysqld.service #启动MySQL服务
systemctl start httpd #启动MySQL服务

'查看进程' ps -ef | grep tomcat
| 管道符,分割开两个命令，把前一个命令处理的结果交给后面一个命令继续处理
grep 过滤查找

'杀进程' kill -9 pid
```

## 8.7权限相关的命令

### 8.7.1用户

**Linux系统中有两类用户**

- 一类是管理员用户 root /root [root@localhost opt]# root用户的标识符 #
- 一类是普通用户 xiaowang /home [xiaowang@localhost opt]$   普通用户的标识符  $

```shell
'创建用户' useradd 用户名
'修改用户密码' passwd 用户名
'切换用户' su 用户名 '高级别切换到普通用户不需要输入密码，同级别的或者是低级别切换到高级别是需要输入密码'
'删除用户' userdel 用户名
'删除用户及相应的信息' userdel -r 用户名
'用户的信息存放在' /etc/passwd   
				xiaoming:x:1000:1001::/home/xiaoming:/bin/bash
				用户名:密码:用户id:组ID:用户的家目录:shell环境
```

### 8.7.2组

```shell
'创建组' groupadd 组名
'删除组' groupdel 组名 '不能删除有用户的组'
'组的信息存放在' /etc/group
			  xiaoming:x:1001:
			  组名：组密码：组ID
```

**Linux系统的权限管理机制：组**

- Linux系统中的用户不能独立于组而存在，每一个用户都有一个主属组；权限是通过组来管理，赋予权限给某一个组，该组的用户就拥有了相应的权限，如果取消了该组响应的权限，该组的用户就取消了用户的权限
- 创建一个组的时候，如果你没有给这个用户指定组，系统会自动的创建一个和这个用户名同名的组，然后把这个用户添加到这个组中

```shell
# 创建一个用户并确定属组
useradd -g 组id 用户名
```

### 8.7.3权限

- Linux系统是一个多用户多任务的操作系统，安全，对每一个文件或者文件夹都管理了权限
- Linux系统中的权限是针对文件或者是文件夹的权限，对系统中的每一个文件或者文件夹都涉及到了权限

**权限**：组来管理权限
**对于一个文件或者文件夹而言**

- 文件的所有者        这个文件或者文件夹是谁创建者
- 文件的所属组        这个文件的所有者属于哪个组，这个文件就属于哪个组
- 文件的其他组        不在所属组之外的都叫其他组

`rwx-r-x-r-x`：所有者的权限--所属组的权限--其他组的权限
**对文件而言**

```shell
读：查看 (cat head tail)
写：编辑 (echo '' > 文件)
执行：可以运行文件 (./zbox start、sh startup.sh)
```

**对文件夹而言**

```shell
读:读取查看文件夹中的内容 ls ls-a
写：可以在文件夹中创建文件夹创建文件复制剪切
执行:进入这个文件文件 cd
```

### 8.7.4修改权限

**权限的数字： `r 读 4` `w  写  2` `x  执行 1`**

#### 方法一

**数字法修改权限**：4+2+1

```shell
第一个数字代表的是所有者的权限，第二个数字代表的是所在组的权限，第三个数字是其他组的权限
chmod 777 文件名 '给所有用户赋予读写执行权限'
```

#### 方法二

通过字母来修改权限   u   所有者   g 所在组     o 其他组    a（all）所有用户

```shell
chmod u=rwx 1.txt
chmod u-r 1.txt
chmod a=r 1.txt
```

## 8.8其他的常用命令

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
clear '清空终端屏幕'
man 命令 '查看帮忙命令' = 命令 --help
```

## 8.9常见文件后缀

```shell
.exe  ---可执行
.iso  ---镜像文件
.bat  ---windoes中可执行文件
.sh   ---Linux中可执行文件
.xml  ---配置文件
```

# 9.杂

## 9.1项目组成员

1. 项目经理
2. 产品经理（BA）
3. 开发
4. 概要设计：实时  定时
5. 详细设计
6. 测试
7. DBA
   - 数据-----》表（字段长度）---------》数据库
   - 在项目开始做之间，就会做好数据字典，项目中一共需要多少张表，每一张表存储哪一些字段的数据
   - 表与表之间怎么关联

## 9.2环境

- 测试环境:   http://ip地址
- 生成环境：上线之后客户真实使用的环境    http：//www.taobao.com
  - SIT；测试环境    构造很多的数据    脏数据  异常数据
    电商项目订单     添加商品都购物车---付款---订单
  - UAT：用户验收环境
    taobao项目组的测试     zhanghao  1亿

- 部署环境：  测试环境的部署    测试工程师   第一次部署环境 root   ： jdk  tomcat  数据库 

  - 发包：
  - 生产环境的部署    很有经验的老的开发
  
## 9.3日志分析
  1. anr   crash    app产生的中间      app的客户端的日志
  2. 手机中的指定的文件中找    /data/anr
  3. 日志    服务器下面logs

4. 测试小流程

  - 开发  前端开发 A B    后端开发  a  b
  - 开发人员分配   登录  A   a
  - 测试人员分配 测试任务   登录  注册

5. 发现了bug---》提交给谁？判断是前端的bug还是后端的bug？

  - APP端
    - Andorid  sdk   
    - 安装了模拟器        模拟器相对于手机，在手机上操作app
    - adb命令：adb  shell  monkey  -p  包名 1000
      - adb logcat
      - adb  shell：手机本地
        cd   /data/anr
  - web端 网页 http://www.baidu.com
    - 金融项目环境
    - 偶现的bug ，不能直接的复现这些操作 ，去打印日志协助分析问题
    - 日志文件一般会展示所有的异常，大概异常发送的时间点 2:30  -4:30
    - 2024-5-12   14:02   XXXXX

# 10.DD命令

`dd`命令是Unix和Linux系统中一个非常强大的工具，用于转换和复制文件。以下是如何使用`dd`命令的一些基本方法：

## 10.1基本语法

```shell
dd if=<输入文件> of=<输出文件> [选项]
```

- `if`：指定输入文件名或设备名。默认为标准输入(stdin)。
- `of`：指定输出文件名或设备名。默认为标准输出(stdout)。
- `[选项]`：各种可选参数，用于控制复制行为。

## 10.2常用选项

- `bs=块大小`：指定读写的块大小，如`bs=4M`。默认为512字节。
- `count=块数`：指定要复制的块数，如`count=10`。
- `skip=块数`：在读取输入文件之前跳过的块数，如`skip=5`。
- `seek=块数`：在写入输出文件之前跳过的块数，如`seek=5`。
- `conv=转换列表`：指定数据转换方式，如`conv=sync`确保同步模式，`conv=noerror`忽略读写错误等。
- `status=LEVEL`：控制状态输出的详细程度，如`status=progress`会显示复制进度。

## 10.3示例

- **复制文件**：将一个文件复制到另一个文件。

  ```shell
  dd if=/path/to/source_file of=/path/to/destination_file
  ```

- **备份磁盘分区**：将一个磁盘分区备份到一个镜像文件。

  ```shell
  dd if=/dev/sda1 of=/path/to/backup.img
  ```

- **恢复磁盘分区**：将镜像文件恢复到磁盘分区。

  ```shell
  dd if=/path/to/backup.img of=/dev/sda1
  ```

- **创建镜像文件**：创建一个指定大小的镜像文件，内容全为零。

  ```shell
  dd if=/dev/zero of=imagefile.img bs=1G count=10
  ```

- **制作启动盘**：将ISO文件写入U盘，制作启动盘。

  ```shell
  dd if=/path/to/ubuntu.iso of=/dev/sdb bs=4M status=progress
  ```

- **擦除硬盘数据**：使用随机数据覆盖整个硬盘，确保数据无法恢复。

  ```shell
  dd if=/dev/urandom of=/dev/sda bs=4M
  ```

> [!WARNING]
> - 使用`dd`命令时需要谨慎，错误的操作可能会导致数据丢失或系统损坏。在执行涉及磁盘操作的命令前，最好先进行备份。
> - 部分操作可能需要root权限，如备份和恢复磁盘分区等。
