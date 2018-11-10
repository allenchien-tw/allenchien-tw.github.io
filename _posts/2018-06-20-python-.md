---
published: true
title: (Python-學習-07) --- Python Exception
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20180620/20180620-000.png)


# 異常處理
Python 提供 try – except 異常處理功能，*try- except* 語句可以帶有 else 語句， else 主要是執行若沒有發生異常時的程式碼。
```python
import sys
try:
    f = open('myfile.txt')
    s = f.readline()
    i = int(s.strip())
except OSError as err:
    print("OS error: {0}".format(err))
except ValueError:
    print("Could not convert data to an integer.")
except:
    print("Unexpected error:", sys.exc_info()[0])
else:
        i = i + 10
      print("Open file successs.")
```
在異常語句中，我們可以為 except 語句指定一個變數，用來傳遞異常相關參數。
```python
try:
    raise Exception('spam', 'eggs')
except Exception as inst:
    print(type(inst))
    print(inst.args)
    print(inst)
    x, y = inst.args
    print('x =', x)
    print('y =', y)
```
輸出 :
```python
<class 'Exception'>

('spam', 'eggs')

('spam', 'eggs')

x = spam

y = eggs
```

# 拋出異常
使用 raise 強制拋出異常。
```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    raise
```
輸出 :
```python
An exception flew by!
Traceback (most recent call last):
  File "C:/Users/ALLEN/Documents/Python/Basic/Except.py", line 12, in <module>
    raise NameError('HiThere')
NameError: HiThere
```

#  用戶自定異常
我們也可以先建立一個 exception 的 calss ，然後拋出我們定義的異常
```python
class MyError(Exception):
    def __init__(self, value):
        self.value = value
    def __str__(self):
        return repr(self.value)
```
輸出 :
```python
try:
    raise MyError(2*2)
except MyError as e:
    print('My exception occurred, value:', e.value)
```

# 定義清理行為
try- except 語句還有一個可選語句 finally
無論是否有發生異常，finally 語句一定會被執行。常見的應用是在釋放資源 (例如 file close)
```python
try:
    file = open("test.py")
except:
    print('Read file error')
finally:
    file.close()
```
另一種用法，可以使用 with 語句。
```python
with open("myfile.txt") as f:
    for line in f:
        print(line)
```
