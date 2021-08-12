---
title: DOS 常用命令行
date: 2021-08-12 16:24:10
tags: DOS
categories: DOS 基础
---

- 创建文件夹
```bash
$ md 123
$ mkdir 123
```

- 查看文件列表
```bash
# 显示文件列表
$ dir

# 列出各子级文件,就很炫
$ dir /s data

# 只列出文件名,简短
$ dir /b
```

<!-- more -->

- 路径跳转
```bash
# 进入 F 盘
$ f:
$ cd /d f:

# 进入指定路径
$ cd /d f:\data

# 进入当前目录的子目录
$ cd data

# 进入上一级
$ cd ..

# 回到当前盘根目录
# 空格可省略，后面可跟随文件夹
$ cd \
$ cd \data
```

- 删除文件夹
```bash
# 删除文件夹 - 不能删除文件，可删除文件夹下文件
$ rd 123
$ rmdir 123

# 递归删除子文件夹
$ rd 123 /s
```

- 重命名和移动
```bash
# 123 文件夹改名为 12
$ move 123 12
```

- 文件复制
```bash
# 复制文件 - 不能复制文件夹
$ copy 123 12
```

- 文件删除
```bash
$ del file-name

# 删除所有文件
$ del *.* 

# 强制递归删除所有文件和目录
$ del /s *.*
```

- 批量更改文件名
```bash
# 批量更改文件名
$ ren *.jpg *.png

# 等价于
$ copy *.jgp *.png
$ del *.jpg
```

- 查看文件内容
```bash
# 只能看一部分，文件很长则只能看最上面一部分
$ type file-name

# 分页查看文件内容
$ more file-name
```

- 打开文件夹
```bash
# 打开文件夹
$ explorer

# 打开指定路径文件夹
$ explorer f:\MyWork\data
```

- 启动任务管理器
```bash
$ taskmgr
```

- 打开系统自带软键盘
```bash
$ osk
```

- 启动计算器
```bash
$ calc
```

- 启动控制面板
```bash
$ control
```

- 定时关机
```bash
# 设置半小时后关机
$ shutdown -s -t 1800

# 取消定时关机
$ shutdown -a
```

- 查看运行中的进程
```bash
$ tasklist
```

- 查看IP信息
```bash
$ ipconfig
```
