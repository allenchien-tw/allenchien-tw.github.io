---
published: true
title: (EdgeX-Foundry-開發-01) --- EdgeX Foundry 簡介
layout: post
author: Allen
category: EdgeX
tags: 
  - EdgeX
comments: true
---

![edgex](/images/blog/20181009/20181009-000.png)


# EdgeX Foundry 簡介
EdgeX 的目標是要分離連接標準與應用程式的裝置介面，EdgeX 也因為獨立平臺和鬆散耦合的微
服務，獲得更好的彈性與擴展性，並能使用通用API將不同語言開發的服務整合在一起。

- South Side: All IoT objects
- North Side: The Cloud


# 最新版 EdgeX California 版本
EdgeX California 的主要新功能旨在提高安全性，基於 Kong 的新反向代理要求任何 EdgeX 微服
務的外部用戶端，載入 EdgeX API 前先身分認證，這將有助於保護 REST API 通訊並保護儲存。

California 版的另一個重大變化是將開發平台從原本 Java 語言移轉至 Go 語言。

Go 語言只是一種基準參考語言，開發人員可一起使用相同 API 與其他語言，除 Go for the
Device Service SDK 外，該項目還將支援 C 語言。

從下圖看出，使用 Go 語言後 Footprint 由 267MB 縮小為 42MB 

![edgex](/images/blog/20181009/20181009-001.png)


# EdgeX Foundry 架構
![edgex](/images/blog/20181009/20181009-002.png)

### Core Service (CS) Layer

- Core data Service : 收集由 South Side Object 所收到的資料
- Command Service : 將 North Side 控制命令送到 South Side Objects
- Metadata Service : South Side Object 的 Meta Data
- Registry and Configuration : 註冊或是配置 Micro services

### Supporting Service (SS) Layer

- 主要是增加 Edge 智能方面的 micro services

- Logging, Scheduling, Data Clean, Rule Engine, Alert, Notification

### Export Service (ES) Layer

- 負責將 South Side 資料傳送到 North Side

- 通知 REST API 位置與 JSON 格式

### Device Service (DS) Layer

- 提供 SDK 整合不同 Device 通訊介面，讓不同 Device 可以與 Core Service 溝通

### Security Infrastructure

- 提供資料保護與不同 Device 的命令

### System Management

- 負責 Microservices 的 installation, upgrade, start, stop, minotring

