---
published: true
title: 將 Flask 建立為 Linux 服務教學
layout: post
author: Allen
category: Nginx
tags: 
  - Linux
  - Flask
  - nohup
  - systemd
  - 教學
comments: true
---

![logo](/images/blog/20200107/20200107-000.png)

# 前言
原本是單純建立好 Flask 程式，可是離開遠端SSH後，無法繼續執行 Flask，於是找到 nohup 的方式可以執行為背景程式，同時離開 SSH 後，仍然可以繼續執行


# 使用 Nohup
執行下列程式，離開後仍然可以執行
```console
nohup python api.py &
```

重新登入後執行，仍然可以看到之前的程式程序
```console
ps aux
```
![ps]](/images/blog/20200107/20200107-001.png)


# 使用 Linux systemd 建立 service

## STEP-1 : 撰寫 service
撰寫 service 文件

```console
[Unit]
Description=abc service

[Service]
Type=simple
WorkingDirectory=/home/allen/abc
ExecStart=/home/allen/miniconda3/envs/abc/bin/python api.py
Restart=always

[Install]
WantedBy=multi-user.target
```

## STEP-2 : 啟動 Service
使用 start 啟動 service 之後，無論如何 kill process 都可以重新啟動

```console
sudo systemctl start abc.service
```


## STEP-3 : 停止 Service
```console
sudo systemctl stop abc.service
```