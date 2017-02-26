# 项目目录结构

> 在上一节里我们使用Django的`django-admin startproject`命令来创建了一个`Helloworld`的项目，在没有写任何代码的情况下成功运行了这个项目。虽然目前来说这个项目没有任何功能，但是这是我们一个成功的开始，不是吗？

## Helloworld项目的目录结构

我们来看一下这个项目的目录结构

![](/assets/Helloworld project directory structure)

* 最外层的Helloworld目录，是项目的根目录，在这个目录下我们看到有2个文件，一个是`db.sqlite3`是数据库文件，另一个是`manage.py`是Django提供的一个管理工具入口，比如上一节中我们使用`python manage.py runserver`来运行这个web app。
* 根目录下面的Helloworld目录，是项目的配置目录，里面放了Django的一些配置信息，包括一个`settings.py`，一个根`urls.py`和`wsgi.py`，这些都是Django运行所需要的配置性文件。
* 还有一个firstapp是我使用`django-admin startapp firstapp`这个命令创建的一个app，这相当是这个项目的一个功能性的app，Django使用app来划分模块。

## 这个项目目录结构好吗？

虽然我们使用了Django提供的`django-admin`创建的项目目录结构看起来很简单明了，但是我们应该知道，这只是供学习使用的，在真正的项目里，估计就没有人这样使用了。一个真实的产品项目，我们需要有更多的配置信息、文档、测试等，以及代码仓库配置等。而这个简单的目录结构显然是达不到这样的要求的。

## 推荐的项目目录结构

在本节里我重点是要介绍一个我认为是最佳的Django项目目录结构，当然所谓的『最佳』因人而异，我同时也会提供其他的一些选项供参考。接下来看一下这个目录结构。

![](/assets/The best django project directory structure)

接下来我详细说明一下这个目录结构
* 最外层的project是项目根目录，这个目录除了之前的`manage.py`这个文件外，还有更多的配置文件，和其他子目录。这些配置文件后面会详细介绍。
* config目录是配置目录，里面除了包含了根`urls.py`文件和`wsgi.py`文件，我们将原来的`settings.py`扩展成为了一个Python package，因为我们在不同的环境中将使用不同的配置文件，在本地电脑上使用`settings.local.py`，而在生产环境中使用`settings.production.py`。
* docs是文档目录
* project目录是项目的apps目录，我们将这个web的apps都放在这个目录下面，比如这里已经有一个`users`的app，同时我们也看到有`static`和`templates`这2个目录，这2个并不是app，而是其他apps需要使用的静态文件目录和模板目录。
* requirements目录是放置依赖包的索引文件，我们知道Python使用`pip`安装Python软件包，所以需要些些Python软件包我们就在一个txt文件里列出这些软件包的名字和版本号。注意我们同样是根据不同的环境有不同的软件包索引，开发环境和生产环境所依赖的Python软件包是不一样的，所以我们也分开在不同的文件中索引。
* utility目录放的是一些项目的工具shell，比如运行这个项目操作系统需要安装的一些底层库和软件包等，这些一般是在部署时使用。

## 怎么创建这个目录结构？

