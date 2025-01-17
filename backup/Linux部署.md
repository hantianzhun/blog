# 1.禅道开源版

## 1.找到官网

- [禅道下载界面](https://www.zentao.net/downloads.html) [按住ctrl点击链接即可打开]

## 2.本地安装和在线安装

### 2.1本地安装

1. 在禅道下载界面选择linux+一键安装包，点击下载，文件在下载目录

2. 使用xftp或者rz传输到linux

3. 解压一键安装包

   ```shell
   tar -xzvf ZenTaoxxx.tar.gz -C /opt
   ```

### 2.2在线安装

1. 点击开源版的安装指南，找到linux一键安装包（推荐）

2. 使用wget进行下载(复制指南的)

   ````shell
   wget https://www.zentao.net/dl/zentao/18.5/ZenTaoPMS.18.5.zbox_64.tar.gz
   ````

3. 解压一键安装包

   ```shell
   tar -xzvf ZenTaoxxx.tar.gz -C /opt
   ```

## 3.启动禅道

> [!CAUTION]
> 运行成功之后若无法通过IP地址进行访问，检查系统防火墙
> systemctl status firewalld (查看防火墙运行状态)
> systemctl stop firewalld (暂时关闭)
> systemctl disable firewalld (关闭开机自启动)

### 3.1运行zbox

```shell
[root@localhost ~]# cd /opt
[root@localhost opt]# ls
btop  zbox
[root@localhost opt]# cd zbox/
[root@localhost zbox]# ./zbox start
 16:03:17.91 INFO  ==> Starting service with Apache port=80, MySQL port=3306, Redis port=6379...
```

## 4.启动问题

### 4.1端口占用：没有关程序(./zbox stop)导致

- 查看被占用的端口进程（ps -ef |grep mysql/apache）
- 查进程，注意被占用的是哪个进程

![](https://hantianzhun.github.io/blog/issues12.01.png)

![](https://hantianzhun.github.io/blog/issues12.02.png)

## 5.禅道的项目结构(集成项目软件包):php+apache+mysql

### 5.1zbox文件夹下的目录介绍

```shell
app：存放的是开发人员写的代码
bin：可执行文件的命令
etc：配置文件  端口号修改等等
tmp：临时文件
auth：作者相关文件
data：数据相关的文件
logs：日志文件
run：运行程序相关文件
```

# 2.JavaWeb项目(Tomcat)

- 组成 ：案例依赖：编程语言(java)  jdk +服务器（tomcat）+数据库（mysql）

## 2.1安装jdk

- 配置环境变量，验证是否部署成功  java -version
  - 详情可见：[01_Java环境变量配置](./01_Java环境变量配置.md) [按住ctrl点击链接即可打开]

## 2.2安装tomcat

- 使用ftp软件上传到linux服务器

- 解压缩启动服务，验证环境部署是否成功：在浏览器中输入地址[http://ip:端口]，出现tomcat页面√

### 2.2.1apache-tomcat-xx.xx.xx下所有目录详解

- bin ：可执行文件的命令文件，启动服务器在该目录

- conf：相关配置文件，如修改端口号(server.xml)等

- lib：动态库链接

- logs：日志文件，如出现异常时可查找日志发现问题所在

- tmp：临时文件

- weapps：开发人员写的程序代码包  （xxx.war）

- work：一些启动目录

### 2.2.2tomcat启动失败

#### 2.2.2.1防火墙没关

> [!CAUTION]
> 运行成功之后若无法通过IP地址进行访问，检查系统防火墙
> systemctl status firewalld (查看防火墙运行状态)
> systemctl stop firewalld (暂时关闭)
> systemctl disable firewalld (关闭开机自启动)

#### 2.2.2.2端口冲突，被占用 

```
ps -ef|grep tomcat(进程)
netstat -ano|grep 8080(端口号)
kill -9 进程号 
```

#### 2.2.2.3修改端口号

- 修改apache-tomcat-xx.xx.xx目录下的conf/server.xml文件

##### 2.2.2.3.1部分修改

```shell
1.# vim ./apache-tomcat-xx.xx.xx/conf/server.xml
2.# 使用vim进行搜索	/8080 并按回车（Enter）
3.# 修改未被注释为需要的端口号（不可与被占用的端口号一致）
4.# 保存退出
```

![](https://hantianzhun.github.io/blog/issues12.03.png)

##### 2.2.2.3.2全部修改
```shell
1.# vim ./apache-tomcat-xx.xx.xx/conf/server.xml
2.# 全部修改需要的端口号（不可与被占用的端口号一致）
	:%s/8080/9090/g '%'是整个文件，其他同下
	:1,$s/8080/9090/g ':'是进入命令模式1,$表示从第1行到$代表最后一行,"s"是substitute的缩写，表示替换操作,"/8080"是要被替换的文本,"g":替换每一行中所有匹配的8080
3.#保存退出
```

## 2.3安装并运行数据库

**示例：Centos7安装MySQL_5.6.51**

### 2.3.1安装MySQL

```shell
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm #获取MySQL5的yum源
rpm -ivh mysql-community-release-el7-5.noarch.rpm #安装MySQL5的yum源
'安装数据库' yum -y install mysql-server
```

### 2.3.2运行数据库

```shell
systemctl start mysqld #启动MySQL服务
```

#### 2.3.2.1MySQL无法启动

```shell
#解决办法一
ps -ef | grep mysql #筛选出包含MySQL字段的进程
netstat -ano | grep 3306 #筛选出使用3306端口的进程
kill -9 pid #强制关闭进程
systemctl start mysqld #启动MySQL服务

#解决办法二
systemctl stop mysqld #关闭MySQL服务
systemctl start mysqld #启动MySQL服务

#解决办法三--->最好使用前两种
reboot #重启服务器，MySQL默认开机自启
systemctl status mysqld #查看MySQL服务状态
```

### 2.3.2赋予权限并设置密码

```sql
mysql -u root -p #本机连接MySQL
show databases; #查看数据库
use mysql; #使用mysql数据库
select user,host,password from user; #查看数据库的用户名、host和密码
# 新建root用户，密码为123456，允许远程连接，赋予全部权限
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
# 刷新权限
FLUSH PRIVILEGES;
```

## 2.4远程连接数据库

**Navicat for MySQL v10为例**

![](https://hantianzhun.github.io/blog/issues12.04.png)

![](https://hantianzhun.github.io/blog/issues12.05.png)

## 2.5上传程序员写的代码

> [!CAUTION]
> 创建的数据库名称随意(非中文)，根据库字符集和表结构以及表数量、数据都与项目文档保持一致

### 2.5.1创建数据库，导入SQL文件

![](https://hantianzhun.github.io/blog/issues12.06.png)

![](https://hantianzhun.github.io/blog/issues12.07.png)

![](https://hantianzhun.github.io/blog/issues12.08.png)

![](https://hantianzhun.github.io/blog/issues12.09.png)

![](https://hantianzhun.github.io/blog/issues12.10.png)

### 2.5.2修改jdbc连接文件

![](https://hantianzhun.github.io/blog/issues12.11.png)

### 2.5.3上传jdbc+log4j文件

**上传到tomcat解压目录下的conf里面**

![](https://hantianzhun.github.io/blog/issues12.12.png)

### 2.5.4上传jar或war包

**上传到tomcat解压目录下的webapps里面**

![](https://hantianzhun.github.io/blog/issues12.13.png)

### 2.5.5浏览器访问http://ip:端口号/包名(在webapps查看) 

- 若有对应的文档里面有**项目访问URL**以文档优先、本文为辅助参考

## 2.6测试过程中发现bug

- 提交bug----->开发修改bug，提交一个新的xx.war------>测试拿到包，停止服务，把最新的xx.war复制到webapps目录下，启动服务，测试
- 在项目组中发包的频率：一般项目迭代周期： 二周