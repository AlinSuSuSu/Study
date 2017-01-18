---
title: Python基础教程（第2版）
tags: Python,模块
grammar_cjkRuby: true
---

####  第1章 快速改造：基础知识
1. **模块：将模块导入Python中以使用模块中的函数**，例如math:

   ``` python
   import math
   print(math.floor(32.9))
	```
    若确定自己使用哪些函数，又不希望使用函数时带上模块名，则可用这种形式：

   ```python
   from math import sqrt
   print(sqrt(9)
   ```
   备注：nan是一个特殊值的简写，意思是"not a number"
	   
2.   **对于复数，使用cmath模块**（complex math）：

     ``` python
     import cmath
     print(cmath.sqrt(-1))
	 #答案是1j
	 ```
	 ```python
	 (1+3j)*(9+4j)
	 #答案：(-3+31j)
	 ```

3. **表示字符串**

   - 单引号，双引号，三引号（可以保持格式）
	    ```python
		"Let's go"
		"Let's say " ' Hello, world!' "
		```
   - repr函数。它会创建一个字符串，以合法的Python表达式的形式来表示值。
		```python
		print repr("Hello,world!")
		#'Hello,world!'
		```
   - str函数
	 ```python
	 print str("Hello,world!")
	 #Hello,world!
	 ```
4.  **input和raw_input的区别**
	name = input("What's your name?")
	会默认输入python合法的字符串，例如"Mary"
	 而raw_input则不需要输入引号""，只需要输入Mary
 