每次开始一个新的Django项目，我们就需要初始化这个项目，创建这个项目的目录结构，然后进行开发。我们知道使用`django-admin`命令行工具是可以做到这一点的，我们用它来创建了`Helloworld`项目。而上面这个项目目录结构是怎么创建的呢？接下来我将介绍另一个非常实用的工具[`cookiecutter`](https://github.com/audreyr/cookiecutter)

## cookiecutter

这是一个专门用于创建项目目录结构的工具，同时也是使用Python来实现的，它可以使用一个模板来创建一个项目，比如上面我介绍的项目目录结构实际上是一个模板，也是github开源的，链接：https://github.com/pydanny/cookiecutter-django

因为这只是一个工具，我们将重点介绍如何使用这个工具：

1. `pip install cookiecutter`安装cookiecutter
2. `cookiecutter https://github.com/pydanny/cookiecutter-django` 创建项目

运行上面第二个命令的时候，会问你一大堆问题，这些问题中下示例（附简短讲解）

```
Cloning into 'cookiecutter-django'...
remote: Counting objects: 550, done.
remote: Compressing objects: 100% (310/310), done.
remote: Total 550 (delta 283), reused 479 (delta 222)
Receiving objects: 100% (550/550), 127.66 KiB | 58 KiB/s, done.
Resolving deltas: 100% (283/283), done.
# 问你项目叫什么名字，这里可以大小写，带空格
project_name [Project Name]: Reddit Clone
# 问你项目的根目录名字，一般是小写没有空格，这个会生成一个目录
project_slug [reddit_clone]: reddit
# 开发者名字
author_name [Daniel Roy Greenfeld]: Jeffrey Hu
# 开发者邮件
email [you@example.com]: zhiwehu@gmail.com
# 项目简短介绍
description [A short description of the project.]: A reddit clone.
# 项目域名
domain_name [example.com]: lettoo.com
# 项目版本号
version [0.1.0]: 0.0.1
# 时区，就选默认的UTC
timezone [UTC]: 
# 是否使用whitenoise，whitenoise是一个Python实现的静态文件host解决方案，建议初学者选No
use_whitenoise [y]: n
# 是否使用celery，[celery](http://www.celeryproject.org/)是一个Python实现的分布式任务队列解决方案，一般用于后台job，建议初学者选No
use_celery [n]: 
# 是否使用mailhog，mailhog是一个用于本地开发环境测试email的，建议初始选No
use_mailhog [n]: n
# 是否使用sentry，sentry是一个云端日志跟踪和分析平台，Python实现，同时也是开源平台，你可以自己搭建自己的sentry云日志跟踪分析平台。建议初始选No
use_sentry_for_error_reporting [y]: n
# 是否使用opbeat，opbeat是一个云端性能跟踪和分析工具，有一部分错误分析功能，建议初始选No
use_opbeat [n]: n
# 是否使用pycharm，pycharm是一个IDE，由大名鼎鼎的jetbrains公司出品，其出品其他有名的IDE如Idea，Webstorm等，因为我是pycharm开发所以选Yes，如果你不使用这个IDE则选No
use_pycharm [n]: y
# 是否是windows操作系统
windows [n]: n
# 是否使用Python3
use_python3 [y]: y
# 是否使用docker，docker是一个app容器平台，建议初始选No
use_docker [y]: n
# 是否使用heroku，heroku是一个PAAS云平台，用于部署web app，建议初始选No
use_heroku [n]: n
# 是否使用compressor，compressor是一个压缩解决方案，建议初始选No
use_compressor [n]: n
# 使用postgresql版本，这个项目建议本地开发环境和生产环境都使用Postgresql数据库，Postgresql是一个开源数据库，也是Django官方推荐使用的数据库，默认选择1为当前最新的版本。
Select postgresql_version:
1 - 9.5
2 - 9.4
3 - 9.3
4 - 9.2
Choose from 1, 2, 3, 4 [1]: 1
# 选择哪一种JavaScript任务管理器，这里建议初始选None，我们不希望在这里过多的涉及前端的内容。
Select js_task_runner:
1 - Gulp
2 - Grunt
3 - Webpack
4 - None
Choose from 1, 2, 3, 4 [1]: 4
# 是否使用let's encrypt，let's encrypt是一个免费生成SSL HTTPS证书的服务，让你的网站免费支持https安全协议，默认选No
use_lets_encrypt [n]: n
# 开源license，默认选1，如果你是私有项目，选5
Select open_source_license:
1 - MIT
2 - BSD
3 - GPLv3
4 - Apache Software License 2.0
5 - Not open source
Choose from 1, 2, 3, 4, 5 [1]: 1
是否使用AWS Elastic Beanstalk，默认选No
use_elasticbeanstalk_experimental: n
```
好吧我承认一下子内容显的有点多，我们目前不需要过多的关注上面那些第三方的服务或者软件包，我们本节的目标就是使用`cookiecutter`来创建我们的项目目录而已。当然我们可以了解到，开发一个真正的Python Django web app是需要掌握多方面的知识的，当然我们目前先不用关注这些，部分内容我们会在后面的章节里详细说明。
