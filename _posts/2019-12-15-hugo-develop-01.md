---
published: true
title: (Hugo-開發-01) --- 靜態網頁產生器比較
layout: post
author: Allen
category: Hugo
tags: 
  - Hugo
  - 前端
  - 教學
comments: true
---

![book](/images/blog/20191215/20191215-000.png)

# 前言
最近想要另外自架新的網站，但是想到傳統架網站需要先安裝 Web Server, Database, CMS 等一堆步驟就覺得非常麻煩。



# Github 搭配 Jekyll
自從使用 Github 搭配 Jekyll 的方式，讓簡單的 markdown 文件自動產生成網頁後，就回不去傳統的架站模式。
雖然 Github 使用方便並且應用在 Blog 功能非常足夠，但是針對服務型的網站，並且後續還會有新個擴充需求來說。
這個方式已經不符合所需，所以又燃起再找其他方案的想法



# Hugo 與 Jekyll 比較
由於目標明確，所以使用 Google 關鍵字搜尋 *markdown static page* 很快就找到 Jekll 與 Hugo 兩大方案與比較文章。



### Jekyll 特色
- 優點
  - 免費
  - 簡單易用
  - Github Pages 支援
- 缺點
  - 隨著網站內容的增長，構建過程變得非常慢
  - 很多插件都過時了



### Hugo 特色
- 優點
  - 免費
  - 因為使用 Go 語言，超快的速度
  - 引擎和速度優化
- 缺點
  - 主題使用 Go 模板，需要熟悉 Go 來創建主題
  - 插件較少



因為沒有比較少接觸 Go 語言，也許可以透過這個方式順便再多學習一種新語言，接下來後續文章會持續記錄如何學習 Hugo 