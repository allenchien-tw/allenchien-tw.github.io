---
published: true
title: (Nginx-架設-04) --- Nginx 安裝 SSL 憑證，支援 HTTPS 
layout: post
author: Allen
category: Nginx
tags: 
  - Nginx
  - 架設
  - 安裝
  - 教學
  - SSL
  - HTTPS
  - 免費
comments: true
---

![logo](/images/blog/20191220/20191220-000.png)

# STEP-1. 上傳憑證檔案至網站目錄中
![nginx](/images/blog/20191220/20191220-001.png)



# STEP-2. 開啟 Nginx 設定檔，指向 SSL 憑證路徑
![nginx](/images/blog/20191220/20191220-002.png)

加入下列幾行
```console
# 2019-12-23: add SSL CA
listen  443 ssl;
ssl_certificate /xxx/ca/certificate.crt
ssl_certificate_key /xxx/ca/private.key
```
  

# STEP-3. 重新啟動 Nginx 就可以看到憑證
![nginx](/images/blog/20191220/20191220-003.png)