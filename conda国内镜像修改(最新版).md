例子卡片11：新手操练Python前，修改conda下载源，提速100倍！

先来区分几个小白容易混淆的概念：pycharm，python解释器，conda安装，pip安装，总结来说：

- `pycharm`是python开发的集成开发环境(Integrated Development Environment，简称IDE)，它本身无法执行Python代码
- `python解释器`才是真正执行代码的工具，pycharm里可设置Python解释器，一般我们可去python官网下载python3.7或python3.8版本；如果安装过`anaconda`，它里面必然也包括一个某版本的Python解释器；pycharm配置python解释器选择哪一个都可以。
- `conda安装`：我们安装过anaconda软件后，就能够使用conda命令下载anaconda源里(比如中科大镜像源)的包
- `pip安装`：也是一种类似于conda安装的python安装方法，如果用过Centos系统，它就像`yum`安装一样。



在使用安装`conda` 安装某些包会出现慢或安装失败问题，最有效方法是修改镜像源为国内镜像源。

之前大家都选用清华镜像源，但是2019年后已停止服务。推荐选用中科大镜像源。

先查看已经安装过的镜像源，cmd窗口执行命令：

```python
conda config --show
```

查看配置项`channels`，如果显示带有`tsinghua`，则说明已安装过清华镜像。

```python
channels:
- https://mirrors.tuna.tsinghua.edu.cn/tensorflow/linux/cpu/
- https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
- https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
- https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
- https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
```

下一步，使用`conda config --remove channels url地址 `删除清华镜像，如下命令删除第一个。然后，依次删除所有镜像源

```python
conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/tensorflow/linux/cpu/
```

添加目前可用的中科大镜像源：

```
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
```

并设置搜索时显示通道地址：

```python
conda config --set show_channel_urls yes
```

确认是否安装镜像源成功，执行`conda config --show`，找到`channels`值为如下：

```
channels:
  - https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
  - defaults
```

Done~
