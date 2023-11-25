---
layout: _posts
title: github代理加速配置
date: 2023-11-25 22:15:37
category: 
  - 代理
  - github
tags:
  - git
  - github代理
---
## 终端命令行
支持终端命令行git clone，wget，curl等工具下载
支持 `raw.githubusercontent.com `, `gist.github.com `, `gist.githubusercontent.com` 文件下载.
**注意**：不支持 SSH Key 方式 git clone 下载.
## 拉取 git clone
git clone https://mirror.ghproxy.com/https://github.com/xxx

## git clone 私有仓库
Clone 私有仓库需要用户在 [Personal access tokens](https://github.com/settings/tokens) 申请 Token 配合使用.
git clone https://user:your_token@mirror.ghproxy.com/https://github.com/your_name/your_private_repo
push 提交代码，也是要带token

## wget & curl
wget https://mirror.ghproxy.com/https://github.com/stilleshan/ServerStatus/archive/master.zip
wget https://mirror.ghproxy.com/https://raw.githubusercontent.com/stilleshan/ServerStatus/master/Dockerfile
curl -O https://mirror.ghproxy.com/https://github.com/stilleshan/ServerStatus/archive/master.zip
curl -O https://mirror.ghproxy.com/https://raw.githubusercontent.com/stilleshan/ServerStatus/master/Dockerfile

参考来源：https://mirror.ghproxy.com/