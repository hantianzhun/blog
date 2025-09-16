## 1.下载JDK

首先我们需要下载 java 开发工具包 JDK，下载地址：[Oracle 中国 Java 下载](https://www.oracle.com/cn/java/technologies/downloads/) [按住ctrl点击链接即可打开]

在下载页面中根据自己的系统选择对应的版本，以 Window 64位系统为例：

![](https://hantianzhun.github.io/blog/issues11.01.png)

下载后双击安装，安装过程中可以自定义安装目录等信息，例如我们选择安装目录为`D:\Program Files\Java\jdk`

## 2.配置环境变量

### 2.1Windows系统

#### 2.1.1Windows7

安装完成后，右击"我的电脑"，点击"属性"，选择"高级系统设置"

![](https://hantianzhun.github.io/blog/issues11.02.png)

选择"高级"选项卡，点击"环境变量"

![](https://hantianzhun.github.io/blog/issues11.03.png)

出现如下图所示的画面：

![](https://hantianzhun.github.io/blog/issues11.04.png)

- 在 "系统变量" 中设置 3 项属性
- JAVA_HOME、PATH、CLASSPATH(大小写无所谓,但是要与path里面引用的一致)
- 若已存在则点击"编辑"，不存在则点击"新建"。

> **注意：**如果使用 1.5 以上版本的 JDK，不用设置 CLASSPATH 环境变量，也可以正常编译和运行 Java 程序。

**变量设置参数如下：**

- 变量名：`JAVA_HOME`
- 变量值：`D:\Program Files\Java\jdk`      ///要根据自己的实际路径配置

- 变量名：`CLASSPATH`
- 变量值：`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar; `    ///记得前面有个"."

- 变量名：`Path`
- 变量值：`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`

配置完成后，一直点击确定即可

#### 2.1.2Windows10/11

安装完成后，右击"我的电脑"，点击"属性"，选择"高级系统设置"

![](https://hantianzhun.github.io/blog/issues11.05.png)

选择"高级"选项卡，点击"环境变量"

<img src="./issues11.06.png"  />

出现如下图所示的画面：

![](https://hantianzhun.github.io/blog/issues11.07.png)

- 在 "系统变量" 中设置 3 项属性
- JAVA_HOME、PATH、CLASSPATH(大小写无所谓,但是要与path里面引用的一致)
- 若已存在则点击"编辑"，不存在则点击"新建"。

**变量设置参数如下：**

```shell
'变量名' JAVA_HOME
'变量值' D:\Program Files\Java\jdk     #要根据自己的实际路径配置

'变量名' CLASSPATH
'变量值' .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;   ##记得前面有个'.'

'变量名' Path 'Windows10Path变成一条一条，分开添加'
'变量值'
	%JAVA_HOME%\bin
	%JAVA_HOME%\jre\bin
```

> [!NOTE]
> Java17之后仅需要JAVA_HOME,Path里面仅%JAVA_HOME%\bin


#### 2.1.3测试JDK是否并配置安装成功

1、"开始"->"运行"，键入"cmd"；

2、键入命令: **java -version**、**java**、**javac** 几个命令，出现以下信息，说明环境变量配置成功

![](https://hantianzhun.github.io/blog/issues11.08.png)

![](https://hantianzhun.github.io/blog/issues11.09.png)

### 2.2Linux

#### 2.2.1CentOS7

```shell
# 使用vim打开配置文件
vim /etc/profile
# 添加以下内容
JAVA_HOME=/2020-5-28/jdk1.8.0_151 #路径与解压路径保持一致
JRE_HOME=/2020-5-28/jdk1.8.0_151/jre #路径与解压路径保持一致CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
# 更新配置文件
source /etc/profile
```

#### 2.2.2Debian12

**AI告诉我**

> 使用以下就可以满足大部分Java环境

```shell
# 使用vim打开配置文件
vim /etc/profile
# 添加以下内容
export JAVA_HOME=/opt/jdk1.8.0_431
export PATH=$JAVA_HOME/bin:$PATH
# 更新配置文件
source /etc/profile
```

#### 2.2.3测试JDK是否安装并配置成功

![](https://hantianzhun.github.io/blog/issues11.10.png)

![](https://hantianzhun.github.io/blog/issues11.11.png)

![](https://hantianzhun.github.io/blog/issues11.12.png)
