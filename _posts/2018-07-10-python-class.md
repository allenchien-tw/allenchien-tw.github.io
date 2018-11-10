---
published: true
title: (Python-學習-08) --- Python Class
layout: post
author: Allen
category: Python
tags: 
  - Python
comments: true
---

![book](/images/blog/20180710/20180710-000.png)


# 類別簡介
類別定義的形式如下 :
```python
class ClassName:
    <statement-1>
    .
    .
    <statement-N>
```
類別建立後，Python 提供兩種方式使用類別的內容 *直接引用* 或是 *產生物件* 。

# 直接引用
則 MyClass.i 和 MyClass.f 是有效的引用，同時呼叫 `__doc__` 會回傳類別的說名字串。
```python
class MyClass1:
    """A simple example class"""
    i = 12345
    def f(self):
        print("Hello MyClass1")

print(MyClass1.__doc__)
print(MyClass1.i)
MyClass1.f
```

輸出 :
```python
A simple example class
12345
```

# 產生物件
另一種方式是，先依據類別定義產生物件，然後再對物件進行呼叫。同時若此物件有實作 `__init__()`
則產生物件時，會先執行 `__init__()` 中所定義的程式。
```python
class MyClass2:
    """A simple example class"""
    def __init__(self):
        self.i = 67890
    def f(self):
        print("Hello MyClass2")

class MyClass2:
    """A simple example class"""
    def __init__(self):
        self.i = 67890
    def f(self):
        print("Hello MyClass2")
    def v(self, input):
        print("Input = {0}".format(input))

x = MyClass2()
print(x.__doc__)
print(x.i)
x.f()
x.v(22)
```

輸出 :
```python
A simple example class
67890
Input = 22
```

從 MyClass2 中的函式，值得注意是 self 這個關鍵字，由上面範例中，我們呼叫 x.f() 並沒有帶入參數，但是明明 def f(self): 就有定一個參數 self 。
事實上，使用 x.f() 相當於 MyClass2.f(x) ，所以我們之後會看到每個 method 的第一個參數一定是 *self* 。


# Class 中的參數
在 Class 中所定義的參數，會被所有的 Object 使用，但是 Object 定義的參數，只會被 Object 本身使用。
```python
class Dog:
    kind = 'canine'  # Class 參數，被所有 Object 共用


    def __init__(self, name):
        self.name = name  # Object 參數，只會被 Object 本身使用


d = Dog('Fido')
e = Dog('Buddy')
print(d.kind)
print(e.kind)
print(d.name)
print(e.name)
```

輸出 :
```python
canine
canine
Fido
Buddy
```

# 繼承
繼承形式如下:
```python
class DerivedClassName(BaseClassName):   
# 另一種寫法 class DerivedClassName(modname.BaseClassName):

    <statement-1>
    .
    .
    .
    <statement-N>
```

子類別可以使用 BaseClassName.methodname(self, arguments) 方式呼叫父類別的method
另外，Python還提供兩個好用的工具:
– isinstance() 用於檢查 class 類型，若物件類型與Class相同，則回 *True*
– issubclass() 用於檢查繼承，若某一 Class 是繼承，則回 *True*
```python
class Animal:
    def base(self):
        print("Animal")

class Cat(Animal):
    def show(self):
        Animal.base(self)
        print("Cat")

c = Cat()
c.show()
print(isinstance(c, Cat))
print(isinstance(c, Animal))
print(issubclass(Cat, Animal))
print(issubclass(bool, int))
print(issubclass(float, int))
```

輸出 :
```python
Animal
Cat
True
True
True
True
False
```

# 多重繼承
Python 支援與 C++ 相同的多重繼承，這樣讓我們會少寫很多code，記得 Java 要做多重繼承還需要先定義 *interface* 等。
```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```

# 私有參數
Python 語言沒有定義 private member 或是 protected member ，因此大多數 Python 程式，會有個變通的方式，
若我們將一個參數前面加上2個底線，例如 __spam，則該參數會被視為 private member
```python
class Mapping:
    def __init__(self, iterable):
        self.items_list = []
        self.__update(iterable)
```