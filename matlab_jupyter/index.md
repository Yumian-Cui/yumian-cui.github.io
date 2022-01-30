# Configure Matlab into Jupyter Notebook

<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

I started using Jupyter Notebook only for coding in Python. However, gradually as I learnt more programming languages, I wish I could have all languages in one environment; Then I don't need to open multiple programs. Luckily, I was told I could easily configure those languages into the Notebook (though not an easy process for me, /(ㄒoㄒ)/~~) and as I would be learning both Matlab and Julia this semester, it would be a good chance to try it out. 

A caveat for those who want to keep on reading, this blog is mainly for installing MATLAB Engine API for Python in a remote location (where you don't have write permission, in other words, not super user) and troubleshooting as I don't want to install Matlab on my own laptop but still want to enjoy the benefits.

## 0. References

You're encouraged to try it on your own first. Here're some resources (including troubleshoots) I referred to in the process:

{{< admonition note "References List" >}}
{{< version 0.2.10 >}}

- [Matlab Kernel for Jupyter Notebooks Tutorial](https://portal.geomar.de/documents/18749/1308328/2018-09-27_Matlab+Kernel+for+Jupyter+Notebooks.pdf/ecd33b0c-2f3d-49ca-8146-1b957a68597d)
- [Install MATLAB Engine API for Python in Nondefault Locations](https://www.mathworks.com/help/matlab/matlab_external/install-matlab-engine-api-for-python-in-nondefault-locations.html)
- [Install Jupyter-MATLAB](https://am111.readthedocs.io/en/latest/jmatlab_install.html)
- [How do I properly install Matlab Engine using the anaconda package manager for Python?](https://www.mathworks.com/matlabcentral/answers/346068-how-do-i-properly-install-matlab-engine-using-the-anaconda-package-manager-for-python)
- [PackagesNotFoundError: The following packages are not available from current channels:](https://stackoverflow.com/questions/48493505/packagesnotfounderror-the-following-packages-are-not-available-from-current-cha)
- [404 error and no such comm target when trying to use ipywidgets](https://github.com/jupyter-widgets/ipywidgets/issues/1720)

{{< /admonition >}}

## 1. Create myenv using Conda

I would suggest for this type of task to always create an virtual environment. Then you can personalize any setting and packages in case the task doesn't align with packages installed in the base or you don't want to mess with that. The prerequisite is that you should install ```conda``` through either [Miniconda or Anaconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html). I highly regretted not doing this at the beginning because later during one step I found out for some reasons Python 3.8 doesn't work very well; so I ended up switching to Python 3.7 when I create myenv susu:

```code
conda create -n susu python=3.7
```

For more conda create env related stuff, please check out the documentation linked [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#id1).

## 2. Find your MATLAB Folder ```matlabroot```

Ideally, ```matlabroot``` can be found by opening the installed Matlab App and run ```matlabroot```. You will see a path like ```ans = "???/???/matlab-2021b"```. But what do you do when the remote computer is not near you? Then you can ssh to that machine and work around this in terminal, which tends to be slow. You can speed it up (though not much I feel) by opening Matlab in terminal by entering [```matlab -nodesktop -nodisplay```](https://www.mathworks.com/help/matlab/ref/matlablinux.html). It starts by saying ```MATLAB is selecting SOFTWARE OPENGL rendering.``` That's a good sign, and you will just wait for a few minutes. Once ```>>``` symbol pops up, run ```matlabroot```. 

## 3. Build or Install in Nondefault Folders

Basically, if you do not have write permission to the default Matlab folder and default Python folder (look up [default vs non-default folder](https://www.pcmag.com/encyclopedia/term/default-folder) if you're confused) as I do because I'm accessing a remote machine, do as follows:

```code
cd "matlabroot\extern\engines\python"
python setup.py build --build-base="builddir" install --prefix="installdir"
```

Notice that ```builddir``` would be a path to the non-default folder that you create under MATLAB folder (the default folder automatically get created when you initialize Matlab program). So is the ```installdir```. It is a path to the non-default folder in the search path for Python packages. I create it directly under myenv susu --- ```???/yumian/Documents/miniconda/envs/susu"```

## 4. Install the Matlab Kernel for Jupyter

```code
pip/conda install matlab_kernal
python -m matlab_kernel install
```

{{< admonition tip >}}
{{< version 0.2.10 >}}
1. I suggest using ```conda``` instead of ```pip```. Just my experience because ```pip``` causes some issues at first for me. 
2. When running ```conda install matlab_kernal```, if you run into:
    ```code 
    PackagesNotFoundError: The following packages are not available from current channels:

    - matlab_kernel
    ```
    Try ```conda install -c conda-forge matlab_kernel```
3. When running ```python -m matlab_kernel install```, if it says permission defined, do what it suggests, add ```--user``` at the end. 

{{< /admonition >}}

After done with this step, you're pretty much ready to launch your jupyter notebook and see ```Matlab``` as an option. 

Before that, Open ```Python``` and run ```import matlab.engine``` to verify you have this module correctly installed. Another thing you can do is ```pip list | grep matlab```, which should list something like:

```code
matlab-kernel                 0.16.11
matlabengineforpython         R2021b
```

If while you're trying to run the cells, the background keeps reporting ```Matlab engine not installed:``` error, go back to check your installed directory; it may be you didn't install it correctly. If the background says ``` HTTP 404: Not Found (Kernel does not exist:``` error, try the trick below (c.r. [@tensionhead](https://github.com/tensionhead)):

```code
jupyter nbextension install --py widgetsnbextension --user
jupyter nbextension enable --py widgetsnbextension
```

Happy coding! I will have another blog about configuring Julia which is so much easier than this. 









