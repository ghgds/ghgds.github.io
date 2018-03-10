---
layout: post
title: 'Ubuntu下与Windows的文件互传及WSL的中文显示'
date: 2018-03-10
author: Twioo
tags: Ubuntu WSL
---

## Ubuntu下与Windows的文件互传及WSL的中文显示

### Ubuntu下与Windows的文件互传
使用WSL时，有时需要与Windows环境互传文件。而直接拷贝的方式会出现权限问题，官方也提示不要在Windows环境下修改WSL内的文件。
    题外话：实际上，经过本人测试，使用Notepad++直接修改WSL内的文件是可行的，前提是文件已经在WSL下存在。如果是创建的，则需要在Ubuntu环境下使用chmod增加权限。
    而安装使用lrzsz则可以实现两个环境的便捷文件传递。
    安装：`sudo apt-get install lrzsz`
    向Ubuntu上传：`rz` ，随即会跳出文件选择窗口，确定即可上传到当前目录（本人使用Xshell方式）
    下载到Windows：`sz 文件名`

### WSL的中文显示问题
    Win10下默认安装的WSL是英文环境，使用`locale`或`echo $LANG`查看LANG为空，因此无法正常显示中文文件名。
    因此，首先查看系统是否有安装，使用`locale -a`查看
    之后设置：`sudo update-locale LANG=en_US.UTF-8`即可，设置后仍为英文环境，但是可以正常显示中文。

    如果要更改为中文环境 `sudo update-locale LANG=zh_CN.UTF-8`，没有的话需要安装`sudo locale-gen zh_CN.UTF-8` 或 `sudo apt-get install language-pack-zh-hans` （此安装方式为网上方案，未验证）


