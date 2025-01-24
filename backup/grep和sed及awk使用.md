## 一、shell环境与常用命令

### 1、Linux下有许多shell环境

```shell
1、Bash (Bourne Again Shell)：最广泛使用的 shell，功能强大且兼容 Bourne shell (sh)。

2、Zsh (Z Shell)：提供更高级的功能，如更强大的补全和主题支持。

3、Fish (Friendly Interactive Shell)：以易用性和交互性为重点，提供丰富的默认功能和用户友好的提示。

4、Dash (Debian Almquist Shell)：轻量级的 shell，通常用于系统脚本，速度快但功能较少。

5、Ksh (Korn Shell)：具有许多编程功能，兼容 Bourne shell 和 Korn shell 的增强版本。
```

### 2、.sh脚本的运行

```shell
touch test.sh
vim test.sh
写入
"#!/bin/bash
 echo 'hello world!'"
chmod 744 test.sh & ./test.sh
/bin/sh test.sh #会让第一行注释失效
```

### 3、Linux常用命令

```shell
ls #列出目录
cd #切换目录
pwd #显示当前目录
mkdir #创建一个空文件夹
rmdir #删除一个空文件夹
mv #移动文件或文件夹，也可以更改文件或文件夹名
cp #复制文件或文件夹
rm #删除文件或文件夹
```

### 4、文件属性、赋权

```shell
-rwxr-xr-x 1 root root    29496 Aug 11 17:38  aria2.sh
#本用户 用户组 其他对这个文件的权限
#read是4、write是2、execute（执行）是1
#赋当前用户的权为读、写、执行，其他无权限
chmod 700 aria2.sh
```

### 5、网络和性能命令

#### 1、ping命令

```shell
ping www.baidu.com -c 4 -i 10
-c 4#四次停止
-i 10#每次ping间隔10s
```

#### 2、netstat 命令

```shell
netstat #打印Linux网络系统的状态信息
-t #列出所有tcp
-u #列出所有udp
-l #只显示监听端口
-n #以数字形式显示地址和端口号
-p #显示进程的pid和名字
#一般来说 使用 netstat -ntpl查看tcp的端口、地址和内容
```

#### 3、显示性能与进程

```shell
top #显示动态的性能与进程
ps -aux #显示一个快照的性能与进程
```

## 二、三剑客与管道符

### 1、管道符与grep（过滤）

#### a、管道符

```shell
 | #把前面的输出结果变成后面的条件
#1.txt的内容如下：
world
adb
adb shell
shell
nginx
hello
hanli
hello world
#命令
cat 1.txt | grep 'hello'
#结果
hello
hello world
```

#### b、grep

```shell
grep [options] PATTERN [file]
PATTERN：要搜索的模式或正则表达式。
file：要搜索的文件名。如果省略此参数，grep 将从标准输入读取数据。
#常用选项
-i：忽略大小写。
grep -i "pattern" file.txt

-v：反转匹配，显示不匹配模式的行。
grep -v "pattern" file.txt

-r 或 -R：递归搜索目录中的文件。
grep -r "pattern" /path/to/directory

-l：仅显示匹配模式的文件名。
grep -l "pattern" *.txt

-n：显示匹配行的行号。
grep -n "pattern" file.txt

-c：显示匹配的行数。
grep -c "pattern" file.txt

-H：在输出中包含文件名。
grep -H "pattern" file.txt

-w：仅匹配整个单词。
grep -w "pattern" file.txt

-e：指定多个模式（可以多次使用）。
grep -e "pattern1" -e "pattern2" file.txt

-o：仅输出匹配的部分。
grep -o "pattern" file.txt

--color：高亮显示匹配部分（通常默认开启）。
grep --color "pattern" file.txt
```

### 2、正则表达式

```shell
\b单词\b#匹配这个单词
\b单词\b.*\b另一个单词\b#匹配有前一个单词以及后一个单词的一群单词，不管中间是什么
0\d{2}-\d{8}#0开头+两位数+'-'+后面八位数
```

| 符号    | 描述                           | 等价字符集示例                    |
| :------ | :----------------------------- | :-------------------------------- |
| `.`     | 匹配任意单个字符（换行符除外） | N/A                               |
| `^`     | 匹配输入字符串的开始           | N/A                               |
| `$`     | 匹配输入字符串的结束           | N/A                               |
| `*`     | 匹配前面的子表达式零次或多次   | `(a)*` 匹配 "a" 出现0次或多次     |
| `+`     | 匹配前面的子表达式一次或多次   | `(a)+` 匹配 "a" 出现1次或多次     |
| `?`     | 匹配前面的子表达式零次或一次   | `(a)?` 匹配 "a" 出现0次或1次      |
| `{n}`   | 匹配确定的 n 次数              | `(a){3}` 匹配 "aaa"               |
| `{n,}`  | 至少匹配 n 次                  | `(a){2,}` 至少匹配 "aa"           |
| `{n,m}` | 匹配 n 到 m 次之间的次数       | `(a){1,3}` 匹配 "a" 到 "aaa"      |
| `[]`    | 匹配方括号内的任意字符         | `[aeiou]` 匹配任何元音字母        |
| `|`     | 逻辑或，匹配两个表达式之一     | `(a|b)` 匹配 "a" 或 "b"           |
| `\\`    | 转义特殊字符或表示特殊序列     | `\n` 匹配换行符                   |
| `()`    | 分组                           | `(ab)` 匹配 "ab" 作为一个整体     |
| `\d`    | 匹配任意数字                   | 等同于 `[0-9]`                    |
| `\w`    | 匹配任意字母数字字符           | 等同于 `[a-zA-Z0-9_]`             |
| `\s`    | 匹配任意空白符                 | 包括空格、制表符等                |
| `\b`    | 单词边界                       | 匹配 "abc" 中的 "ab" 和 "bc" 之间 |

### 3、sed

```shell
sed #流编辑器，一次处理一行内容
```
```shell
#基本语法
sed [options] 'command' file
command：指定要执行的 sed 命令。
```
```shell
#常用命令和选项
#替换（substitute）
基本语法：
sed 's/pattern/replacement/' file
示例：将文件中第一次出现的 "old" 替换为 "new"：
sed 's/old/new/' file.txt
替换所有匹配（使用 g 标志）：
sed 's/old/new/g' file.txt
仅替换第 N 次匹配（例如第 2 次）：
sed 's/old/new/2' file.txt
```
```shell
#删除行（delete）
删除特定行：
sed 'Nd' file
例如，删除第 3 行：
sed '3d' file.txt
删除匹配模式的行：
sed '/pattern/d' file.txt
```
```shell
#插入（insert）
在特定行前插入文本：
sed 'N i\text' file
例如，在第 3 行前插入 "Hello, World!"：
sed '3i\Hello, World!' file.txt
#追加（append）
在特定行后追加文本：
sed 'N a\text' file
例如，在第 3 行后追加 "Goodbye!"：
sed '3a\Goodbye!' file.txt
#替换（change）
用新的文本替换整行
sed 'N c\newtext' file
例如，将第 3 行替换为 "New content here"：
sed '3c\New content here' file.txt
```
```shell
#打印（print）
打印特定行：
sed -n 'Np' file
例如，打印第 3 行：
sed -n '3p' file.txt
多个命令（multiple commands）
在一个 sed 脚本中使用多个命令：
sed -e 'command1' -e 'command2' file
例如，删除第 2 行并在第 4 行后追加文本：
sed -e '2d' -e '4a\New appended text' file.txt
#正则表达式支持使用正则表达式进行复杂匹配和替换：
sed 's/[0-9]\{2\}/XX/g' file.txt
例如，将所有两个数字的序列替换为 "XX"。
将文件 data.txt 中的所有 "apple" 替换为 "orange"：
sed 's/apple/orange/g' data.txt
删除文件 file.txt 中包含 "error" 的所有行：
sed '/error/d' file.txt
在文件 notes.txt 的第 2 行后添加 "Important note!"：
sed '2a\Important note!' notes.txt
在文件 info.txt 的第 5 行前插入 "Header Line"：
sed '5i\Header Line' info.txt
只打印文件 log.txt 中的第 1 和第 3 行：
sed -n -e '1p' -e '3p' log.txt
```

