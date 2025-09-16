# 1.python项目部署

## 1.1下载Python安装包

- 在Python官网进行下载：[Python官网下载地址](https://www.python.org/downloads/) [按住ctrl点击链接即可打开]

## 1.2安装Python

![](https://hantianzhun.github.io/blog/issues14.01.png)

![](https://hantianzhun.github.io/blog/issues14.02.png)

> [!NOTE]
> 仅安装pip就可以

![](https://hantianzhun.github.io/blog/issues14.03.png)

- **点击install，完成后弹出的界面点击close即可**
- **在cmd里面输入`python -V`**

![](https://hantianzhun.github.io/blog/issues14.04.png)

## 1.3安装python需要的软件包

- 安装python包，在项目代码的路径(不要出现中文)

```cmd
安装第三方库
pip install -r 文件名.txt（文件里是需要安装的包列表）
pip  install  包名==版本号
使用镜像源进行包的安装（可以提升速度）
pip install -r requirements.txt -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
使用镜像源更新pip
python -m pip install -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple --upgrade pip
```

![](https://hantianzhun.github.io/blog/issues14.05.png)

> [!NOTE]
> 没error就是正常安装了包

- 查看包，`pip list`

![](https://hantianzhun.github.io/blog/issues14.06.png)

- python包安装成功，在项目路径使用`python xxx.py`即可

![](https://hantianzhun.github.io/blog/issues14.07.png)

# 2.Jmeter安装+使用

## 2.1Jmeter安装

- 在Apache官网进行下载：[Jemter下载地址](https://jmeter.apache.org/download_jmeter.cgi) [按住ctrl点击链接即可打开]

- 将下载的apache-jmeter-5.6.3.zip的压缩包解压到想要的目录即可（不可是中文路径）

## 2.2Windows的JDK是安装包

> [!CAUTION]
> 安装配置环境变量之后JDK改位置和环境变量，双击Jmeter会无法使用

- 配置环境变量，验证是否部署成功  java -version
  - 详情可见：[01_Java环境变量配置](https://blog.587459.xyz/post/11.html) [按住ctrl点击链接即可打开]

- 双击`安装目录/bin/ApacheJMeter.jar`即可打开中文界面的Jmeter

## 2.3Windows的JDK是压缩包

- 解压到想要的文件夹
- 配置环境变量，验证是否部署成功  java -version
  - 详情可见：[01_Java环境变量配置](https://blog.587459.xyz/post/11.html) [按住ctrl点击链接即可打开]

- 使用jmeter.bat启动
  1. 打开 JMeter 的安装目录，找到 `bin` 文件夹。
  2. 在 `bin` 文件夹中，找到并打开 `jmeter.properties` 文件。
  3. 在 `jmeter.properties` 文件中，找到以 `#language=` 开头的行。这行通常位于文件的开头部分。
  4. 去掉该行前面的 `#` 号，并将 `en` 改为 `zh_CN`。修改后的行应该类似于 `language=zh_CN`。
  5. 保存并关闭 `jmeter.properties` 文件。
  6. 重新启动 JMeter 软件，你会发现界面已经变成了中文，并且这种设置会永久生效。

- 在jmeter.bat同目录下新建一个`start.vbs`

```vbscript
#目录和Jmeter安装目录有关系
Set WshShell = CreateObject("WScript.Shell") 
WshShell.Run chr(34) & "D:\apache-jmeter-5.3\bin\jmeter.bat" & Chr(34), 0
Set WshShell = Nothing
```

- 可以给这个vbs文件创建一个快捷方式到桌面，对快捷方式也可以随意改名

- 双击这个vbs文件就可以打开中文界面的Jmeter
