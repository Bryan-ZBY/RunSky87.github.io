---
title: Windows上安装Linux子系统
date: 2021-09-04 12:18:27
tags: linux
categories: linux
---

## 下载子系统
- 下载网址 [download](https://docs.microsoft.com/en-us/windows/wsl/install-manual)

## 启用安装功能
- "控制面板" ---> "卸载程序" ---> "启用或关闭Windows功能"
- 启用 "适用于Linux的windows子系统"

<!-- more -->

![test](/imgs/boayuan20210904122735.png)

## 安装子系统
- 打开下载得到的appx文件,解压缩(如果不能解压缩就把后缀修改为zip再解压缩)
- 要把解压缩后的文件放到一个合适的地方
- 安装其实只是注册,因此安装好后的子系统的文件,就一直放在这里了
- 解压的位置就是安装位置
- 点击解压缩目录中的exe文件,会自动注册
- 按照提示输入用户名和密码

## 使用方式
- 启动的时候,在命令行中输入bash就可以启动.
- 另外存放在linux系统,点击exe也可以启动.
- 在文件夹路径框输入 bash 可以在指定文件夹位置启动.
