---
weight: 1000
title: "Configure Julia into Jupyter Notebook"
date: 2022-01-30T01:44:15-06:00
lastmod: 2022-01-30T01:44:15-06:00
draft: false

description: "My experiences with configuring Julia into Jupyter Notebook in a remote machine"
# resources:
# - name: "featured-image"
#   src: "featured-image.jpg"

tags: ["Julia", "Jupyter Notebook", "Python", "configuration", "installation"]
categories: ["blogs"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---
<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

This blog is written soon after my *Configure Matlab into Jupyter Notebook* blog. If you'd like to see that one, you can click [here](https://yumian-cui.github.io/matlab_jupyter/). It is easier to install so let's just get started!

## 0. References

Similarly, I post the resources articles I referred in here in case you want to try it on your own. 

{{< admonition note "References List" >}}

- [Platform Specific Instructions for Official Binaries](https://julialang.org/downloads/platform/)
- [How to Add Julia to Jupyter Notebook](https://datatofish.com/add-julia-to-jupyter/)

{{< /admonition >}}

## 1. Download Julia

There's no Julia installed in the remote machine. Please take a look at the first document in list to find the instructions tailored to your computer type --- Windows, MaxOS, or Linux. I'm on Linux, so I jumped to the section [Linux and FreeBSD](https://julialang.org/downloads/platform/#linux_and_freebsd). 

```code
wget https://julialang-s3.julialang.org/bin/linux/x64/1.7/julia-1.7.1-linux-x86_64.tar.gz
tar zxvf julia-1.7.1-linux-x86_64.tar.gz
```

Remember to add Julia's ```bin``` folder to ```PATH``` environmental variable so that you can execute Julia anywhere. Otherwise, you need to do ```<Julia directory>/bin/julia``` every time. 

```code
vim ~/.bashrc
export PATH="$PATH:/path/to/<Julia directory>/bin" / export PATH="/path/to/<Julia directory>/bin:$PATH"
source ~/.bashrc # Don't forget!
```

Start a new terminal and try go to a folder that's not Julia's ```bin```, enter ```julia```, which should work just fine. You will see ```julia>``` command line. 

## 2. Add Julia to Jupyter Notebook

Now in the new terminal where you just opened Julia, do:

```code
using Pkg
Pkg.add("IJulia")
```

Done! Now open a new jupyter notebook and you should see Julia as an option in your notebook drop-down menu. 





