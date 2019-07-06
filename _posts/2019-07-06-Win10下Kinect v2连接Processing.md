---
layout:		post
title:		Win10下Kinect v2连接Processing
subtitle:	用Processing连接Kinect进行交互展示
date:		2019-07-06
author: 	Echo
header-img: 	img/2019-07-06/Kinect.png
catalog:	true
tags: 
    - Kinect
    - Processing
---

> 最近在使用 Kinect 完成一个艺术装置。首先需要用 Kinect 捕捉头部的运动数据，继而用 Processing 处理数据，然后将处理好的数据发送给控制端进行装置的控制。

## 0 写在前面

做交互装置的同学有时会用到 Kinect，目前的版本应该是 v2，由于是微软出品，所以建议在 Windows 系统上进行部署，以免出现水土不服的状况。来自一个折腾了两天Mac都没搞定的程序员的忠告 : ）

做交互装置的同学有时会用到 Processing，因为他可以很方便地和 [Arduino](<https://www.bilibili.com/video/av11662037/>?_blank) 进行通信，从而控制硬件，比如舵机。

所以接下来简单描述一下如何在 Win10 上搭建 Processing 3.5.3 开发 Kinect v2的环境。

## 1 软硬件需求

### 1.1 硬件

* 一台 Kinect V2 ：相信点开这个博客的时候你已经有一台Kinect了，否则前方右转出门不送
* 带 USB 3.0 接口的 64 位电脑：划重点划重点 **64 位**和 USB **3.0**（就是你电脑上蓝色的 USB 接口），这一切都是为了满足Kinect V2的高速高清图像传输

### 1.2 软件

在满足了硬件需求之后，就可以开始了解软件环境了。

* Win8 以上的系统：这里使用 Win10，其实 Win8， Win8.1的也可以

* [Kinect SDK v2](<https://developer.microsoft.com/en-us/windows/kinect>)：这个是 Kinect v2 在 windows 系统的开发库，必需品
* [Processing 3.x](<https://processing.org/download/>)：这里使用最新版本 3.5.3，有了它就可以接受并处理 Kinect 传来的数据了
* 更新显卡驱动：[检查显卡驱动](<https://jingyan.baidu.com/article/2c8c281da97bab0008252af3.html>)，如果已经是最新的就 OK，否则需要更新
* [检查 Direct X 版本](<https://support.microsoft.com/zh-hk/help/15061/windows-which-version-directx>)：只有较新的 Direct X 套件才能支持一些 3D 的显示

## 2 开始搭建

在满足硬件需求的基础上，请逐一检查或安装软件环境。

若上述操作全部成功，那就万事俱备，只欠东风了，所谓东风，就是在 Processing 中开发 Kinect 的库： [**KinectPV2**](<https://github.com/ThomasLengeling/KinectPV2>)，安装该库有两种方法：自动安装和手动安装。

### 2.1 自动安装（推荐）

保证有网的前提下，打开 Processing，在`速写本->引用库文件->添加库文件`中搜索 Kinect 应该就会有 Kinect v2 for Porcessing，直接安装即可。

![add Lib](<https://raw.githubusercontent.com/Echo-Ji/Echo-Ji.github.io/master/img/2019-07-06/addLib.png>)

![search for kinectPV2](<https://raw.githubusercontent.com/Echo-Ji/Echo-Ji.github.io/master/img/2019-07-06/search.png>)

### 2.2 手动安装

在项目 Github 的 releases 标签中下载最新版本，然后将解压后的文件拷贝到 Processing 的库文件夹中，一般默认在**我的文档**里`/Processing/libraries`下，找不到的话可以在 Processing 主界面打开`文件->偏好设定`，弹窗的顶部就是**速写本位置**，在此文件夹下找到`libraries`文件夹放进去就好，如果是首次添加第三方库可能需要手动创建`libraries`文件夹。



虽然 Github 的 releases 里停更了，但是我们依旧可以通过第一种方式获取到最新版本的库。

到这里，环境就算搭建好了。可以通过`文件->返利程序->Contributed Librsries`找到示例程序，运行并查看效果​。​Enjoy​~:rocket: