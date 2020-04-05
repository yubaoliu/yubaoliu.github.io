---
layout: "post"
title: "Markdown Cheat Sheet"
date: "2020-04-04 14:21"
categories: articles
toc: true
comments: true
---

# Resources
- [Markdown 教程-runoob](https://www.runoob.com/markdown/md-tutorial.html)
- [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

# Table of contents
[TOC]

# Header
This will be parsed as HTML format:
```html
<pre class="markdown"><b># H1</b></pre>
```

# Math
```latex
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$
```

$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix}
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$

# Task Lists

```markdown
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```

- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item


# 锚点
Each header is an anchor.

```markdown
Jump to [Reference](#Reference)
```
Jump to [Reference](#Reference)

# Font Style

```markdown
~~delete~~
*斜体文本*
_斜体文本_
**粗体文本**
__粗体文本__
***粗斜体文本***
___粗斜体文本___
<u>带下划线文本</u>
```

~~delete~~
*斜体文本*
_斜体文本_
**粗体文本**
__粗体文本__
***粗斜体文本***
___粗斜体文本___
<u>带下划线文本</u>

# 分隔符/分割线
```sh
***
* * *
- - -
----------
```

# 转义字符
```#!/bin/sh
\<br/>
```
\<br/>

```HTML
**文本加粗**
\*\* 正常显示星号 \*\*
```

**文本加粗**
\*\* 正常显示星号 \*\*

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
```HTML
\   反斜线
`   反引号
*   星号
_   下划线
{}  花括号
[]  方括号
()  小括号
#   井字号
+   加号
-   减号
.   英文句点
!   感叹号
```
# List
```markdown
1. 第一项：
    - 第一项嵌套的第一个元素
    - 第一项嵌套的第二个元素
2. 第二项：
    - 第二项嵌套的第一个元素
    - 第二项嵌套的第二个元素
```

1. 第一项：
    - 第一项嵌套的第一个元素
    - 第一项嵌套的第二个元素
2. 第二项：
    - 第二项嵌套的第一个元素
    - 第二项嵌套的第二个元素

# 链接
```markdown
这个链接用 1 作为网址变量 [Google][1]
这个链接用 runoob 作为网址变量 [Runoob][runoob]
然后在文档的结尾为变量赋值（网址）

  [1]: http://www.google.com/
  [runoob]: http://www.runoob.com/
```

这是一个链接 [菜鸟教程](https://www.runoob.com)

直接使用链接地址：
<https://www.runoob.com>

- 这个链接用 1 作为网址变量 [Google][1]
- 这个链接用 runoob 作为网址变量 [Runoob][runoob]
- 然后在文档的结尾为变量赋值（网址）

# 表格
- -: 设置内容和标题栏居右对齐。
- :- 设置内容和标题栏居左对齐。
- :-: 设置内容和标题栏居中对齐。

```markdown
| 左对齐 | 右对齐 | 居中对齐 |
| :-----| ----: | :----: |
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |
```

| 左对齐 | 右对齐 | 居中对齐 |
| :-----| ----: | :----: |
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |

# 脚注
``创建脚注格式类似这样 [^RUNOOB]``

创建脚注格式类似这样 [^RUNOOB]

# html
目前支持的 HTML 元素有：``<kbd> <b> <i> <em> <sup> <sub> <br>``等

```HTML
使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑
```

使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

# 引用
>这是引用的内容
>>这是引用的内容


# Reference
- [Markdown 教程-runoob](https://www.runoob.com/markdown/md-tutorial.html)


[1]: http://www.google.com/
[runoob]: http://www.runoob.com/

[^RUNOOB]: 菜鸟教程 -- 学的不仅是技术，更是梦想！！！
