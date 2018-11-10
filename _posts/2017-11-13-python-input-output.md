---
published: true
title: (Python-學習-06) --- Python Input/Output
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20171113/20171113-000.png)


在Python中，有時會需要列印出一些內容方便顯示與除錯。因此Python提供兩種格式化輸出方式
1. 先將字串格式化，在使用print()印出
2. 直接呼叫 format()

# 字串格式化
Python可以使用 repr() 或是 str() 將其他資料型別轉為字串型別
```python
s = 'Hello, world.'
str(s)
repr(s)
str(1/7)
x = 10 * 3.25
y = 200 * 200
s = 'The value of x is ' + repr(x) + ', and y is ' + repr(y) + '...'
print(s)
hello = 'hello, world\n'
hellos = repr(hello)
print(hellos)
any = repr((x, y, ('spam', 'eggs')))
print(any)
```
輸出 :
```python
The value of x is 32.5, and y is 40000...
'hello, world\n'
(32.5, 40000, ('spam', 'eggs'))
```

# 使用str.format
另一種方式，使用上有點類似 C# 方式
```python
print('{0} and {1}'.format('spam', 'eggs'))
print('{1} and {0}'.format('spam', 'eggs'))
print('This {food} is {adjective}.'.format(food='spam', adjective='absolutely horrible'))
print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred', other='Georg'))

import math
print('The value of PI is approximately {0:.3f}.'.format(math.pi))

table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
for name, phone in table.items():
    print('{0:10} ==> {1:10d}'.format(name, phone))
```
輸出 :
```python
spam and eggs
eggs and spam
This spam is absolutely horrible.
The story of Bill, Manfred, and Georg.
The value of PI is approximately 3.142.
Jack       ==>       4098
Dcab       ==>       7678
Sjoerd     ==>       4127
```

# 檔案的讀入與寫出
檔案開起使用 open() 完成，範例如下:
```python
f = open('workfile.txt', 'r+')
print(f.readline())  #一次讀入一行

print(f.readline())
print(f.readline())
print(f.read())  #讀入全部檔案


print(f.write("\nwrite1"))
print(f.write("0123456789abcdef"))
f.seek(5)            #移到第6個元素

print(f.read(1))     #讀一個元素

print(f.read(1))
f.close()
```
輸出 :
```python
write10123456789abcdefine1
line2
line3
end


write1
write1
write1
write10123456789abcdef
write10123456789abcdef
write10123456789abcdef
7
16
t
e
```

