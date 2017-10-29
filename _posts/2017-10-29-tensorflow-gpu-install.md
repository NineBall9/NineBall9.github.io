---
layout: post
title: tensorflow-gpu的安装
description: tensorflow-gpu1.2.0, cuda v8.0, cudnn 5.1
category: blog
---

#win10+python3.5+tensorflow-gpu-1.2.0安装

##1、安装前准备

先下好anaconda，cuda8.0和cudnn5.1(下载地址https://pan.baidu.com/s/1miBc2VY，密码 5aoc）

##2、安装tensorflow

cpu版本：pip install tensorflow
gpu版本：pip install tensorflow-gpu

##3、安装cuda8.0

这一步很简单，直接解压就好，安装完成后在命令行输入nvcc -V验证是否安装成功。

##4、安装cudnn5.1

这一步很关键，安装完之后会出现三个文件夹，每个文件夹下对应一个文件，将这三个文件放进对应cuda8.0的文件夹中，同时修改path为这cuda8.0中对应的三个目录，bin,include,lib/x64

##5、验证tensorflow-gpu是否安装成功

在命令行中输入python,然后import tensorflow
发现会出现一堆错误，主要是"DLL LOAD FAILED， 找不到指定模块"，试了网上各种方法，有的说缺少mvcp140.dll文件的，有的说cuda版本不对的，应该是V8.0.44却安装了V8.0.60，还有的说环境变量没设置好的。
反正试了一万种方法，在https://stackoverflow.com/questions/42011070/on-windows-running-import-tensorflow-generates-no-module-named-pywrap-tenso中找到了答案，
结果是tensorflow版本太高了导致cudnn版本不匹配，安装的是TensorFlow1.3.0需要cudnn6，却用的cudnn5.1.然后卸了TensorFlow1.3.0，装上TensorFlow1.2.0，最终运行正确。
废了九牛二虎之力，总算把这玩意整好了。

##什么东西都会有一个正确的方法打开，不要畏惧困难，方法一直都存在，就看你能不能找到了。

最后放一张运行正确的图，表达一下我的ease。
![](images/1.gif)
