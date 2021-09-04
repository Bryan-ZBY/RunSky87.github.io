---
title: GitHub 提示需要使用token代替个人密码
date: 2021-09-04 16:49:46
tags: error
categories: error
---

## git push 时报错如下
```bash
$ git push
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: Authentication failed for 'https://github.com/RunSky87/RunSky87.github.io.git/'
```

## 官方文档说明文档
- [创建个人访问令牌](https://docs.github.com/cn/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token)
- 出于安全原因，在离开页面后，您将无法再次看到令牌，所以需要保存好。
- 个人访问令牌只能用于 HTTPS Git 操作。 如果您的仓库使用 SSH 远程 URL，则需要将远程 URL 从 SSH 切换到 HTTPS。
- 使用凭据：password:token.


