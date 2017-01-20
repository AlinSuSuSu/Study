---
title:python笔记
tags: 函数,模板
grammar_cjkRuby: true
---

1. getattr函数:built-in function 
   getattr(object, name[, default])
   Return the value of the named attribute of object. name must be a string. If the string is the name of one of the object’s attributes, the result is the value of that attribute. For example, getattr(x, 'foobar') is equivalent to x.foobar. If the named attribute does not exist, default is returned if provided, otherwise AttributeError is raised.
	举例：
	```python
	def callback(self, prefix, name, *args):  
        method = getattr(self, prefix+name, None)  
        if callable(method): return method(*args) 
	```
	link:https://docs.python.org/3/library/functions.html?highlight=getattr#getattr
	![bulit-in functions][1]
2. 字符串对象的 rjust() 方法： 它可以将字符串靠右, 并在左边填充空格。
    类似的如：ljust(),center(),zfill()。zfill()会在数字的左边填充0
3. str.format() 的基本使用如下:
    ```python
	>>> print('{}网址： "{}!"'.format('菜鸟教程', 'www.runoob.com'))
	菜鸟教程网址： "www.runoob.com!"
	```
	括号及其里面的字符 (称作格式化字段) 将会被 format() 中的参数替换。
	在括号中的数字用于指向传入对象在 format() 中的位置，如下所示：
	```python
	>>> print('{0} 和 {1}'.format('Google', 'Runoob'))
	Google 和 Runoob
	>>> print('{1} 和 {0}'.format('Google', 'Runoob'))
	Runoob 和 Google
    ```
4. open(file,mode)打开文件 
5. 类的常用方法：
   ```python
	__init__ : 构造函数，在生成对象时调用
	__del__ : 析构函数，释放对象时使用
	__repr__ : 打印，转换
	__setitem__ : 按照索引赋值
	__getitem__: 按照索引获取值
	__len__: 获得长度
	__cmp__: 比较运算
	__call__: 函数调用
	__add__: 加运算
	__sub__: 减运算
	__mul__: 乘运算
	__div__: 除运算
	__mod__: 求余运算
	__pow__: 称方	
	```
6. Python isdigit() 方法检测字符串是否只由数字组成。
7. ![re,flagonson][2]
	


  [1]: ./images/1484798948070.jpg "1484798948070.jpg"
  [2]: ./images/1484820209534.jpg "1484820209534.jpg"