### 4、awk

`awk` 是一种强大的文本处理工具，常用于处理和分析数据文件，如日志文件。它支持复杂的文本模式匹配和操作，可以用来执行条件判断、循环等编程逻辑。`awk` 的基本语法是：

```shell
awk '条件 {动作}' 文件名
```

例如，如果你想打印一个文本文件中所有包含单词 "error" 的行，可以使用以下命令：

```shell
awk '/error/ {print}' filename.txt
```

这里 `filename.txt` 是你要处理的文件名。`/error/` 是一个模式匹配，它匹配包含 "error" 的行。`{print}` 是一个动作，表示对于每个匹配的行执行打印操作。

**`awk` 的一些常用命令和功能包括：**

1. **打印特定列**：

   ```shell
   awk '{print $1}' filename.txt
   ```

   这将打印文件 `filename.txt` 中每行的第一个字段。

2. **打印多个列**：

   ```shell
   awk '{print $1 " " $2 " " $3}' filename.txt
   ```

   这将打印文件中每行的前三个字段。

3. **使用变量**：

   ```shell
   awk '{sum += $1} END {print sum}' filename.txt
   ```

   这将计算文件中第一列所有数值的总和。

4. **条件打印**：

   ```shell
   awk '$1 > 10 {print $1}' filename.txt
   ```

   这将打印第一列值大于10的所有行。

5. **模式匹配**：

   ```shell
   awk '/pattern/ {print}' filename.txt
   ```

   这将打印所有包含 "pattern" 字符串的行。

6. **使用正则表达式**：

   ```shell
   awk '/^[0-9]/ {print}' filename.txt
   ```

   这将打印以数字开头的所有行。

7. **字段分隔符**：

   ```shell
   awk -F: '{print $1}' filename.txt
   ```

   这将使用冒号作为字段分隔符，并打印每行的第一个字段。

8. **多条件**：

   ```shell
   awk '$1 > 10 && $2 < 20 {print $1, $2}' filename.txt
   ```

   这将打印第一列大于10且第二列小于20的所有行。

9. **循环**：

   ```shell
   awk '{for (i=1; i<=NF; i++) print $i}' filename.txt
   ```

   这将对文件中每行的每个字段进行循环并打印。

10. **格式化输出**：

    ```shell
    awk '{printf "%-10s %-10s\n", $1, $2}' filename.txt
    ```

    这将格式化输出，使第一列和第二列宽度为10个字符，左对齐。

11. **内置数组**：

    ```shell
    awk '{arr[$1]++} END {for (key in arr) print key, arr[key]}' filename.txt
    ```

    这将统计第一列中每个唯一值的出现次数。

12. **函数使用**：

    ```shell
    awk '{print length($0)}' filename.txt
    ```

    这将打印每行的长度。

`awk` 中的 `print` 命令是用来输出文本到标准输出（通常是终端或控制台）。在 `awk` 脚本中，`print` 是最常用的动作之一，因为它直接将数据展示给用户或将其写入文件。然而，`awk` 也提供了其他一些动作和函数，可以用来执行不同的任务，而不仅限于打印。

**以下是一些 `awk` 中除了 `print` 之外的其他常用动作和函数：**

1. **赋值**：给变量赋值。

   ```shell
   awk '{sum = sum + $1}' filename.txt
   ```

