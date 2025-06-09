## 1.使用MySQL Installer安装

### 1.1下载MySQL Installer

| 1.[MySQL Installer下载链接(点击即可跳转)](https://dev.mysql.com/downloads/installer/),下载不带web的安装程序 |  2.点击下载，出现如下界面，点击最下面的no thank，会进行下载  |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.01.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.02.png" style="zoom:50%;" /> |

> [!TIP]
>
> 但是上述安装程序有部分版本没有，安装完会多一个MySQL Installer，强迫症狂喜
>

### 1.2MySQL Installer安装

|                      1.双击打开安装程序                      |          2.一般选Server only，想自定义就选最后一项           |         3.上一张图点击下一步，这张点击执行(Execute)          |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.03.png" style="zoom: 50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.04.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.05.png" style="zoom:50%;" /> |
| 4.这是成功了，若是失败一般是Windows的C++库的问题，装一个就好了 |               5.上一张图点击下一步，这一张也是               | 6.设置端口号和数据库配置，一般默认即可，若之前装过，需改动port |
| <img src="https://hantianzhun.github.io/blog/issues16.06.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.07.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.08.png" style="zoom:50%;" /> |
|     7.第一种需Navicat15+，改了加密方式，第二种则没有限制     |            8.输入root用户的密码，两遍，点击下一步            |             9.这个是注册开机服务项，一般默认即可             |
| <img src="https://hantianzhun.github.io/blog/issues16.09.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.10.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.11.png" style="zoom:50%;" /> |
| 10.点击执行(Execute)[这步前面不小心漏了一步，不重要，自用默认和第三项都行] |              11.全打上对勾就是好了，点击Finish               |               12.显示MySQL状态，点击下一步即可               |
| <img src="https://hantianzhun.github.io/blog/issues16.12.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.13.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.14.png" style="zoom:50%;" /> |
|             13.可查看安装log，点击Finish结束安装             |              14.安装后就是有一个MySQL Installer              |              15.可以单独卸载MySQL Installer解决              |
| <img src="https://hantianzhun.github.io/blog/issues16.15.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.16.png"  /> |                                                              |

## 2.使用MySQL Server.exe安装

### 2.1下载MySQL Server.exe

| 1.[MySQL Server.exe下载链接(点击即可跳转)](https://dev.mysql.com/downloads/installer/)，点击MSI进行下载 |              2.点击最下面的no thank，会进行下载              |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.17.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.18.png" style="zoom:50%;" /> |

> [!TIP]
>
> 有些版本有MySQL Sever的MSI安装程序，有些只有ZIP，ZIP看第三种方法

### 2.2MySQL Server.exe安装

#### 2.2.1MySQL 8

|                      1.双击打开安装程序                      |                      2.同意并点击下一步                      |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.19.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.20.png" style="zoom:50%;" /> |
| 3.一般选典型，也可选第二个自定义但只改安装路径，除非懂每一项的作用 |                          4.点击安装                          |
| <img src="https://hantianzhun.github.io/blog/issues16.21.png"  style="zoom:50%;"/> | <img src="https://hantianzhun.github.io/blog/issues16.22.png" style="zoom:50%;" /> |
|                5.默认勾选进行配置，点击Finish                |                         6.点击下一步                         |
| <img src="https://hantianzhun.github.io/blog/issues16.23.png"  style="zoom:50%;"/> | <img src="https://hantianzhun.github.io/blog/issues16.24.png" style="zoom:50%;" /> |
|                     7.可选数据库存放位置                     |                8.可配置类型和端口号，一般默认                |
| <img src="https://hantianzhun.github.io/blog/issues16.25.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.26.png" style="zoom:50%;" /> |
|                       9.root用户的密码                       |                    10.安装MySQL自启动服务                    |
| <img src="https://hantianzhun.github.io/blog/issues16.27.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.28.png" style="zoom:50%;" /> |
|          11.自行选择，和我一样也行(上面忘记截图了)           |                   12.示例数据库，自行选择                    |
| <img src="https://hantianzhun.github.io/blog/issues16.29.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.30.png" style="zoom:50%;" /> |
|                    13.点击执行，进行安装                     |                   14.安装完成，点击下一步                    |
| <img src="https://hantianzhun.github.io/blog/issues16.31.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.32.png" style="zoom:50%;" /> |
|               15.整个MySQL安装成功，点击Finish               |                                                              |
| <img src="https://hantianzhun.github.io/blog/issues16.33.png" style="zoom:50%;" /> |                                                              |

#### 2.2.2MySQL 5

|               1.在典型安装后，自动弹出这个弹窗               |                         2.点击下一步                         |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.34.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.35.png"/> |
|             3.默认勾选启动数据库配置，点击finish             |                         4.点击下一步                         |
| <img src="https://hantianzhun.github.io/blog/issues16.36.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.37.png" /> |
|   5.第一次安装选择和我一样的标准安装，第一种自定义自行摸索   |               6.安装MySQL服务，默认勾选自启动                |
| <img src="https://hantianzhun.github.io/blog/issues16.38.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.39.png" /> |
|          7.root用户密码，可勾选远程访问允许root用户          |                          8.点击执行                          |
| <img src="https://hantianzhun.github.io/blog/issues16.40.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.41.png"/> |
|                    9.安装完毕，点击finish                    |                                                              |
| <img src="https://hantianzhun.github.io/blog/issues16.42.png" style="zoom:50%;" /> |                                                              |

## 3.使用MySQL Server.ZIP安装

### 3.1下载MySQL Server.ZIP

| 1.[MySQL Server.zip下载链接(点击即可跳转)](https://dev.mysql.com/downloads/installer/)，点击ZIP进行下载，不要下debug |              2.点击最下面的no thank，会进行下载              |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.17.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.18.png" style="zoom:50%;" /> |

### 3.2MySQL Server.ZIP安装

> [!TIP]
>
> [https://wwwe.lanzouq.com/ik7yi2ydalgh 密码:3c5t](https://wwwe.lanzouq.com/ik7yi2ydalgh)
>
> 也可以看看上面Claude生成的教程，有5.7.44和8.x版本

#### 3.2.1解压和配置环境变量

|                    1.解压到想要存放的目录                    |                      2.配置系统环境变量                      |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.43.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.44.png"/> |

#### 3.2.2.A在MySQL 5解压目录新建my.ini

```ini
[mysqld]
# 设置mysql的安装目录
basedir="D:/mysql-5.7.44-winx64"
# 设置mysql数据库的数据的存放目录
datadir="D:/mysql-5.7.44-winx64/data"
# 设置默认使用的端口
port=3306
# 允许最大连接数
max_connections=200
# 允许连接失败的次数
max_connect_errors=10
# 服务端使用的字符集（5.7版本推荐utf8mb4）
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# MySQL 5.7 特有配置
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES

[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```

#### 3.2.2.B在MySQL 8解压目录新建my.ini

```ini
[mysqld]
# 设置mysql的安装目录
basedir="D:/mysql-8.4.5-winx64"
# 设置mysql数据库的数据的存放目录
datadir="D:/mysql-8.4.5-winx64/data"
# 设置默认使用的端口
port=3306
# 允许最大连接数
max_connections=200
# 允许连接失败的次数
max_connect_errors=10
# 服务端使用的字符集
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用"mysql_native_password"插件认证
default_authentication_plugin=mysql_native_password

[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4

[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```

#### 3.2.3 初始化数据库

```cmd
# 以管理员身份打开命令提示符，执行：

# 切换到mysql的bin目录（示例）
D:
cd D:/mysql-5.7.44-winx64/bin

# 初始化数据库（会生成临时密码）
mysqld --initialize --console
```

**重要：** 记录输出中的临时密码，类似：

```cmd
A temporary password is generated for root@localhost: kT7!mN9pQ2xR
```

#### 3.2.4安装 MySQL 服务

```cmd
# 继续在管理员命令提示符中执行：

# 安装MySQL服务
mysqld --install MySQL

# 设置开机自启
sc config MySQL start= auto

# 启动MySQL服务
net start MySQL
```

### 3.3首次登录和密码设置

#### 3.3.1登录MySQL

```cmd
mysql -u root -p

# 输入刚才记录的临时密码
```

#### 3.3.2修改root密码

```sql
-- 修改密码（将 'your_new_password' 替换为您的新密码）
ALTER USER 'root'@'localhost' IDENTIFIED BY 'your_new_password';

-- 刷新权限
FLUSH PRIVILEGES;

-- 退出
EXIT;
```

### 3.4验证安装

#### 3.4.1重新登录测试

```cmd
mysql -u root -p

# 使用新密码登录
```

#### 3.4.2查看版本信息

```sql
SELECT VERSION();
```

#### 3.4.3查看数据库

```sql
SHOW DATABASES;
```

## 4.使用Navicat连接MySQL

|                      1.打开Navicat软件                       |                      2.选择MySQL数据库                       |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues16.45.png" style="zoom:50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.46.png" style="zoom:50%;" /> |
|          3.连接名随意，输入root账户的密码，点击确定          |         4.即可看到默认的数据库，可新建数据库再创建表         |
| <img src="https://hantianzhun.github.io/blog/issues16.47.png" style="zoom: 50%;" /> | <img src="https://hantianzhun.github.io/blog/issues16.48.png" style="zoom:50%;" /> |

