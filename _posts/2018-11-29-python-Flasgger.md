---
published: true
title: (Python-學習-09) --- 使用 Flassger 自動產生 API 文件
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20181129/20181129-000.png)

# 為何需要自動產生 API 文件 ?

這是源自於工程師的天性，懶得寫文件，我們常常一接到專案，就開始埋頭寫 code，修 bug ，偶爾會先寫 Design Document 但是常常到後來 Document 與實際程式碼，相差甚遠。
造成後續維護與交接時，還需要再重寫文件。

經過多次專案的經驗，發現工程師比較願意再寫 code 時順便改一下註解，所以如果能夠透過註解內容產生文件，這樣文件可以與 code 的版本趨於一致。
傳統使用 C++ 開發 Windows 應用程式時，我都會使用 [Doxygen](http://www.doxygen.nl/) 但是開發 RESTful APIs 就發現 [Flasgger](https://github.com/rochacbruno/flasgger)  這個好用的工具。


# Swagger 簡介

Swagger 是一個大型的 API 開發者的工具框架，該框架提出了一個編寫OpenAPI的規範（命名為OAS），並且 Swagger 可以跨整個API生命週期進行開發，從設計和文檔到測試和部署。
透過 OpenAPI 規範， Swagger 能夠自動產生 Web 版的 API 文件，並且可提供網頁 UI 進行 API 測試



