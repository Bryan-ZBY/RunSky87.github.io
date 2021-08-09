---
title: Hello Hexo World
date: 2021-08-09 16:20:11
tags: hexo
categories: hexo
---

## 初始化准备
### 安装 hexo
```bash
$ npm install -g hexo-cli
$ hexo init blog
$ cd blog
$ npm install
```

## 文件系统
### 创建新文档
``` bash
# 创建新文档
$ hexo new "My New Post"

# 创建指定路径的文档: _ports/hexo/test.md
$ hexo new --path hexo/test "title"
$ hexo new -p hexo/test "title"
```

### 使用文档模板
```bash
# 使用 photo.md 作为模板生成新文档
hexo new photo "new title"
```

### 生成静态网页文件
``` bash
$ hexo generate
$ hexo g
```

### 清除缓存文件
```bash
# 一般在更改文件或者风格的时候需要清除
$ hexo clean
```

### 本地启动服务器查看效果
``` bash
# 默认开启 4000 端口
$ hexo server
$ hexo s

# 指定端口
$ hexo s -p 5000
```

### 部署网站命令
``` bash
# 将之前生成的静态网页文件上传到github
$ hexo deploy
$ hexo d
```

### 更新网页文件并部署到网站
```bash
$ hexo d -g
$ hexo g -d
```

### 部署网站
```bash
$ npm install hexo-deployer-git
$ vim _config.yml
# 添加如下内容
deploy:
  type: git
  repo: git@github.com:RunSky87/RunSky87.github.io.git
  branch: master

$ hexo g

# 下行命令可以直接将生成的网页内容上传到github的master分支
$ hexo deploy
```