2. **条件语句**：基于条件执行不同的动作。

   ```shell
   awk '{if ($1 > 10) print $1}' filename.txt
   ```

3. **循环**：使用 `for` 循环迭代数组或执行重复动作。

   ```shell
   awk '{for (i = 1; i <= NF; i++) print $i}' filename.txt
   ```

4. **数组**：使用数组存储和操作数据。

   ```shell
   awk '{arr[$1]++} END {for (key in arr) print key, arr[key]}' filename.txt
   ```

5. **内置函数**：`awk` 提供了许多内置函数，如 `length()`, `toupper()`, `tolower()`, `split()`, `sprintf()` 等，可以对数据进行处理。

   ```shell
   awk '{print length($1)}' filename.txt
   ```

6. **模式匹配**：使用正则表达式进行模式匹配。

   ```shell
   awk '/^#/ {next}' filename.txt
   ```

7. **文件操作**：可以对多个文件进行操作。

   ```shell
   awk 'FNR==1 {print "File: " FILENAME} {print $1}' file1.txt file2.txt
   ```

8. **记录分隔符**：处理多行记录。

   ```shell
   awk 'BEGIN {RS=""; FS="\n"} {print $1}' filename.txt
   ```

9. **字段分隔符**：自定义字段分隔符。

   ```shell
   awk -F, '{print $1}' filename.csv
   ```

10. **记录和字段计数**：使用内置变量 `NR` 和 `NF` 来获取记录数和字段数。

    ```shell
    awk '{print NR " " NF}' filename.txt
    ```

`print` 命令之所以频繁出现，是因为它是最基础的输出方式。但是，`awk` 的强大之处在于它能够结合这些不同的元素来执行复杂的文本处理任务。

## 三、Bash编程语法

### 1、Bash变量命名规则

在 Bash 脚本编程中，变量命名需要遵循一些特定的规则，并且要避免与 Bash 的关键字和内置命令冲突。以下是整合后的命名规则和注意事项：

1. **变量名只能使用英文字母（a-z, A-Z）、数字和下划线，且不能以数字开头。**
2. **变量名不能有空格。**
3. **变量名不能使用标点符号。**
4. **不能使用 shell 里的关键字，如 `if`、`then`、`else`、`fi`、`for`、`while`、`case` 等。**
5. **变量名应该避免与 Bash 的内置命令冲突，例如 `alias`、`cd`、`echo`、`export` 等。**
6. **变量名区分大小写。** 例如，`Variable` 和 `variable` 是两个不同的变量。
7. **建议使用小写字母和下划线来命名变量，以提高代码的可读性。**
8. **避免使用太短或太通用的名称。** 例如，使用 `count` 而不是 `c`，使用 `filename` 而不是 `fn`。
9. **使用大写字母表示常量。** 习惯上，常量的变量名通常使用大写字母，例如 `PI=3.14`。

此外，Bash 脚本中的变量默认是字符串类型，即使赋值时看起来像数值，它们也会被视为字符串。因此，如果需要进行数值运算，可能需要使用 `declare` 或 `typeset` 命令来指定变量为整数类型。

**以下是一些主要的 Bash 关键字：**

- `case`：用于多条件分支结构。
- `do`：通常与 `for`、`while` 或 `until` 循环配合使用，开始一个代码块。
- `done`：结束循环或 `case` 结构。
- `elif`：条件语句中的“else if”分支。
- `else`：条件语句中的默认分支。
- `esac`：结束 `case` 结构。
- `fi`：结束 `if` 条件语句。
- `for`：开始一个循环结构。
- `function`：声明一个函数。
- `if`：开始一个条件语句。
- `in`：在 `for` 循环和 `case` 结构中使用，指定范围或模式。
- `select`：用于创建简单的菜单选择结构。
- `then`：条件语句中的“then”分支，跟随 `if` 或 `elif`。
- `until`：开始一个循环，直到条件为真时停止。
- `while`：开始一个循环，当条件为真时继续。

