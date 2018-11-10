---
published: true
title: (Python-學習-04) --- Python Data Structure
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20180228/20180228-000.png)

# List 基礎
Python 的 list 資料結構非常實用，可以支援索引(index)與切片(slice)
在Python中可以使用一行指令就可以完成在c++的sub-string功能，
看到後感覺得學這個語言，可以讓你的人生省一半的時間。哈!
```python
def list():
    squares1 = [1, 4, 9, 16, 25]
    print(squares1[0])  #索引

    print(squares1[-1])  #反向索引

    squares2 = squares1[-3:]  #切片並產生新的串列

    print(squares2)
    squares1 = squares1 + [36, 49, 64, 81, 100]  #串列連接, 串列是可變的

    print(squares1)
    squares1.append(22)  #使用append進行串列連接

    print(squares1)
    squares1[1:3] = [8, 8, 8]  #直接取代串列中某些元素

    print(squares1)
    squares1[1:3] = []  #移除串列中某些元素

    print(squares1)
    print(len(squares1))  #顯示串列長度

if __name__ == '__main__':
    list()
```
輸出 :
```python
1
25
[9, 16, 25]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 22]
[1, 8, 8, 8, 16, 25, 36, 49, 64, 81, 100, 22]
[1, 8, 16, 25, 36, 49, 64, 81, 100, 22]
10
```

# List 內建函數
List 也提供許多實用的 function , 可以參考下面範例
```python
def list_func():
    squares = [1, 4, 9, 16, 25]
    squares.append(10)
    print(squares)
    squares[len(squares):] = [10]  #結果與上述寫法相同

    print(squares)
    squares.extend([10, 10, 10])
    print(squares)
    squares[len(squares):] = [10, 10, 10]  #結果與上述寫法相同

    print(squares)
    squares.insert(0, 22)  #插入22到第一個元素前

    print(squares)
    squares.remove(10)  #移除第一個找到內容為 10 的元素

    print(squares)
    squares.pop(0)  #移除第一個元素

    print(squares)
    squares.pop()
    print(squares)  #移除最後一個元素

    print(squares.index(10))  #回傳找到第一個內容為 10 的index

    print(squares.count(10))  #回傳 10 在串列中的次數

    squares.sort()  #將串列排序

    print(squares)
    squares.reverse()  #將串列反向排序

    print(squares)
    squares1 = squares.copy()
    print(squares1)
    squares2 = squares[:]  #結果與上述寫法相同

    print(squares2)
    squares1.clear()
    print(squares1)
    del squares2[:]  #結果與上述寫法相同

    print(squares2)


if __name__ == '__main__':
    list_func()
```
輸出 :
```python
[1, 4, 9, 16, 25, 10]
[1, 4, 9, 16, 25, 10, 10]
[1, 4, 9, 16, 25, 10, 10, 10, 10, 10]
[1, 4, 9, 16, 25, 10, 10, 10, 10, 10, 10, 10, 10]
[22, 1, 4, 9, 16, 25, 10, 10, 10, 10, 10, 10, 10, 10]
[22, 1, 4, 9, 16, 25, 10, 10, 10, 10, 10, 10, 10]
[1, 4, 9, 16, 25, 10, 10, 10, 10, 10, 10, 10]
[1, 4, 9, 16, 25, 10, 10, 10, 10, 10, 10]
5
6
[1, 4, 9, 10, 10, 10, 10, 10, 10, 16, 25]
[25, 16, 10, 10, 10, 10, 10, 10, 9, 4, 1]
[25, 16, 10, 10, 10, 10, 10, 10, 9, 4, 1]
[25, 16, 10, 10, 10, 10, 10, 10, 9, 4, 1]
[]
[]
```

