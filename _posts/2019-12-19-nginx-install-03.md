---
published: true
title: (Nginx-架設-03) --- Nginx 安裝免費 SSL 支援 HTTPS
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

![logo](/images/blog/20191219/20191219-000.png)

# SSL for Free

目前因為 Google Search 政策，要求網站必須支援 HTTPS 網路協定才能讓網站的搜尋排名能夠提高。
但是，針對剛開始架站的人來說，在網站人數還不夠多時，也不太能付出太多成本購買很貴的 SSL 憑證。
幸運的事，我在網路上查到 [這篇文章](https://free.com.tw/ssl-for-free/) ，剛好有介紹到 [SSL For Free](https://www.sslforfree.com/) 這個好用的資源

透過 [SSL For Free](https://www.sslforfree.com/) 線上工具，讓你從網站上取得免費 SSL 憑證，然後再匯入到 Nginx 中
可以參考之前的文章

[(Nginx-架設-01) --- Nginx 安裝教學](https://allenchien-tw.github.io/blog/2019/12/17/nginx-install-01)
[(Nginx-架設-02) --- Nginx 啟動教學](https://allenchien-tw.github.io/blog/2019/12/18/nginx-install-02)


# 取得免費 SSL 憑證

在線上工具中，輸入你的網站 domain，並按下 *Create Free SSL Certificate* 按鈕
![nginx](/images/blog/20191219/20191219-001.png)

在下一頁中，網站會要求你進行驗證，確認你是網站管理員，我採用手動驗證的方式
![nginx](/images/blog/20191219/20191219-002.png)