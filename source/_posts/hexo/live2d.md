---
title: 在hexo博客添加live2d模型
date: 2021-08-10 10:48:00
tags: hexo
categories: hexo
---

## 安装依赖包
```bash
npm install --save hexo-helper-live2d
```

## 引入模型
```bash
npm install --save live2d-widget-model-koharu
```

<!-- more -->

## 配置示例
```yml
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-koharu
  display:
    position: left
    width: 150
    height: 300
  mobile:
    show: true
  react:
    opacity: 0.7
```
