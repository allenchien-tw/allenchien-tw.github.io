---
published: true
title: (Python-Pandas-01) --- 學習 Pandas 使用 Time Series 結構
description: 使用 Python Pandas 的 Time Series 功能，並說明 iloc 與 loc 區別
layout: post
author: Allen
category: Pandas
type: Blog
image: /images/blog/20190627/20190627-000.png
tags: 
  - Python
  - Pandas
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

## 3. 一次設定所有值
```python
s = pd.Series(2, index=date)
```
![book](/images/blog/20190627/20190627-003.png)

## 4. 使用 loc() 查找某一個值
```python
date = pd.date_range('20180101', periods=6)
s = pd.Series([1,2,3,4,5,6], index=date)
s.loc['20180104']
```
![book](/images/blog/20190627/20190627-004.png)

```python
s.loc['20180102':'2018-01-04']
```
![book](/images/blog/20190627/20190627-005.png)

## 5. 使用 iloc() 查找某一個值
```python
s.iloc[1]
```
![book](/images/blog/20190627/20190627-006.png)

```python
s.iloc[1:4]
```
![book](/images/blog/20190627/20190627-007.png)

## 6. 數值計算
```python
print(s)
r1 = s.max()
print(r1)
r2 = s.min()
print(r2)
r3 = s.mean()
print(r3)
r4 = s.std()
print(r4)
r5 = s.cumsum()
print(r5)
r6 = s.cumprod()
print(r6)
```
![book](/images/blog/20190627/20190627-008.png)


## 7. 整體序列計算
```python
print(s)
print(s + 1)
print(s - 1)
```
![book](/images/blog/20190627/20190627-009.png)
```python
print(s * 2)
print(s / 2)
print(s > 3)
print(s < 3)
```
![book](/images/blog/20190627/20190627-010.png)

## 8. 繪圖
```python
%matplotlib inline
s.plot()
```
![book](/images/blog/20190627/20190627-011.png)