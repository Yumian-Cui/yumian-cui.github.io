---
weight: 1001
title: "将 Julia 配置到 Jupyter Notebook 中"
date: 2022-01-30T01:44:15-06:00
lastmod: 2022-01-30T01:44:15-06:00
draft: false

description: "我在远程机器上将 Julia 配置为 Jupyter Notebook 的经验"
# resources:
# - name: "featured-image"
#   src: "featured-image.jpg"

tags: ["Julia", "Jupyter Notebook", "Python", "设置", "安装"]
categories: ["博客"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---
<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

这个博客是在我的 *将 Matlab 配置到 Jupyter Notebook 中* 博客之后不久写的。如果你想看那个，你可以点击 [here](https://yumian-cui.github.io/matlab_jupyter/)。这个更容易安装，所以让我们立即开始！

## 0. 参考文献

类似地，我在这里发布了参考资料文章，以备你自己尝试使用。

{{< admonition note "References List" >}}

- [官方二进制文件的平台特定说明](https://julialang.org/downloads/platform/)
- [如何将 Julia 添加到 Jupyter Notebook](https://datatofish.com/add-julia-to-jupyter/)

{{< /admonition >}}

## 1. 下载 Julia 

这台远程电脑没有安装 Julia。请查看列表中的第一个文档，以找到针对你的计算机类型定制的说明--Windows、MaxOS 或 Linux。我在 Linux 上，所以我跳到了 [Linux 和 FreeBSD](https://julialang.org/downloads/platform/#linux_and_freebsd) 部分。


```code
wget https://julialang-s3.julialang.org/bin/linux/x64/1.7/julia-1.7.1-linux-x86_64.tar.gz
tar zxvf julia-1.7.1-linux-x86_64.tar.gz
```

记住将 Julia 的 ```bin``` 文件夹添加到 ```PATH``` 环境变量，这样你就可以在任何地方执行 Julia。否则，每次都需要执行 ```<Julia directory>/bin/julia```。


```code
vim ~/.bashrc
export PATH="$PATH:/path/to/<Julia directory>/bin" / export PATH="/path/to/<Julia directory>/bin:$PATH"
source ~/.bashrc # Don't forget!
```

启动一个新的终端，并尝试进入一个不是 Julia 的 ```bin``` 的文件夹，输入 ```julia```，它应该可以正常工作。你将看到 ```julia>``` 命令行。

## 2. 将 Julia 添加到 Jupyter Notebook 

现在，在新的终端，你刚刚打开了朱莉娅，请照做以下：


```code
using Pkg
Pkg.add("IJulia")
```

好了！现在打开一个新的 Jupyter 笔记本，你应该看到 Julia 作为一个选项，在你的 Notebook 下拉菜单。





