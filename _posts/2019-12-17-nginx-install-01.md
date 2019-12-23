---
published: true
title: (Nginx-安裝-01) --- Nginx 安裝
layout: post
author: Allen
category: Nginx
tags: 
  - Nginx
comments: true
---

![logo](/images/blog/20191217/20191217-000.png)

# 安裝準備
先安裝必要的 Ubuntu 套件

```console
sudo apt install curl gnupg2 ca-certificates lsb-release
```

使用下列命令，確認 APT 的正確資源來源
```console
echo "deb http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list
```

匯入 Nginx 官方金鑰
```console
curl -fsSL https://nginx.org/keys/nginx_signing.key | sudo apt-key add -
sudo apt-key fingerprint ABF5BD827BD9BF62
```

# 安裝 Nginx 
安裝 Nginx 
```console
sudo apt update
sudo apt install nginx
```

