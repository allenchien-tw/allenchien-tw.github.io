---
published: true
title: (Python-學習-03) --- Python Function
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20170520/20170520-000.png)

# 定義函式
在 Python 中可以使用， def 在 function 定義中的第一行，可以針對這個函式進行說明與註解。
稱為 docstring ，日後可以透過工具擷取說明內容，產生API開發手冊，這是很好的方式。
非常適合不喜歡寫文件的工程師，只要改code的同時順便修改一下說明，手冊就會一倂更新。
之前使用C++開發軟體也是常常配合使用 Doxygen
function 的輸入參數是使用 call by value 機制，所以 function 內部會將輸入參數 copy 一份。
```python
def fib(n):
    """ 印出 n 個費式數列."""
    a = 0
    b = 1
    while a < n:
        print(a)
        a = b
        b += a

if __name__ == '__main__': 
    f = fib  # 將 fib 函式重新命名為 f

    f(100)
    print(fib(100))
```
輸出:
```python
0
1
2
4
8
16
32
64
None
```
另外，function 一定會回傳值，在 function 中沒有 return xxx 時，python 會自動回傳 None
也可以透過 *list* 回傳一組結果
```python
def fib2(n):
    """ 回傳一組資料，並將結果存在一個 list 資料結構中."""
    result = []
    a = 0
    b = 1
    while a < n:
        result.append(a)
        a = b
        b += a
    return result

if __name__ == '__main__':
    data = fib2(100)
    print(data)
```
輸出:
```python
[0, 1, 2, 4, 8, 16, 32, 64]
```

# 函式進階 — 預設參數
Python 的輸入參數可以有三種形式，分別是
- 預設參數
- 關鍵字參數
- 可變參數列表
第一種形式，可以透過預設參數型式，將參數給與預設值。
```python
def fib3(n = 200):
    """ 回傳一組資料，並將結果存在一個 list 資料結構中."""
    result = []
    a = 0
    b = 1
    while a < n:
        result.append(a)
        a = b
        b += a
    return result


if __name__ == '__main__':
    data = fib3()
    print(data)
```
輸出 :
```python
[0, 1, 2, 4, 8, 16, 32, 64, 128]
```

**重點提示**: function 的預設值，只會被設定一次。如下範例:
```python
def fib4(a, L=[]):
    L.append(a)
    return L
if __name__ == '__main__':
    print(fib4(1))
    print(fib4(2))
    print(fib4(3))
```
輸出 :
```python
[1]
[1, 2]
[1, 2, 3]
```

# 函式進階 — 關鍵字參數
function 參數的位置順序若需要不固定，則可以使用 關鍵字參數 型式
```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")

if __name__ == '__main__':
    parrot(1000)                                          # 1 positional argument

        parrot(voltage=1000)                                  # 1 keyword argument

        parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments

        parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments

        parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments

        parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
```

# 函式進階 — 可變參數列表
function 若需要傳入不固定參數，例如 C 語言中的 *printf*，則可以使用 可變參數列表 型式
```python
def concat(*args, sep="/"):
    return sep.join(args)

if __name__ == '__main__':
    print(concat("earth", "mars", "venus"))
    print(concat("earth", "mars", "venus", sep="."))
```
輸出 :
```python
earth/mars/venus
earth.mars.venus
```

# 函式進階 — 輸入參數列表或是字典
function 允許輸入一個list，並且透過 * 將輸入參數拆解，例如 *parrot(*listdata)*
也可以輸入一個dic，並且透過 ** 將輸入參數拆解
```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")

if __name__ == '__main__':
    list_data = ["four million", "bleedin' demised", "VOOM"]
    dic_data = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
    parrot(*list_data)
    parrot(**dic_data)
```
輸出 :
```python
-- This parrot wouldn't VOOM if you put four million volts through it.

-- Lovely plumage, the Norwegian Blue

-- It's bleedin' demised !

-- This parrot wouldn't VOOM if you put four million volts through it.
-- Lovely plumage, the Norwegian Blue
-- It's bleedin' demised !
```
