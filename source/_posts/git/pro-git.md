---
title: Git基本操作
date: 2021-08-10 18:35:32
tags: Git
categories: Pro Git 学习笔记
---

## 基础操作
- 初始化仓库
```bash
$ git init
```

- 仓库克隆
```bash
$ git clone git-url

# 自定义本地仓库名
$ git clone git-url local-name
```

- 文件跟踪
```bash
$ git add file-name

# 取消文件的跟踪
$ git reset HEAD file-name
```

<!-- more -->

- 文件提交
```bash
$ git commit -m commit-info

# 暂存并提交已跟踪文件
$ git commit -a -m "commit info"

# 向提交中补充文件
$ git commit -m 'commit info'
$ git add new-file
$ git commit --amend
```

- 查看文件状态
```bash
$ git status


# 简洁输出
$ git status -s
```

- 撤销文件的修改
```bash
$ git checkout file-name
```

- 查看修改内容
```bash
$ git diff

# 查看已暂存的文件
$ git diff --cache

# 比较文件差异
$ git difftool
```

- 移除文件
```bash
$ git rm file-name

# 强制删除已改动文件
$ git rm -f file-name

# 取消跟踪,但保留文件
$ git rm --cached file-name 
```

- 文件改名或移动
```bash
$ git mv file-from file-to

# 等同于
$ mv file-from file-to
$ git rm file-from
$ git add file-to
```

## Log 历史记录
- 查看提交历史
```bash
$ git log

# 查看最近两条 
$ git log -2

# 查看每次提交内容差异
$ git log -p

# 查看提交统计信息
$ git log --stat

# 一行显示提交记录
$ git log --oneline

# ASCII 字符串显示记录
$ git log --graph

# 最近两周内的提交
$ git log --since=2.weeks
```

- 搜索记录
```bash
# 指定作者的提交
$ git log --author=user-name

# 搜索指定提交commit内容
$ git log --grep=commit-word

# 搜索指定文件的提交记录
$ git log file-name

# 搜索指定文本内容的提交
$ git log -S func-string
```

## 远程仓库
- 查看远程仓库
```bash
# 查看远程仓库简称
$ git remote

# 查看远程仓库链接
$ git remote -v

# 查看详细信息
$ git remote show remote-name
```

- 添加远程仓库
```bash
$ git remote add remote-name remote-url
```

- 远程仓库简称重命名
```bash
$ git remote rename old-name new-name
```

- 删除远程仓库关联
```bash
$ git remote rm remote-name
```

- 获取远程信息
```bash
$ git fetch
```

- 拉取最新代码
```bash
$ git pull

# 等同于
$ git fetch
$ git merge
```

- 推送代码
```bash
# 前提是已经配置过
$ git push

# 提交到指定分支
$ git push remote-name branch-name

# 提交到命名不同的分支上
$ git push remote-name local-branch-name:remote-branch-name
```

## Tag 标签
- 查看标签列表
```bash
$ git tag

# 筛选标签
$ git tag -l 'tag-word'
```

- 创建标签
```bash
# 轻量标签
$ git tag tag-name

# 附注标签
$ git tag -a tag-name -m 'tag info'

# 补充标签
$ git tag -a tag-name commit-hash
```

- 查看标签详细信息
```bash
$ git show tag-name
```

- 提交标签
```bash
# 提交一个标签
$ git push origin tag-name

# 提交所有标签
$ git push origin --tags
```

- 从指定标签检出分支
```bash
$ git checkout -b branch-name tag-name
```

## Git 分支
- 创建分支
```bash
# 创建分支，但不跳转
$ git branch new-branch-name

# 创建分支并跳转
$ git checkout -b new-branch-name

# 从远程拉取分支并自定义本地名称
$ git checkout -b local-branch-name remote-name/branch-name
```

- 分支切换
```bash
$ git checkout branch-name
```

- 分支合并
```bash
$ git merge another-branch-name
```

- 本地分支删除
```bash
$ git branch -d branch-name

# 强制删除
$ git branch -D branch-name

# 删除远程分支
$ git push origin --delete branch-name
```

- 处理冲突
```bash
# 图形化工具处理完会自动将冲突标记为已解决
# 实际上对文件执行 git add 后，即将其存入暂存区后
# 它的冲突标记就会被改为已解决
$ git mergetool
```

- 查看分支列表
```bash
# 查看本地分支列表
$ git branch

# 查看远程分支列表
$ git branch -r

# 查看已经合并进当前分支的分支列表
$ git branch --merged

# 查看未合并入当前分支的分支列表
$ git branch --no-merged

# 查看每个分支最后一次提交内容
$ git branch -v

# 查看本地分支和远程分支的对应关系
$ git branch -vv
```
