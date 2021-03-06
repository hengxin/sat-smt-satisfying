# Z3环境配置

这个教程简单介绍[Z3](https://github.com/Z3Prover/z3)的环境配置, 主要使用PyCharm集成开发环境, 因此在各个平台的操作基本相同.

## 安装Python3

[SAT_SMT_by_example.pdf](https://yurichev.com/writings/SAT_SMT_by_example.pdf)书中使用的是Python2, 然而Python2已经于2020年1月1日[停止更新](https://pythonclock.org/). 书中的代码改为Python3几乎只需要将`print`加上括号, 比如`print s.model()`改为`print(s.model())`.

Windows安装步骤(其他平台请自行搜索安装方法):

- 下载最新[Python3安装包](https://www.python.org/ftp/python/3.8.2/python-3.8.2-amd64.exe), 如果速度较慢试试[这个](http://tangruize.fun:8080/Downloads/python-3.8.2-amd64.exe),
- 勾选`Add Python 3.8 to PATH`, 其他选项保持默认即可.

## 安装PyCharm

PyCharm是一个专门用于编写和调试Python代码的IDE, 可以在Jetbrains的[toolbox-app](https://www.jetbrains.com/toolbox-app/)中安装(推荐), 也可以[直接安装](https://www.jetbrains.com/pycharm/download).

## 配置PyCharm

以Windows为例, 配置步骤如下

- 打开 PyCharm - Settings(ctrl+alt+s) - Project Interpreter, 应该能自动找到Python解释器(如下图所示), 如果没有找到, 点击右上角的设置图标自行添加,

  ![Project Interpreter](figs/project_interpreter.png)

- 点击右上角的 `+` 图标, 会打开Available Packages菜单,

  ![Available Packages](figs/available_packages.png)

- 点击Manage Repositories, 由于官方的源太慢了, 将列表第一个改为 `https://pypi.tuna.tsinghua.edu.cn/simple/`
  
  ![Manage Repositories](figs/manage_repositories.png)

- 搜索并安装 `z3-solver` 和 `jupyter`. 注意是 `z3-solver` 而不是 `z3`, 这个比较坑, 因为代码中出现 `import z3` 而没有找到这个包时, PyCharm会提示安装 `z3`, 就会装错.

- 大功告成! 如果要打开或创建一个工程, Project Interpreter选择Existing interpreter.

  ![New Project](figs/new_project.png)

## 使用Jupyter Notebook

编写Python的教程文档通常使用[Jupyter Notebook](https://jupyter.org/)(文件扩展名为`.ipynb`), 它有 [Markdown cells](https://nbsphinx.readthedocs.io/en/0.6.0/markdown-cells.html) (在PyCharm中以`#%% md`开始, 支持Markdown和Latex的数学公式), [Code cells](https://nbsphinx.readthedocs.io/en/0.6.0/code-cells.html) (在PyCharm中以`#%%`开始, 可运行) 和 [Raw cells](https://nbsphinx.readthedocs.io/en/0.6.0/raw-cells.html). Jetbrains的IDE和VSCode都支持`.ipynb`格式.

将这个仓库用PyCharm打开, 创建一个Jupyter Notebook文件:

![New Jupyter Notebook](figs/new_jupyter_notebook.png)

或者在Terminal中运行`jupyter notebook`, 将会启动Jupyter服务并打开网页`http://localhost:8888/tree`, 这个网页的功能很强, 可以自行探索:

![jupyter notebook](figs/jupyter_notebook.png)

环境配置到这里就结束了, 打开[example.ipynb](example.ipynb)看看吧!