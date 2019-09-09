---
title: 开发环境配置
tags: ubuntu opencv ide
categories: Jiaolong-cv-novice-tutorial
---

* TOC
{:toc}

# <span id="head2"> 一、Ubuntu18.04安装</span>

ubuntu18.04是一个操作系统，在其上进行开发比windows更加方便。

镜像下载地址

* [官网地址](https://ubuntu.com/download/desktop)
* [百度网盘链接](https://pan.baidu.com/s/1hJJBsDpbrWk7MiiB116mdg)  提取码: 6h2j

# <span id="head3"> 1.虚拟机安装</span>

首先安装vmware，交大有参加vmware学术计划，可以申请到正版下载。[http://vmap.sjtu.edu.cn](http://vmap.sjtu.edu.cn/)  
之后安装，百度有许多教程。

# <span id="head4"> 2.双系统安装</span>

双系统安装比较麻烦，但运行速度会稍快一些。同时虚拟机无法使用GPU资源，如果想要使用GPU进行机器学习计算等，务必使用双系统安装方式。

## <span id="head5"> 2.1磁盘分区</span>

为了安装ubuntu系统，我们需要在磁盘上开辟一块空间，**不需要分区，只需要划出一片空间即可**，推荐空间大小>50G。  
如果电脑空间足够的话，建议将分区分在固态硬盘上，如果安装在机械硬盘上，亲测会比较卡顿。  
分区软件可以使用DiskGenius：[官网下载地址](http://www.diskgenius.cn/)  
具体使用方法请自行探索。  

## <span id="head6"> 2.2启动盘制作</span>

也就是把下载的镜像文件刻录到Ｕ盘中。  
推荐的刻录软件UltraISO：[官网下载地址](https://cn.ultraiso.net/)  
刻录方式自行百度

## <span id="head7"> 2.3从U盘启动</span>

这一步不同的电脑型号略有不同，请自行根据自己电脑型号百度方法。注意：**务必使用UEFI方式启动**

## <span id="head8"> 2.4开始安装</span>

从U盘启动成功后，按照显示屏上的指导进行。  
当出现下面这个界面时，选择Somethine else  
![type](/static/img/type.png)

接下来这个界面上，在最下方的boot loader installation找到你的windows启动分区，即Windows Boot Manager  
![boot](/static/img/boot.png)

接下来在这个界面上找到刚才划分出的磁盘空间，并双击，按照如下配置  
![partation](/static/img/partation.png)

最后点击Install Now即可开始安装，等待安装完毕即可。

# <span id="head9"> 二、OpenCV库安装</span>

首先安装依赖，在控制台执行以下命令  

```shell
sudo apt update
sudo apt upgrade -y
sudo apt install -y htop cmake cmake-gui gcc g++ vim git wget net-tools zip unzip build-essential intltool curl libcanberra-gtk-module python python-dev python-pip python-tk python3 python3-dev python3-pip python3-tk libssl-dev libgtk-3-dev libeigen3-dev libavcodec-dev libavformat-dev libpng-dev libtiff5-dev libjpeg-dev libwebp-dev libavresample-dev libswscale-dev libavutil-dev libopenexr-dev
sudo pip3 install --upgrade pip setuptools
pip3 install --user numpy
```

随后下载[opencv3.4.5](https://github.com/opencv/opencv/archive/3.4.5.zip)和[opencv_contrib3.4.5](https://github.com/opencv/opencv_contrib/archive/3.4.5.zip)源码。如果下载速度过慢可以使用[百度网盘](https://pan.baidu.com/s/11T89p59ps4F4kBrCWiEOKw)下载，提取码: hxyt。  
下载完成后解压，并新建文件夹build用于编译，建议文件夹组织格式  
![folder](/static/img/folder.png)

进入build文件夹并打开终端执行  

```shell
cmake -D OPENCV_EXTRA_MODULES_PATH="../opencv_contrib-3.4.5/modules" ../opencv-3.4.5
```

过程中会下载一些东西，因为有某墙，下载可能失败，反复执行上述命令，直到成功为止。  
确保上述命令执行成功之后，再执行下面的命令开始编译并安装，编译时间较长，耐心等待。  

```shell
make install -j8 && sudo make install
```

不出意外，OpenCV环境配置成功

# <span id="head10"> 三、安装一款IDE</span>

推荐的IDE：clion [官方下载地址](http://www.jetbrains.com/clion/)  
该软件收费，但交大可以申请教育版免费使用。申请方法自行百度。  
如果有其他已经习惯的IDE也可以，但clion支持cmake生成项目，亲测十分好用。

# <span id="head11"> 四、安装相机驱动</span>

由于2019赛季用的是MindVision公司的相机，需要专门的驱动程序。[官网下载地址](http://www.mindvision.com.cn/rjxz/list_12.aspx?lcid=138)