5. **长字符串、原始字符串和Unicode**
	- 长字符串：可以使用'''实现跨行，对于普通字符串，可以通过\来实现跨行，同时，这个方法适用于表达式和语句：
		```python
		 print "Hello,\
		 world!"
		 #输出：Hello,world!
		 1+2+\
		 3+4
		 #输出：10
		 ```
	 - 原始字符串：对反斜线不会特殊对待。反斜线用于转义：
		 可以使用r来进行转义，但字符串最后一个字符不能是\，否则Python不知是否该结束语句
		 ```python
		 print r"C:\Program Files\Intel\bozz"
		 #输出：C:\Program Files\Intel\bozz
		 ```
	 - Unicode字符串：在字符串前加上u，例如：u"Hello,world!"
 
 
 **小结**
 新函数：
 ```python
import cmath
abs(-3)#3
cmath.sqrt(-1)#1j
float("4")#4.0
help()
input()
int(4.3)
math.ceil(4.3)#5
math.floor(4.3)#4
math.sqrt(5)#2.23606797749979
pow(3,2,4)#1  pow(x,y[,z])返回x的y次方，对z取模）
repr(3)#'3'
round(4.6432,2)#4.64
str(4)#'4'
 ```
#### 列表和元组
**一、列表：**

1.  索引
	```python
	greeting="Hello"
	greeting[0]#'H'
	greeting[-1]#'o'
	'Hello'[-2]#'l'
	#-----
	fourth=raw_input('Year:')[3]
	Year:2005#fourth'5'
	#----
	```

2. 分片

	```python
	greeting="Hello,Mary!"
	greeting[6:-1]
	greeting[:]
	greeting[-5:]
	greeting[:-4]
	```
3. 步长
	```python
	greeting="Hello,Mary!"
	greeting[::2]#'HloMr!'
	greeting[::-2]#'!rMolH'
	```
4. 序列相加+
5. 乘法：[42]\*5:[42,42,42,42,42]
6. 成员资格in：'w' in 'world!'  #True
7. 长度length，最大max，最小min
8. list函数： list('3242')   #['3', '2', '4', '2']
9. 基本的列表操作x=['3', '2', '4', '2']
	- 赋值：x[3]='1'  #x=['3', '2', '4', '1']
	- 删除：del x[2]   #x=['3', '2',  '2']
	- 分片赋值：x[2:]=list('45')  #x=['3', '2','4','5']；x[0:1]=[]   #x=['2', '4', '2']
10. 列表方法
	- append追加：x.append('5')  #x=['2', '4', '2','5']
	- count计算某个元素在列表中出现的次数：x.count('2')   # 2
	- extend在列表末尾追加多个值：x.extend(x)  #x=['2', '4', '2','5','2', '4', '2','5']
	- index：x.index(3)  # '5'
	- insert：x.insert(5,'five')  #x=['2', '4', '2','5','2','five', '4', '2','5']
	- pop：x.pop()   # '5'； x.pop(1)  #'4'   x=['2', '2','5','2','five', '4', '2']
	- remove：x.remove('2')  #x=[ '2','5','2','five', '4', '2']
	- reverse：x.reverse() #x=['2', '4', 'five', '2', '5', '2']
	- sort：x.sort() #x=['2', '2', '2', '4', '5', 'five']
	- *高级排序cmp：x < y返回负数，大于返回正数，x=y返回0*

**二、元组：**
- 元组不能修改。
- 表示一个值的元组（2，）必须加逗号
- 元组的创建：如果用逗号分隔了一些值，那么就自动创建了元组。
- 元组的意义：
  - 元组可以在映射中当做键使用
  - 元组作为很多内建函数和方法的返回值存在。
1. tuple函数：一个卢谢作为参数并把它转换为元组 tuple([1,2,3])   #结果：（1,2,3）
2. 基本操作：
```python
x=1,2,3
x #（1,2,3）
x[2] #3
x[0:2] #(1,2)
```
#### 第三章 使用字符串

1. 字符串格式化：使用字符串格式化操作符%来实现
   ```python
	format="Hello,%s,%s enough for you?"
	values=("world","it's")
	print(format % values)
    #Hello,world,it's enough for you? 
	```
	模板方法：
	```python
	from string import Template
	 s=Template("$a,it's $a")
	 s.substitute(a='slum')
	 "slum,it's slum"
	```
2. 基本的转换符说明：
    - %字符：标记转换符的开始
    - 转换标志（可选）：-表示左对齐，+表示在转换值之前要加上正负号，空白字符表示正数之前保留空格，0表示转换值若位数不够用0来补充。
    - 最小字段宽度（可选）
    - 点（.）后跟精度（可选）
    - 转换类型：如d,o,f,x,e等
3. 字符串方法：
   - find 返回子串所在位置的最左端索引
   - join 是split方法的逆方法，用来连接序列中的元素
      ```python
	  dirs='','usr','bin','env'
	  '/'.join(dirs)
	  #dirs='/usr/bin/env'
      ```
   - lower 返回字符串的小写字母版 str.lower()
   - replace 返回某字符串的所有匹配项均被替换之后得到的字符串str.replace('is','name')
   - split是join的逆方法，用于分解字符串成序列
     ```python
	 '1+2+3+4'.split('+')
	 #[1,2,3,4]
	 ```
   - strip去除字符串两侧的空格（不包含内部）
   - translate替换字符串中的某些部分，与replace不同的是，translate只处理单个字符
 
#### 第四章 字典：当索引不好用时
1. 创建字典：phonebook={'Alice':'8024312','Mary':'8092412','John':'8902142'}
2. dict函数：通过其他映射或者（键，值）对的序列建立字典
     ```python
      items=[('name','Henry'),('age',42)]
	  d=dict(items)
	  #d={'age':42,'name':'Henry'}
     ```
3. 字典的格式化字符串
    ```python
	"John's phone number is %(John)s" % phonebook
	#John's phone number is 8902142"
	```
4. 字典方法
   - clear清除字典中所有的项
   - copy返回一个具有相同键-值对的新字典
   - fromkeys使用给定的键建立新的字典
    dict.fromkeys(['name','age'],'unknown')
	{}.fromkeys(['name','age']
   - get更加宽松的访问字典项的方法。如果访问一个不存在的值，没有任何异常，得到none值
   - items和iteritems，items是将字典所有的项以列表方式返回，列表汇总的每一项都表示为（键，值）对的形式。而iteritems是返回一个迭代器对象而不是列表
   - keys和iterkeys将键以列表和迭代器对象的形式返回
   - pop用来获得对应于给定键的值，然后将这个键-值对从字典中移除
   - popitem弹出随机项
   - setdefault当键不存在的时候，返回默认值并相应地更新字典；如果键存在，就返回与其对应的值，但不改变字典
   - update利用一个字典项更新另外一个字典
   - values和itervalues返回字典中的值序列和迭代器对象
 
 
 #### 第五章 条件、循环和其他语句

1. print 和import 的更多信息
   - 使用逗号隔开输出。
	```python
	print 'Age',42,'Name','Henry'
	```
   - 把某件事作为另一事导入：from somemodule import somefunction.或者是import somemodule as myfunction
2. 赋值魔法
   - 序列解包：
   ```python
   x,y,z=1,2,3
   print x,y,z#1,2,3
   x,y=y,x
   print x,y,z#2,1,3
   values=1,2,3#values=(1,2,3)
   x2,y2,z2=values#x2=1
    ```
	当函数或者方法返回元组时，这个特性尤其有用。例如用popitem方法，将键-值对作为元组返回
	sound={'name':'Robin','girlfriend':'Marion'}
	key,value=sound.popitem()
	#key='girlfriend'#value='Marion'
3. python中的比较运算符
    表达式  |   描述
	---------  |  --------
	x == y   |
	x < y     |
	x > y     |
	x >= y   |
	x <= y   |
	x != y    |
	x is y    |  x和y是同一个对象
	x is not y  |
	x in y    | x是y容器（例如序列）成员
	x not in y |
4. 断言assert


#### 第八章  异常

#### 构造方法、属性和迭代器

1. 构造方法,将init方法修改为_init_
2. 迭代器：_iter_
3. 生成器：任何包含yield语句的函数成为生成器。


#### 第十章 自带电池

1. 模块用于定义：
   ```python
   import sys
   sys.path.append("c:\python")#模块的路径
   
   import testmodule
   testmodule.hello()#调用自己的模块中的hello函数
   ```
2. 查询解释器去哪里查找python使用的模块
	  ```python
	 >>> import pprint,sys
	 >>> pprint.pprint(sys.path)
	  ['',
	 'D:\\installations\\Python3_5_2\\Lib\\idlelib',
	 'D:\\installations\\Python3_5_2\\python35.zip',
	 'D:\\installations\\Python3_5_2\\DLLs',
	 'D:\\installations\\Python3_5_2\\lib',
	 'D:\\installations\\Python3_5_2',
	 'D:\\installations\\Python3_5_2\\lib\\site-packages',
	 'c:\\python',
	 'c:\\python',
	 'c:\\python']
	  ```
	  使用sys.path添加不是通用的方法，标注男的实现方法是在PYTHONPATH环境变量中包含模块所在的目录。（在用户环境变量中添加的python解释器路径，多路径用;分隔
	  
3. 使用包，包中可包含多个模块。
    ```python
	import packagename1
	import packagename1.module1
	import packagename1.module2
	from packagename1 import module3
	```
4. 查询模块中有什么
    - 使用dir
       ```python
	   >>>[n for n in dir(pprint) if not n.startswith('_')]
	   ['PrettyPrinter', 'isreadable', 'isrecursive', 'pformat', 'pprint', 're', 'saferepr']
	   ```
	- 使用\__all\__变量。
	  ```python
	  >>> pprint.__all__
	  ['pprint', 'pformat', 'isreadable', 'isrecursive', 'saferepr', 'PrettyPrinter']
	  ```
	- 用help获取帮助
	   ```python
	   >>> help(pprint.pformat)
	   Help on function pformat in module pprint:

	   pformat(object, indent=1, width=80, depth=None, *, compact=False)
	   Format a Python object into a pretty-printed representation.
	   ```
    -  文档:查询详细的文档信息。
		```python
		>>> print(range.__doc__)
		range(stop) -> range object
		range(start, stop[, step]) -> range object

		Return an object that produces a sequence of integers from start (inclusive)
		to stop (exclusive) by step.  range(i, j) produces i, i+1, i+2, ..., j-1.
		start defaults to 0, and stop is omitted!  range(4) produces 0, 1, 2, 3.
		These are exactly the valid indices for a list of 4 elements.
		When step is given, it specifies the increment (or decrement).
		```
	 - 使用源代码，查询模块的源代码在哪里
	   ```python
		>>> print(pprint.__file__)
		D:\installations\Python3_5_2\lib\pprint.py
	   ```
	   
	   
