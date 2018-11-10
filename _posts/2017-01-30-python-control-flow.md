---
published: true
title: (Python-學習-02) --- Python 控制流程
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20170130/2017013-000.png)


接下來介紹 Python 對於程式流程的控制邏輯，基本上與一般 C/Java 語言類似，主要需要注意的是
Python 並沒有左右括號，所以都是用 縮排 (Tab) 來判斷一個語句段落，若縮排沒有一致就會發生錯誤。
自己之前用Notepad++來撰寫Python時常發生縮排的錯誤 (用空格，而不是用Tab產生縮排)。
因此寫Python建議需要搭配IDE，幫忙避免這類的錯誤。

雖然一開始覺得很麻煩，可是看到乾淨整齊的程式，就覺得Python設計者真的很有遠見，透過這個規則，讓所有Python程式都能有一致的撰寫風格，看其他人寫的程式也不會感覺怪怪的。(C++語言光是大括號每個人的風格都不一樣)

# if 語句
```python
x = 1
if x < 0:
    x = 0
    print('Negative changed to zero')
elif x == 0:
    print('Zero')
elif x == 1:
    print('Single')
else:
    print('More')
```
輸出 :
```python
"Single"
```

# for 語句
for語句與C語言的for迴圈不同，C語言的for迴圈可以設定起始值(位置)，每次迴圈的間隔值。
但是Python是依照序列的順序逐步執行。比較像 C# 的foreach語句
```python
words = ['cat', 'window', 'defenestrate']
for w in words:
    print(w, len(w))
for i in range(3):
    print(i)
```
輸出 :
```python
cat 3
window 6
defenestrate 12
0
1
2
```

# break / continue / else 語句
break 與 continue 主要配合 for 與 while 語句
而 else 應用在 for 與　while 迴圈中，代表的意義是若迴圈沒有被中斷，則會執行else的段落
```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', n//x)
            break
    else:
        print(n, 'is a prime number')
```
輸出 :
```python
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

# pass 語句
直接跳過沒有執行任何程式，通常使用在創建一個最小的class，不過目前我還是不太清楚使用時機。
等之後看到不錯的範例程式再補充。
```python
# 持續等待 (Ctrl+C) 按鍵

while True:
    pass

# 創建一個最小的class

class MyEmptyClass:
    pass
```
