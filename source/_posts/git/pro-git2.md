---
title: Git 实用技巧
date: 2021-08-12 09:18:07
tags: Git
categories: Pro Git 学习笔记
---


## 查看提交内容
- 查看分支最后一次提交内容
```bash
$ git show branch-name
```

- 查看某次提交内容
```bash
# 使用 SHA-1
$ git show 1c002dd4b536e7479fe34593e72e6c6c1819e53b
$ git show 1c002dd4b536e7479f
$ git show 1c002d
```

<!-- more -->

- 查看某次贮存内容
```bash
$ git show stash@{2}
```

- 查看 reflog 节点内容
```bash
$ git show HEAD@{2}
```

## 引用日志 reflog
引用日志只存在于本地仓库，一个记录你在你自己的仓库里做过什么的日志。其他人拷贝的仓库里的引用日志不会和你的相同；而你新克隆一个仓库的时候，引用日志是空的，因为你在仓库里还没有操作。
- 查看引用日志
```bash
# HEAD 引用的历史，可查看历次修改和分支切换的节点
$ git reflog
8c546e1 HEAD@{2}: checkout: moving from jira/KF-17252 to release/20210816
81aa239 (origin/jira/KF-17252, jira/KF-17252) HEAD@{3}: commit: KF-17252 客厅沙发组陷入地面
8c546e1 HEAD@{4}: checkout: moving from release/20210816 to jira/KF-17252
8c546e1 HEAD@{5}: checkout: moving from jira/KF-test to release/20210816
e434430 HEAD@{6}: checkout: moving from jira/test to jira/KF-test
f5654ae (origin/jira/KF-16809, jira/KF-16809) HEAD@{7}: checkout: moving from jira/KF-16809 to jira/test
f5654ae (origin/jira/KF-16809, jira/KF-16809) HEAD@{8}: cherry-pick: KF-16809 处理书房融合出现的无线递归问题
8c546e1 HEAD@{9}: checkout: moving from jira/KF-test to jira/KF-16809
```

- 查看 reflog 节点提交内容
```bash
$ git show HEAD@{2}
```

- 输出带有 reflog 的 log 记录
```bash 
$ git log -g
commit 81aa239099066fd01badc6028a1db901ba3d3ad9 (origin/jira/KF-17252, jira/KF-17252)
Reflog: HEAD@{3} (zhangbaoyuan <zhangbaoyuan@123kanfang.com>)
Reflog message: commit: KF-17252 客厅沙发组陷入地面
Author: zhangbaoyuan <zhangbaoyuan@123kanfang.com>
Date:   Wed Aug 11 14:58:14 2021 +0800

    KF-17252 客厅沙发组陷入地面
```

## 交互式暂存
- git log -i
```bash
# 查看本地已暂存和未暂存的文件列表
$ git add -i
           staged     unstaged path
  1:    unchanged       +30/-0 src/Chapter01/Listing01.06.MultipleStatementsOneOneLine.cs
  2:     +41/-338      nothing src/Chapter19/Listing19.01.StartingAMethodThread.cs
  3:       +0/-15      nothing src/Chapter19/Listing19.02.UsingThreadPool.cs
  4:        +2/-1      nothing test.sh

*** Commands ***
  1: status       2: update       3: revert       4: add untracked
  5: patch        6: diff         7: quit         8: help
What now> 
What now> 1: 显示列表
What now> 2: 将未暂存文件添加到暂存区
What now> 3: 将已暂存文件取消暂存
What now> 5: 比如文件内修改两处,可以选择只暂存某一处
What now> 6: 等价于 git diff --cached
What now> 
What now> 5
(1/2) Stage this hunk [y,n,q,a,d,j,J,g,/,e,?]? ?
y - stage this hunk
n - do not stage this hunk
q - quit; do not stage this hunk or any of the remaining ones
a - stage this hunk and all later hunks in the file
d - do not stage this hunk or any of the later hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
e - manually edit the current hunk
? - print help
@@ -1,3 +1,7 @@
+using System;
+using System.Threading;
+using System.Threading.Tasks;
+
 namespace AddisonWesley.Michaelis.EssentialCSharp.Chapter01.Listing01_06
 {
     public class HelloWorld
(1/2) Stage this hunk [y,n,q,a,d,j,J,g,/,e,?]?
(2/2) Stage this hunk [y,n,q,a,d,k,K,g,/,e,?]? g
  1:  -1,3 +1,7          +using System;
  2:  -5,6 +9,32         +            CancellationTokenSource ts = new CancellationTo
go to which hunk? 1
@@ -1,3 +1,7 @@
+using System;
+using System.Threading;
+using System.Threading.Tasks;
+
```
也可以不必在交互式添加模式中做部分文件暂存 - 可以在命令行中使用 `git add -p` 或 `git add --patch` 来启动同样的脚本。
更进一步地，可以使用 `reset --patch` 命令的补丁模式来部分重置文件, `git stash --patch` 命令来部分贮存文件。

## 贮存
- 添加到贮存空间
```bash
$ git stash
```

- 查看贮存空间列表
```bash
$ git stash list
stash@{0}: WIP on v7.0: f9f79da test bash
stash@{1}: WIP on v7.0: f9f79da test bash
```

- 取出贮存空间内容
```
# 取出最后一次贮存
$ git stash apply

# 取出指定贮存
$ git stash apply stash@{2}
```

- 取出并删除贮存
```bash
# 最后一次贮存
$ git stash pop

# 指定贮存
$ git stash pop stash@{2}
```

- 删除贮存
```bash
# 删除最后一次贮存
$ git stash drop

# 删除指定贮存
$ git stash drop stash@{2}
```
- 从贮存处创建分支
```bash
$ git stash branch branch-name
```

## 文件搜索
- 文件内容搜索
```bash
# 搜索指定字符串
$ git grep func-string

# 显示所在行数
$ git grep -n func-string

# 在每个文件中的出现次数
$ git grep --count func-string

# 按文件分段
$ git grep --break func-string

# 保留行缩进显示
$ git grep --heading func-string
```

- 查看每一行的最后修改日期
```bash
$ git blame ErrorCode.cs
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  1) ﻿using System;
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  2) using System.Collections.Generic;
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  3) using System.Text;
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  4)
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  5) namespace YW.Services.DecorationService.Exceptions
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  6) {
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  7)     public enum ErrorCode
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  8)     {
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800  9)         // unreal issue
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 10)         GenerateFloorPlanFailed,
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 11)         GenerateAnchorDataFailed,
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 12)         GenerateTVPositionDataFailed,
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 13)         MultiFloorNotSupport,
b6ac1b46 (xmhuang      2021-07-06 09:35:43 +0800 14)         FloorPlanOptimizeFailed,
ee679f0f (xmhuang      2021-07-02 18:04:59 +0800 15)         RoomNotExist,
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 16)         AuditFailed,
31320d8a (xmhuang      2021-07-02 18:27:51 +0800 17)         UncaughtException,
4540250a (zhangbaoyuan 2021-08-09 11:39:20 +0800 18)         OutOfMemoryException,
e6807951 (zhangbaoyuan 2021-08-12 11:40:09 +0800 19)         DecorateTimeout,
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 20)     }
2d98ee36 (xmhuang      2021-06-30 14:56:05 +0800 21) }

# -------

# 设定区间
$ git blame -L 1,12 file-name

# 查看每一行的原始出处
$ git blame -C file-name

```
