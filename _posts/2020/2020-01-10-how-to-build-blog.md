---
layout: "post"
title: "How to build blog"
date: "2020-01-10 14:49"
categories: Tools
tags: [Tools]
toc: true
comments: true
---

# Introduction

[About GitHub Pages and Jekyll](https://help.github.com/en/github/working-with-github-pages/about-github-pages-and-jekyll#plugins)

# Upload image

- [PicGo](https://github.com/Molunerfinn/PicGo/releases)


# Jekyll TO

如何在页面上显示TOC?

## Plugin: [Jekyll-toc](https://github.com/toshimaru/jekyll-toc)

这种方法在上传到GitHub Pages上后,页面上发现并没有显示TOC.这种方法是不可行的.

- Issue:  TOC on GitHub Pages [#29](https://github.com/toshimaru/jekyll-toc/issues/29)

Description:

> The plugin works fine locally, but when I push the website to the GitHub pages, it doesn't work there. Is there any way to make it work on GitHub beside producing a static version of the website in gh-pages branch and pushing that to the GitHub?

Answer:

> You're right, you can NOT use jekyll-toc powered by official GitHub Pages gem because available plugins are limited.

> To use jekyll-toc plugin, build your site locally and push it onto the gh-pages branch. I deployed my personal blog site in that way. The source code is open, so you can see how it works. https://github.com/toshimaru/blog.toshimaru.net

## Plugin: [jossets/jekyll-toc](https://github.com/jossets/jekyll-toc)

这种方法是兼容GitHub page的.

> A GitHub Pages compatible Table of Contents generator without a plugin or JavaScript :octocat: https://pure-liquid.allejo.org/

Usage:

Alright, so how do you use it?

使用方法很简单:

- Download the latest [toc.html](https://github.com/jossets/jekyll-toc/blob/master/_includes/toc.html) file

- Toss that file in your _includes folder.

- Use it in your template layout where you have ``{{ content }}``  which is the HTML rendered from the markdown source with this liquid tag:

    ```sh
    {% include toc.html html=content %}
    ```
## Reference
- [jekyll GitHub Pagesでも目次(ToC)は作れる](https://blog.kotet.jp/2018/04/toc-on-github-pages/)

# BiliBili
## Insert Video

Add $$width="640" height="480"$$ is needed.

<iframe width="640" height="480" src="//player.bilibili.com/player.html?aid=76942715&bvid=BV1gJ411R7GM&cid=131520361&page=1" scrolling="no" border="0" frameborder="yes" framespacing="0" allowfullscreen="true">
</iframe>

## 专栏写作 Use Markdown

BiliBili的富文本编辑器,用起来很不方便. 现在大家都用Markdown方式来编辑.

使用方法:

- Install Chrome
- Install **Markdown Here** plugin.
    ![Markdown Here](http://qiniu.yubaoliu.cn/markdown-img-paste-20200418131546727.png)
- Edit your blog using Markdown grammer

For example:

````
# Syntax highlighting

``` js
var foo = function (bar) {
  return bar++;
};
console.log(foo(5));
```
# Tables
| Option | Description |
| ------ | ----------- |
| data   | path to data files to supply the data that will be passed into templates. |
| engine | engine to be used for processing templates. Handlebars is the default. |
| ext | extension to be used for dest files. |
````

- Click **Markdown Here** to format your markdown text
![Markdown Here Result](http://qiniu.yubaoliu.cn/markdown-img-paste-20200418132450352.png)



## 网上常见的其它方法

但是这些方法还是有些复杂.

### bilibili-zhuanlan-markdown-tool

- [bilibili-zhuanlan-markdown-tool](https://www.bilibili.com/read/cv403592/)

### markdown上传biliibili专栏

- [markdown上传biliibili专栏](https://www.bilibili.com/read/cv4578780)

这个方法我测试过. 个人建议是用别的软件行将markdown转成HTML, 然后再POST到B站上.

This is his script that used to transfer markdown to html and upload to BiliBili:

```python
import requests
import codecs, markdown
import re

def post_md(title, content, cookie):

    csrf = re.search(r"bili_jct=(.+?);", cookie).group(1)
    headers = {
               "Host": "api.bilibili.com",
               "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:72.0) Gecko/20100101 Firefox/72.0",
               "Accept": "application/json, text/javascript, */*; q=0.01",
               "Accept-Language": "zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en;q=0.3,en-US;q=0.2",
               "Accept-Encoding": "gzip, deflate, br",
               "Content-Type": "application/x-www-form-urlencoded; charset=UTF-8",
               "Content-Length": "489",
               "Origin": "https://member.bilibili.com",
               "Connection": "keep-alive",
               "Referer": "https://member.bilibili.com/article-text/home?",
               "Cookie": cookie
               }

    data = {
            "title": title,
            "banner_url": "",
            "content": content,
            "summary": '',
            "words": "",
            "category": "0",
            "list_id":"0",
            "tid": "4",
            "reprint": "0",
            "tags": "",
            "image_urls": "",
            "origin_image_urls": "",
            "dynamic_intro": "",
            "media_id": "0",
            "spoiler": "0",
            "original": "0",
            "csrf": csrf
           }

    url = "https://api.bilibili.com/x/article/creative/draft/addupdate"
    r = requests.post(url, data, headers=headers)
    if r.status_code == 200:
        print("上传成功！请到草稿箱查看")

def startwith(line):
    line_split= line.split(" ")
    line_start = line_split[0]
    line_end = " ".join(line_split[1:])
    if line_start == "#":
        return "<h1>" + line_end + "</h1>"
    elif line_start == "##":
        return "<h2>" + line_end + "</h2>"
    elif line_start == "###":
        return "<h3>" + line_end + "</h3>"
    elif line_start == "####":
        return "<h4>" + line_end + "</h4>"
    elif line_start == "#####":
        return "<h5>" + line_end + "</h5>"
    elif line_start == "######":
        return "<h6>" + line_end + "</h6>"
    elif re.match(r"!\[.*?\]\((.+?)\)", line):
        return '<img alt="" src=%s />' % re.match(r"!\[.*?\]\((.+?)\)", line).group(1)
    else:
        return "<p>" + line + "</p>"


def md_to_html(file_path):
    with open(file_path, "r", encoding="utf-8") as f:
        lines = f.readlines()
        lines = [i.strip() for i in lines]
        new_lines = [startwith(i) for i in lines]
        print("已经将markdown转换成html")
        return "\n".join(new_lines)


if __name__ == "__main__":

    md_path = "E:/自己的程序/bilibili/markdown_upload/markdown上传biliibili专栏.md"
    html = md_to_html(md_path)

    cookie = ""
    title = md_path.split("/")[-1].split(".")[0]
    post_md(title, html, cookie)
```
About this script, please refer https://www.bilibili.com/read/cv4578780 for detail.
