---
title: apt install 报错：Unable to locate package expect
date: 2021-09-04 12:02:19
tags: error
categories: error
---

- 报错内容如下
```bash
yuanbao@WIN-7QEOL1RIOU2:/mnt/f/ShellTest$ sudo apt install expect
[sudo] password for yuanbao:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package expect
```

- 解决方法如下
```bash
yuanbao@WIN-7QEOL1RIOU2:/mnt/f/ShellTest$ sudo apt-get update
yuanbao@WIN-7QEOL1RIOU2:/mnt/f/ShellTest$ sudo apt install expect
```

