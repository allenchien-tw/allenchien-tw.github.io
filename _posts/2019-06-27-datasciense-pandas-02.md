---
published: true
title: (Python-Pandas-02) --- 學習 Pandas 使用 DataFrame 結構
description: 使用 Python Pandas 的 DataFrame 功能，並說明 iloc 與 loc 區別
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

# DataFrame 結構
DataFrame 結構其實就是 Time Series 衍生，它的應用與 Time Series 極為相似

## 1. 建立第一個 DataFrame
```python
s1 = pd.Series([1,2,3,4,5,6], index=date)
s2 = pd.Series([5,6,7,8,9,10], index=date)
s3 = pd.Series([11,12,5,7,8,2], index=date)

dictionary = {
    'c1': s1,
    'c2': s2,
    'c3': s3,
}

df = pd.DataFrame(dictionary)
df
```
![book](/images/blog/20190627/20190627-012.png)

## 2. 繪圖
```python
%matplotlib inline
df.plot()
```
![book](/images/blog/20190627/20190627-013.png)

## 3. 使用 loc() 查找某一個值
```python
r1 = df.loc['2018-01-02']
print(r1)
r2 = df.loc['2018-01-02':'2018-01-05', ['c1', 'c2']]
print(r2)
```
![book](/images/blog/20190627/20190627-014.png)

## 4. 使用 iloc() 查找某一個值
```python
r1 = df.iloc[1]
print(r1)
r2 = df.iloc[1:4, [0, 1]]
print(r2)
```
![book](/images/blog/20190627/20190627-015.png)

## 5. 數值計算
```python
df.cumsum()
df.cumprod()
```
![book](/images/blog/20190627/20190627-016.png)

![book](/images/blog/20190627/20190627-017.png)


