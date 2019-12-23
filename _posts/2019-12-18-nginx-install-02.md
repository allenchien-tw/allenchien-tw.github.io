---
published: true
title: (Nginx-架設-02) --- Nginx 啟動教學
layout: post
author: Allen
category: Nginx
tags: 
  - Nginx
  - 架設
  - 安裝
  - 教學
comments: true
---

![logo](/images/blog/20191218/20191218-001.png)

# Nginx 確認是否安裝成功

```console
$ nginx -v

nginx version: nginx/1.16.1
```


# Nginx 啟動

```console
$ nginx
```
結果如下圖
![nginx](/images/blog/20191218/20191218-002.png)

# Nginx 停止與其他操作

```console
nginx -s stop    (停止)
nginx -s quit    (暫時停止)
nginx -s reload  (重新刷新 configure)
nginx -s reopen  (重新開啟 log 檔)
```


