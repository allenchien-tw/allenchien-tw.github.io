---
published: true
title: (Python-資料科學-01) --- 學習 Pandas Time Series
layout: post
author: Allen
category: 資料科學
type: Blog
image: /images/blog/20190627/20190627-000.png
tags: 
  - Python
comments: true
---

![book](/images/blog/20190627/20190627-000.png)

# 為何 Pandas ?
Pandas 是 Python 語言中的一個資料分析工具，提供高效能，簡易使用的資料格式，讓開發人員能快速操作資料與分析。
Pandas 主要提供兩種資料結構 :
- Time Series: 時間序列結構，Time-Value 組成的結構
- DataFrame: 是屬於 Time Series 的延伸，相同時間可以搭配多組資料，成為多維結構

# Time Series 結構
接下來我們來看看它有哪些應用

## 1. 建立第一個時間序列
```python
import pandas as pd
s = pd.Series([1,2,3,4])
```
![book](/images/blog/20190627/20190627-001.png)

## 2. 加上時間 TS
```python
date = pd.date_range('20180101', periods=6)
s = pd.Series([1,2,3,4,5,6], index=date)
```
![book](/images/blog/20190627/20190627-002.png)