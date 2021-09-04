---
title: modified () new commits
date: 2021-09-04 17:17:50
tags: error
categories: error
---

## 异常内容如下
```bash
AdminBao@WIN-7QEOL1RIOU2 MINGW64 /f/MyBlog (develop)
$ git status
On branch develop
Your branch is up to date with 'origin/develop'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   .deploy_git (new commits)

no changes added to commit (use "git add" and/or "git commit -a")

AdminBao@WIN-7QEOL1RIOU2 MINGW64 /f/MyBlog (develop)
$ git diff
diff --git a/.deploy_git b/.deploy_git
index 5fa1603..fcc41b1 160000
--- a/.deploy_git
+++ b/.deploy_git
@@ -1 +1 @@
-Subproject commit 5fa1603b92440788bfbcbccb8fe539ad58a6ae9d
+Subproject commit fcc41b107339e9ceb3ced6b82b891957cd734995
```

## 解决方法
```bash
$ cd .deploy_git
$ Git reset --hard 5fa1603b92440788bfbcbccb8fe539ad58a6ae9d
$ cd ..
$ git status
# 干净了
```
