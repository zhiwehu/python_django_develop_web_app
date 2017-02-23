# 准备开发环境

---

## Python2 or Python3

Python目前有2个大版本：Python2和Python3。我建议使用Python3，因为根据官方的说法，Python3代表了Python的未来。如果是几年之前，使用Python3会有很多问题，最主要的就是很多第三方的Python软件包不兼容Python3，但现在有越来越多的Python软件包都已经支持Python3，所以如果条件允许的话，我们应该尽可能的使用Python3。

![](/assets/python version)

很多计算机操作系统都预装了Python，比如我的Mac OS就预装了Python2.7.10。我们只需要在终端命令行工具上输入`python --version`，如果你能看到相应的Python版本，就表明你已经安装了Python。如果没有安装或者是你想升级Python版本，只需要去官方网站\(https://www.python.org/downloads/\)下载安装即可。

> 关于Python2和Python3的区别，建议参考官方说明：https://wiki.python.org/moin/Python2orPython3



## pip

什么是pip？这是一个Python软件包安装工具。如果是从官方下载安装Python话，一般会自带pip和easy\_install（另一个Python软件包安装工具）。在终端命令行工具上输入`pip --version`，如果能够看到相应的pip版本号，表示已经安装pip了，如果没有安装或者是想升级版本，官方的安装方法如下：

1. 下载get-pip.py：https://bootstrap.pypa.io/get-pip.py
2. 运行`python get-pip.py`

![](/assets/python get-pip.py)

## virtualenv

什么是virtualenv？假如你的电脑上永远只有一个Python项目，那么你直接使用系统