**除了这些关键字，还有一些特殊的符号和结构在 Bash 中具有特殊含义，例如：**

- `(( ... ))`：用于算术表达式的括号。
- `[[ ... ]]`：用于条件表达式的扩展测试。
- `{}`：用于分组命令或定义函数体。
- `!`：逻辑非操作符。
- `&&`：逻辑与操作符，用于连接命令，当第一个命令成功时执行第二个命令。
- `||`：逻辑或操作符，用于连接命令，当第一个命令失败时执行第二个命令。

**大于小于**

- `-eq`：等于
- `-ne`：不等于
- `-gt`：大于
- `-ge`：大于等于
- `-lt`：小于
- `-le`：小于等于

### 2、算数运算符

```shell
#!/bin/bash

a=10
b=5

# 加法
sum=$(expr $a + $b)
echo "加法结果: $sum"

# 减法
difference=$(expr $a - $b)
echo "减法结果: $difference"

# 乘法
# 注意：在expr中乘法需要使用星号(*)前加反斜杠(\)作为转义字符
product=$(expr $a \* $b)
echo "乘法结果: $product"

# 除法
# 注意：expr命令不支持直接的除法运算，这里使用除以1来实现除法
quotient=$(expr $a / $b)
echo "除法结果: $quotient"

# 取余数（模运算）
remainder=$(expr $a % $b)
echo "取余数结果: $remainder"

=为赋值、==为相等、!=为不相等
```

### 3、脚本参数传递

```shell
$0：脚本的名称。
$1, $2, ...：脚本的第1个、第2个等位置参数。
$#：传递给脚本的位置参数的数量。
$*：所有位置参数，合并成一个字符串。
$$：脚本当前运行的进程号。
$?：上一个命令的退出状态码，0表示无错误，其他表明有错误。

read之后不写变量则存在于REPLY
```

### 4、curl命令

`curl`是一个强大的命令行工具，用于传输数据，支持多种协议，包括HTTP、HTTPS、FTP等。

**下面是一些基本的`curl`用法：**

1. **获取网页内容**：

   ```shell
   curl http://example.com
   ```

2. **发送POST请求**：

   ```shell
   -d: 指定post请求体
   -X: 后面跟指定的请求方法，post、get等等
   curl -d "param1=value1&param2=value2" -X POST http://example.com/resource
   ```

3. **发送带有HTTP头的请求**：

   ```shell
   curl -H "X-My-Header: 123" http://example.com
   ```

4. **使用用户名和密码进行HTTP认证**：

   ```shell
   curl -u username:password http://example.com
   ```

5. **上传文件**：

   ```shell
   curl -F "file=@localfile.txt" http://example.com/upload
   ```

6. **下载文件**：

   ```shell
   curl -o filename.ext http://example.com/file
   ```

7. **使用cookie**：

   ```shell
   curl -b cookies.txt -c cookies.txt http://example.com
   ```

8. **跟随重定向**：

   ```shell
   curl -L http://example.com
   ```

9. **通过代理访问**：

   ```shell
   curl -x http://proxyserver:port http://example.com
   ```

10. **显示详细的调试信息**：

    ```shell
    curl -v http://example.com
    #-s 不输出错误信息和进度信息
    curl -s http://example.com
    ```

11. **使用SSL/TLS协议**：

    ```shell
    curl -k https://example.com # -k 忽略证书验证
    ```

12. **限制传输速度**：

    ```shell
    curl --limit-rate 1000 http://example.com
    ```

13. **使用自定义的CA证书**：

    ```shell
    curl --cacert cacert.pem https://example.com
    ```

14. **保存响应头信息**：

    ```shell
    curl -D headers.txt http://example.com
    ```

15. **设置超时时间**：

    ```shell
    curl --connect-timeout 10 http://example.com
    ```

