---
weight: 1000
title: "在 Jupyter Notebook 里使用 Matlab 教程"
date: 2022-01-30T01:44:15-06:00
lastmod: 2022-01-30T01:44:15-06:00
draft: false

description: "我在远程机器上将 Matlab 配置到 Jupyter Notebook 的经验分享"
# resources:
# - name: "featured-image"
#   src: "featured-image.jpg"

tags: ["Matlab", "Jupyter Notebook", "Python", "设置", "安装"]
categories: ["博客"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---
<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

我开始使用 Jupyter Notebook 仅用于在 Python 中进行编码。然而，随着我逐渐学会了更多的编程语言，我希望我可以在一个环境中拥有所有的语言，然后我就不需要打开多个程序了。幸运的是，我被告知我可以轻松地将这些语言配置到笔记本中（尽管对我来说不是一个简单的过程，/（o）/~~），并且由于我将在本学期同时学习 Matlab 和 Julia，这将是一个尝试它的好机会。

对于那些想要继续阅读的人的注意事项，这个博客 (1) 不包括如何在您自己或远程计算机上安装 Matlab (2) 主要用于在远程位置安装 MATLAB Engine API for Python（您不需要 '没有写权限，换句话说，不是超级用户）和故障排除，因为我不想在我自己的笔记本电脑上安装 Matlab，但仍然想享受这些好处。 不过，该过程可以适应并推广到其他情况，我确实在下面列出了适合各种需求的参考资料。

## 0. 参考文献

我鼓励你先自己试一试。以下是我在流程中提到的一些资源（包括故障排除）：

{{< admonition note "References List" >}} 

- [Jupyter 笔记本电脑的 MATLAB 内核教程](https://portal.geomar.de/documents/18749/1308328/2018-09-27_Matlab+Kernel+for+Jupyter+Notebooks.pdf/ecd33b0c-2f3d-49ca-8146-1b957a68597d)
- [在非默认位置为 Python 安装 MATLAB 引擎 API ](https://www.mathworks.com/help/matlab/matlab_external/install-matlab-engine-api-for-python-in-nondefault-locations.html)
- [安装 Jupyter-Matlab ](https://am111.readthedocs.io/en/latest/jmatlab_install.html)
- [如何使用 Python 的 Anaconda 包管理器正确安装 MATLAB 引擎？](https://www.mathworks.com/matlabcentral/answers/346068-how-do-i-properly-install-matlab-engine-using-the-anaconda-package-manager-for-python)
- [packagesnotfounderror:以下软件包不能从当前渠道获得：](https://stackoverflow.com/questions/48493505/packagesnotfounderror-the-following-packages-are-not-available-from-current-cha)
- [当尝试使用 ipyWidgets 时 404 错误且没有此通信目标](https://github.com/jupyter-widgets/ipywidgets/issues/1720)

{{< /admonition >}}

大多数教程都假设编码人员已经具有相对较高的理解水平。 对于像我这样的新手，我会很感激更详细的解释。 这也是我立即写这篇博客的原因，供我自己参考，也供那些正在努力解决问题的人参考。

## 1. 使用 Conda 创建 Myenv 

对于这类任务，我建议始终创建一个虚拟环境。然后，你可以对任何设置和包进行个性化设置，以防任务与安装在基础中的包不一致，或者你不想搞砸它。前提条件是，你应该通过 [微型或水蟒](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html) 安装 ```conda```。我非常后悔一开始没有这样做，因为在一步之后，我发现由于某些原因 Python3.8 不能很好地工作；所以当我创建 Myenv Susu 时，我最终切换到了 Python3.7:


```code
conda create -n susu python=3.7
```

有关 Conda Create Env 的更多相关内容，请查看链接 [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#id1) 的文档。

## 2. 找到你的 MATLAB 文件夹 ```matlabroot```

理想情况下，打开已安装的 Matlab 应用程序并运行 ```matlabroot``` 就可以找到 ```matlabroot```。你将看到类似 ```ans = "???/???/matlab-2021b"``` 的路径。但是，当远程计算机不在你身边时，你该怎么办？然后，你可以 SSH 到那台机器上，在终端上处理这个问题，这往往是很慢的。通过在 Terminal 中打开 Matlab，输入 [``Matlab-nodesktop-nodisplay``](https://www.mathworks.com/help/matlab/ref/matlablinux.html)，可以加快速度（虽然我感觉不是很快）。它的开头是说 ```MATLAB is selecting SOFTWARE OPENGL rendering.``` 这是个好兆头，你只需等待几分钟。一旦 ```>>``` 符号弹出，运行 ```matlabroot```。

## 3. 在非默认文件夹中构建或安装

基本上，如果你没有对默认的 Matlab 文件夹和默认的 Python 文件夹的写权限（如果你对此感到困惑，请查找 [默认值与非默认值文件夹](https://www.pcmag.com/encyclopedia/term/default-folder)），因为我正在访问远程计算机，请按以下方式执行：


```code
cd "matlabroot\extern\engines\python"
python setup.py build --build-base="builddir" install --prefix="installdir"
```

请注意，```builddir``` 将是你在 Matlab 文件夹下创建的非默认文件夹的路径（当你初始化 Matlab 程序时，默认文件夹将自动创建）。```installdir``` 也是。它是 Python 包的搜索路径中非默认文件夹的路径。我直接在 myenv susu 下创建它--```???/yumian/Documents/miniconda/envs/susu"```

## 4. 为 Jupyter 安装 Matlab 内核


```code
pip/conda install matlab_kernal
python -m matlab_kernel install
```

{{< admonition tip >}}
1. 我建议使用 ```conda``` 而不是 ```pip```。只是我的经验，因为 ```pip``` 一开始会给我带来一些问题。
2. 运行 ```conda install matlab_kernal``` 时，如果遇到：

    ```code 
    PackagesNotFoundError: The following packages are not available from current channels:

    - matlab_kernel
    ```
    尝试 ```conda install -c conda-forge matlab_kernel```
3. 当运行 ```python -m matlab_kernel install``` 时，如果它表示已定义权限，请按照它的建议执行，在末尾添加 ```--user```。

{{< /admonition >}}

完成这一步后，你就可以启动 Jupyter 笔记本了，可以选择 ```Matlab```。

在此之前，打开 ```Python``` 并运行 ```import matlab.engine``` 以验证你是否正确安装了此模块。你可以做的另一件事是 ```pip list | grep matlab```，它应该列出以下内容：


```code
matlab-kernel                 0.16.11
matlabengineforpython         R2021b
```

如果在尝试运行单元格时，后台一直报告 ```Matlab engine not installed:``` 错误，请返回检查已安装的目录；可能是你没有正确安装它。如果背景显示 ``` HTTP 404: Not Found (Kernel does not exist:``` 错误，请尝试下面的技巧（c.r.[@tensionhead](https://github.com/tensionhead)）：


```code
jupyter nbextension install --py widgetsnbextension --user
jupyter nbextension enable --py widgetsnbextension
```

编程愉快！我将有另一个关于配置 Julia 的博客，它比这个简单得多。








