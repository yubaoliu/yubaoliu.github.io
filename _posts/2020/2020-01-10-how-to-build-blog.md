---
layout: "post"
title: "How to build blog"
date: "2020-01-10 14:49"
categories: Tools
tags: [Tools]
toc: true
comments: true
---

* TOC
{:toc}

# Introduction

[About GitHub Pages and Jekyll](https://help.github.com/en/github/working-with-github-pages/about-github-pages-and-jekyll#plugins)

# Upload image

- [PicGo](https://github.com/Molunerfinn/PicGo/releases)



![flowers-left](/assets/img/2020-01-10-how-to-build-blog/flowers-left.png)

# TOC


## Plugin: Jekyll-toc

- Issue:  TOC on GitHub Pages [#29](https://github.com/toshimaru/jekyll-toc/issues/29)

Description:

> The plugin works fine locally, but when I push the website to the GitHub pages, it doesn't work there. Is there any way to make it work on GitHub beside producing a static version of the website in gh-pages branch and pushing that to the GitHub?

Answer:

> You're right, you can NOT use jekyll-toc powered by official GitHub Pages gem because available plugins are limited.
> To use jekyll-toc plugin, build your site locally and push it onto the gh-pages branch. I deployed my personal blog site in that way. The source code is open, so you can see how it works. https://github.com/toshimaru/blog.toshimaru.net

