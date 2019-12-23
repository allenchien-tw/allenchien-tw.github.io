---
published: true
title: (Nginx-啟動-02) --- Nginx 啟動
layout: post
author: Allen
category: Nginx
tags: 
  - Nginx
comments: true
---

![logo](/images/blog/20191218/20191218-001.png)

# 可以使用下列命令進行 Nginx 的啟動與停止

```console
nginx -s stop    (停止)
nginx -s quit    (暫時停止)
nginx -s reload  (重新刷新 configure)
nginx -s reopen  (重新開啟 log 檔)
```