# 使用 List 模擬 Stack 資料結構
我們可以使用 List 模擬 Stack 的資料結構
```python
def list_stack():
    stack = [3, 4, 5]
    stack.append(6)
    stack.append(7)
    print(stack)
    print(stack.pop())
    print(stack.pop())
    print(stack.pop())

if __name__ == '__main__':
    list_stack()
```
輸出 :
```python
[3, 4, 5, 6, 7]
7
6
5
```

# 使用 List 模擬 Queue 資料結構
使用 List 並且搭配 `collections.deque` 模擬 Queue 的資料結構
```python
from collections import deque
def list_deque():
    queue = deque(["Eric", "John", "Michael"])
    queue.append("Terry")
    queue.append("Graham")
    print(queue)
    print(queue.popleft())
    print(queue.popleft())
    print(queue)

if __name__ == '__main__':
    list_deque()
```
輸出 : 
```python
deque(['Eric', 'John', 'Michael', 'Terry', 'Graham'])
Eric
John
deque(['Michael', 'Terry', 'Graham'])
```

# 使用 List 推導式
List 提供兩種用方式，可以使用程式產生串列內容，範例如下 :
```python
def list_gen1():
    squares = []
    for x in range(10):
        squares.append(x**2)
    print(squares)
    squares = [x**2 for x in range(10)]
    print(squares)

def list_gen2():
    squares = []
    for x in [1,2,3]:
       for y in [3,1,4]:
           if x != y:
               squares.append((x, y))
    print(squares)
    squares = [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
    print(squares)

if __name__ == '__main__':
    list_gen1()
    list_gen2()
```
輸出 :
```python
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

# 使用 del 語句
del 語句可以刪除串列的某一個元素，或是透過切片的方式移除一群元素。
```python
def list_del():
    a = [-1, 1, 66.25, 333, 333, 1234.5]
    del a[0]
    print(a)
    del a[2:4]
    print(a)
    del a[:]
    print(a)
    del a  #若呼叫 print(a) 或是參考 a 會產生錯誤

if __name__ == '__main__':
    list_del()
```
輸出 :
```python
[1, 66.25, 333, 333, 1234.5]
[1, 66.25, 1234.5]
[]
```

# Set 資料結構
Set (集合) 是一個 *無序* 並且 *無重複元素* 的資料結構，並且資源 union, intersection, difference等集合的數學運算。集合使用 { } 來創建
```python
def set_test():
    basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
    print(basket)
    print('orange' in basket)
    print('crabgrass' in basket)
    a = set('abracadabra')
    b = set('alacazam')
    print(a)
    c = a - b  # 在a中在不再b中

    print(c)
    c = a | b  # 在a或b中

    print(c)
    c = a & b  #同時在a與b中

    print(c)
    c = a ^ b  #在a或b中，但是不同時存在a,b中

    print(c)

if __name__ == '__main__':
    set_test()
```
輸出 :
```python
{'apple', 'orange', 'banana', 'pear'}
True
False
{'b', 'r', 'a', 'd', 'c'}
{'b', 'r', 'd'}
{'z', 'r', 'a', 'l', 'd', 'b', 'c', 'm'}
{'a', 'c'}
{'z', 'l', 'r', 'd', 'b', 'm'}
```

# Dict 資料結構
Python 的 *dict* 其實就是C++中的 *map* , 所以一樣 key-value pair
```python
def dict_test():
    tel = {'jack': 4098, 'sape': 4139}
    tel['guido'] = 4127
    print(tel)
    print(tel['jack'])
    del tel['sape']
    tel['irv'] = 4127
    print(tel)
    print(tel.keys())
    tel_sort = sorted(tel.keys())
    print(tel_sort)
    'guido' in tel
    'jack' not in tel

if __name__ == '__main__':
    dict_test()
```
輸出 :
```python
{'jack': 4098, 'guido': 4127, 'sape': 4139}
4098
{'jack': 4098, 'guido': 4127, 'irv': 4127}
dict_keys(['jack', 'guido', 'irv'])
['guido', 'irv', 'jack']
```