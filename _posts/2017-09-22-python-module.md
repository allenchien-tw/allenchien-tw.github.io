---
published: true
title: (Python-學習-05) --- Python Module
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20170922/20170922-000.png)

# 基本說明
當定義了許多函式之後，我們會開始想讓它們被重複利用，並且能夠集中起來方便管理，
因此Python提供了模組(Modules)機制，方便我們將函式集中管理。

首先建立一個 fib.py 的檔案如下:
```python
def fib(n):  
    a, b = 0, 1
    while b < n:
        print(b, end=' ')
        a, b = b, a+b
    print()

def fib2(n): 
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a+b
    return result
```
然後再主程式中使用下面 namespace 方式宣告模組並使用
```python
import fibo
fibo.fib(1000)
fibo.fib2(100)
```

# 模組進階
模組有兩個主要特色:
## 初始化一次
Python 的模組在 import 時只會被載入一次，之後再使用import則不會有任何作用，但是也可以使用 imp.reload 的方式，重新載入。
```python
import imp
imp.reload(modulename)
```
## 命名空間 (Namespace)
Python為模組提供命名空間的機制，讓函式名稱不會產生衝突，下面有寫法，習慣上比較推薦第一種，因為第一種除了保證不會與其他名稱衝突外，也可以讓程式讀起來更容易理解，使用的函式是出自哪一個模組中。
```python
#寫法1  (推薦)
import fibo
fibo.fib(1000)
fibo.fib2(100)
#寫法2
from fibo import fib, fib2
fib(500)
#寫法3  (最不建議)
from fibo import *
fib(500)
```

# 模組的收尋路徑
Python尋找某一模組 xxx.py 時，會依照 sys.path 所定義的路徑，依序搜尋
sys.path 定義的目錄列表如下:
1. 當前目錄下尋找 xxx.py
2. 由環境變數 PYTHONPATH 指定的目錄下尋找
3. 由Python的安裝路徑

# 套件
當模組又成長出很多 .py 檔案，變成一個專案時，這時就需要使用套件 (package)，將這些模組組織起來。
建立套件的方式，就是建立一個目錄，並且在目錄中放一個 init.py 檔案，此時Python就會自動將這個目錄視為套件。而目錄名稱就是套件名稱。
```python
sound/                          Top-level package
      __init__.py               Initialize the sound package
      formats/                  Subpackage for file format conversions
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  Subpackage for sound effects
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  Subpackage for filters
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
              ...
```
使用方式如下
```python
import sound.effects.echo
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)  #使用完整名稱

from sound.effects import echo
echo.echofilter(input, output, delay=0.7, atten=4)  #減少部分套件名稱

from sound.effects.echo import echofilter
echofilter(input, output, delay=0.7, atten=4)
```
若在套件中引用子套件的模組時，可以使用相對路徑，例如上述結構中 surround.py 可以使用下面方式
```python
from . import echo
from .. import formats
from ..filters import equalizer
```
