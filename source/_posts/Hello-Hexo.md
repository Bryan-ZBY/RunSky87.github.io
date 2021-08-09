---
title: Hello Hexo
date: 2021-08-09 14:45:57
tags:
---

## 初始化
```bash
$ hexo init blog
$ cd blog
$ hexo server
```
默认打开 4000 端口查看效果。

## 部署到GitHub插件和配置
```bash
npm install hexo-deployer-git

# open file ./_config.yml
deploy:
  type: git
  repo: git@github.com:RunSky87/RunSky87.github.io.git
  branch: master 
```


## 部署到GitHub命令
```
hexo deploy
```

## 开发流程
master 分支用于部署网站
dev 分支用于写博客
