## 1.下载chrome_updater

根据架构下载，一般的电脑都是下amd64的，是在不知道建议先搜一下自己电脑cpu的架构。

[chrome_updater下载地址点击直达](https://github.com/libsgh/chrome_updater/releases)

> [!TIP]
>
> 使用这个之后，Chrome更新也只能用chrome_updater进行更新了

## 2.在D盘新建一个目录

|           1.chrome_updater.exe移入此目录，双击打开           |         2.直接点击下载安装，再点击创建快捷方式          |
| :----------------------------------------------------------: | :-----------------------------------------------------: |
| <img src="https://hantianzhun.github.io/blog/issues18.01.png"/> | <img src="https://hantianzhun.github.io/blog/issues18.01.png"/>  |

## 3.安装后在此目录会有App、Cache、Data目录

## 4.在快捷方式的目标处更改

```shell
"D:\Program Files\Chrome\App\chrome.exe" --user-data-dir="D:\Program Files\Chrome\Data" --user-cache-dir="D:\Program Files\Chrome\Cache"
```

> [!TIP]
>
> 可以将旧的data目录("C:\Users\usernme\AppData\Local\Google\Chrome\User Data")复制放到`D:\Program Files\Chrome\Data`，应该可以保数据

## 5.更改注册表以可以让其他软件调用

```cmd
# chrome
计算机\HKEY_CLASSES_ROOT\ChromeHTML.Q66WDMR3GVLKU6RCNLLAO6BLCI(点后面可能会没有)\shell\open\command下的默认更改为
"D:\Program Files\Chrome\App\chrome.exe" --user-data-dir="D:\Program Files\Chrome\Data" --user-cache-dir="D:\Program Files\Chrome\Cache" --single-argument %1

# http
计算机\HKEY_CLASSES_ROOT\http\shell\open\command下的默认更改为
"D:\Program Files\Chrome\App\chrome.exe" --user-data-dir="D:\Program Files\Chrome\Data" --user-cache-dir="D:\Program Files\Chrome\Cache" %1

# https
计算机\HKEY_CLASSES_ROOT\https\shell\open\command
"D:\Program Files\Chrome\App\chrome.exe" --user-data-dir="D:\Program Files\Chrome\Data" --user-cache-dir="D:\Program Files\Chrome\Cache" %1
```

