---
published: true
title: (Nginx-架設-03) --- Nginx 下載免費 SSL 憑證
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


- [(Nginx-架設-01) --- Nginx 安裝教學](https://allenchien-tw.github.io/blog/2019/12/17/nginx-install-01)
- [(Nginx-架設-02) --- Nginx 啟動教學](https://allenchien-tw.github.io/blog/2019/12/18/nginx-install-02)

</br></br>

# 取得免費 SSL 憑證

## STEP-1 在線上工具中，輸入你的網站 domain，並按下 *Create Free SSL Certificate* 按鈕
![nginx](/images/blog/20191219/20191219-001.png)

</br>

## STEP-2 在下一頁中，網站會要求你進行驗證，確認你是網站管理員，我採用手動驗證的方式
![nginx](/images/blog/20191219/20191219-002.png)

![nginx](/images/blog/20191219/20191219-003.png)

</br>

## STEP-3 從網站下載 3 個檔案
![nginx](/images/blog/20191219/20191219-006.png)

</br>

## STEP-4 在 server 上的 nginx 目錄中建立 *.well-known* 與 *acme-challenge*  檔案夾
![nginx](/images/blog/20191219/20191219-004.png)

![nginx](/images/blog/20191219/20191219-005.png)

</br>

## STEP-5 並且把剛剛從網站下載的網站，上傳到 *acme-challenge*  檔案夾中
![nginx](/images/blog/20191219/20191219-007.png)

</br>

## STEP-6 驗證成功後，按下下載憑證檔案
![nginx](/images/blog/20191219/20191219-008.png)

</br>

## STEP-7 Let’s Encrypt 憑證簽發每 90 天必須更新（renew）一次，SSL For Free 提供訂閱通知的機制，你可在稍後填入自己的 Email，在憑證過期前就會收到電子郵件通知。
![nginx](/images/blog/20191219/20191219-009.png)