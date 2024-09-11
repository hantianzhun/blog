# 一、本博客文章的发表

## 1.访问github

**访问[写作地址](https://github.com/hantianzhun/hantianzhun.github.io)，可以得到如下页面，此时最好先登录github账号。**

![1.png](https://wp-cdn.4ce.cn/v2/b4ff7c9e45871f76c9339.png)

## 2.打开Issues

**点击Issues，可以看到如下内容。**

![2.png](https://wp-cdn.4ce.cn/v2/88b774563940a237ffd83.png)

## 3.撰写

**点击New Issues即可看到如下页面，可按下图所示进行撰写。**

> [!TIP]
> 这里给一个我使用的[图床网站](https://wp-cdn.4ce.cn/)

![3.png](https://wp-cdn.4ce.cn/v2/45624a5550a011015d993.png)

## 4.重新编辑

**如果想要重新编辑之前写过的文章，点开自己之前的Issues，按下图所示进行即可。**

![4.png](https://wp-cdn.4ce.cn/v2/9cdfca4c59c7e56b1805c.png)

## 5.删除

**想要删除所写的文章，往下拉，在下面可以看到如下图所示，点击delete的按钮按提示操作即可。**

![5.png](https://wp-cdn.4ce.cn/v2/e60eff8fa613c8032e9d4.png)

# 二、Markdown语法

> [!NOTE]
> Markdown是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档，然后转换成结构化的HTML。

> [!IMPORTANT]
> 下面是一些基本的Markdown语法


## 1.标题

使用`#`来创建标题。一个`#`是最大的标题，六个`#`是最小的标题。

```
### 这是三级标题
```

### 这是三级标题

## 2.段落

段落之间用一个空行隔开。

## 3.字体样式

- 粗体：使用两个*或两个_包围文字。

```
**这是粗体**
__这是粗体__
```

  **这是粗体**
  __这是粗体__

- 斜体：使用一个*或一个_包围文字。
```
*这是斜体*
_这是斜体_
```
  *这是斜体*
  _这是斜体_

## 4.列表

- 无序列表使用星号*、加号+或减号-作为列表标记。

```
* 列表项一
* 列表项二
* 列表项三
```
  * 列表项一
  * 列表项二
  * 列表项三

- 有序列表使用数字后跟一个点来创建。

```
1. 第一项
2. 第二项
3. 第三项
```

  1.第一项
  2.第二项
  3.第三项

## 5.链接

使用方括号`[]`来包含链接文本，圆括号`()`来包含URL

```
[这是一个链接](https://www.example.com)
```

[这是一个链接](https://www.example.com)

## 6.图片

和链接类似，但是前面加上一个感叹号`!`。

```
![这是图片的标记文字](https://www.example.com/image.jpg)
```

![这是图片的标记文字](https://www.example.com/image.jpg)

可以使用html标签对图片进行缩放

``` 
<img src="https://www.example.com/image.jpg" width="50%" height="50%" alt="这是图片的标记文字" />

``` 

``` 
<img src="https://www.example.com/image.jpg" style="zoom:25% alt="这是图片的标记文字" />

```
## 7.引用

使用`>`来创建引用。

> [!TIP]
> 都可以引用，格式不一样可以起强调作用

```
> [!NOTE]
> Useful information that users should know, even when skimming content.
```
```
> [!TIP]
> Helpful advice for doing things better or more easily.
```
```
> [!IMPORTANT]
> Key information users need to know to achieve their goal.
```
```
> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.
```
```
> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
```

> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

## 8.代码

### a.单行代码使用反引号`来创建。

`这是一行代码`

### b.多行代码块使用三个反引号包围。

```
这是多行代码块
这是多行代码块
```

## 9.水平线

使用三个或更多的星号`*`、减号`-`或下划线`_`来创建。

---或***或___

-----

*****

___


## 10.表格

使用竖线`|`和减号`-`来创建表格。

```
| 标题1 | 标题2 | 标题3 |
|-------|-------|-------|
| 单元格1 | 单元格2 | 单元格3 |
| 单元格4 | 单元格5 | 单元格6 |
```

| 标题1   | 标题2   | 标题3   |
| ------- | ------- | ------- |
| 单元格1 | 单元格2 | 单元格3 |
| 单元格4 | 单元格5 | 单元格6 |

## 11.任务列表

使用`- [ ]`和`- [x]`来创建任务列表。

```
- [ ] 未完成的任务
- [x] 已完成的任务
```

- [ ] 未完成的任务
- [x] 已完成的任务

> [!NOTE]
> 这些是Markdown的一些基本语法，可以帮助你开始使用Markdown来格式化你的文本。