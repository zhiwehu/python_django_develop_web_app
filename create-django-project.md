# 创建Django项目

创建Django项目有很多种方法，最简单的方法就是使用Django官方文档说明的方法，具体可以参考[https://www.djangoproject.com/start/](https://www.djangoproject.com/start/)。这里结合一下我的经验，简单说明一下步骤：

## 使用virtualenv创建项目虚拟Python环境

因为我们不想在系统级别的Python环境里安装Django以及其他依赖的Python软件包，所以我们使用virtualenv来创建一个虚拟Python环境。

```
virtualenv env --python=python3
```

![](/assets/virtualenv env --python=python3)

注意我使用了`--python=python3`的参数来告诉virtualenv这个虚拟环境是使用Python3的。virtualenv会创建一个Python虚拟环境在当前目录的`.env`子目录下，使用`source .env/bin/activate`可以激活这个虚拟Python环境，然后使用`python --version`命令可以看到这个虚拟Python环境的版本是Python3.6.0。

## 安装Django

使用`pip install django`来安装Django当前的最新版本。

安装完成后使用`python -m django --version`来检查Django的版本。

![](/assets/pip install django)

## 创建Django项目

Django是一个Web开发框架，它同时也提供了命令行工具来帮助开发者创建项目。

```
django-admin startproject Helloworld
```

![](/assets/django startproject Helloworld)

用上面的命令，创建了一个名为Helloworld的项目，这个项目的目录结构如下：

![](/assets/Helloworld Django Project dir)

## 运行Django项目

是的你没有听错，我们现在就可以运行这个项目了，尽管我们一行代码也没有写！

```
cd Helloword
python manage.py runserver
```

![](/assets/python manage.py runserver)

打开浏览器，在地址栏输入`http://127.0.0.1:8000`，我们看到如下界面！

![](/assets/first run Helloworld)

