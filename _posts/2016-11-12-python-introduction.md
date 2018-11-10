---
published: true
title: (Python-學習-01) --- Python 簡介
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20161112/20161112-000.png)

# 前言
雖然接觸 Python 也有2年的時間，但是學習都是斷斷續續，目標都是讓專案可以運作，並沒有真正去了解這個語言，所以這個比較主要是紀錄，重新學習 Python 的練習範例心得。

# 工具
因為目前還是用 Windows 平台，所以找了一個蠻多人推薦的 IDE 工具 PyCharm 直接安裝就可以使用，非常方便。

# 教科書
由於是重新學習，所以希望能先找一本免費而且經典的讀物，所以選擇了 The Python Tutorial 當作學習的框架。

# Python 特色
相較 C/C++ 語言，Python 可以像 Shell Script 容易使用，同時又提供完整的程式結構
- Python 內建了許多好用的資料結構類型，例如List, Dict 等
- Python 的模組功能，可以方便組織大型系統，讓它更有結構化與重複利用的能力
- Python 與 C 語言結合的很棒  ( 這部分在我之前的許多專案，應用的很頻繁，常常是需要Python與C++ DLL做整合 )

# Python 簡介
Python 使用 # 當作註解，例如:
```python
# this is the first comment

spam = 1  # and this is the second comment
```
數字系統中，使用簡單的運算符號，進行計，例如:
```python
2 + 2             # = 4

50 - 5 * 6        # = 20

(50-5*6)/4        # = 5.0

8 / 5             # = 1.6 除法永遠返回 float 型態

7.0 / 2           # = 3.5 integer 與 float 混合計算，會強制轉為 float 型態

17 // 3           # = 5  使用 // 可以返回整數結果，併捨取小數點部分

17 % 3            # = 2  取餘數

5 ** 2            # = 25 等於5^2

2 ** 7            # = 128 等於 2^7

width = 20        # 設值給變數

height            # error 變數都需要預設值

3+5j              # 表示複數
```
字串系統，Python 提供 [單引號] 或是 [雙引號] 來表示字串，可能寫C++習慣了，我比較喜歡用雙引號的方式，
```python
'spam eggs'
'doesn\'t'              # 使用 \' 代表單引號...

"doesn't"               # 若使用雙引號，則裡面可以直接加上單引號

"\"Yes,\" he said."     # 若使用雙引號，則需使用 \" 代表字串中的雙引號.

print('C:\some\name')   # 在這範例 \n 代表，新一行，所以輸出 C:\some

print(r'C:\some\name')  # 在這範例 \n 代表字元 n ，所以輸出 C:\some\name

print("""\              # 使用 """ 並配合 \ 可以組成多行的字串
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
3 * 'un' + 'ium'       # = 'unununium' (3 times 'un', followed by 'ium')
'Py' 'thon'            # 'Python'
word = 'Python'        
word[0]                # = 'p' (character in position 0)
word[-1]               # = 'n' (last character)
word[0:2]              # = 'Py' (characters from position 0 (included) to 2 (excluded))
word[:2]               # = 'Py' (character from the beginning to position 2 (excluded))
```
值得注意的是，在Python中字串是 [唯獨] 的，所以不能重新給值，比需使用創建的方式
```python
word = 'Python'  
word[0] = 'J'          # TypeError:

'J' + word[1:]         # = 'Jython'

len(word)
```
