---
title: 数据类型和运算符
date: 2019-11-06 17:05:43
tags: Python
category: "Python"
---

<!-- ## 数据类型和运算符 -->
## 算术运算符
`+ 加`
`- 减`
`* 乘`
`/ 除`
`% 取模（相除后的余数）`
`** 取幂`
`// 相除后向下取整到最接近的整数`
***
## 变量
``` python
x = 3
y = 4   等价于   x, y, z = 3, 4, 5
z = 5
```
变量命名规则：
1. 变量名称应该要能够描述所存储的值。

2. 只能在变量名称中使用常规字母、数字和下划线。不能包含空格，并且需要以字母或下划线开头。

3. 不能使用保留字或内置标识符。

4. 变量名称的命名方式是全部使用小写字母，并用下划线区分单词。 例：my_variable = 1

![](/img/keywordsinpy.png)
***
## 赋值运算符
`+=   如：x+=2 equal x=x+2`
`-=   如：x-=2 equal x=x-2`
`*=   如：x*=2 equal x=x*2`
***
## 整数和浮点数
数字值可以用到两种 python 数据类型：
int - 表示整数值
float - 表示小数或浮点数值
``` python
x = int(4.7)   # x is now an integer 4
y = float(4)   # y is now a float of 4.0
>>> print(type(x))
int
>>> print(type(y))
float
```
有个有趣的现象，如下：
``` python
>>> print(.1 + .1 + .1 == .3)
False
```
Q: 为什么结果是false呢？？？
A: 详戳[文档](https://docs.python.org/3/tutorial/floatingpoint.html)

Q: 如果在 Python 中除以零，会发生什么？
A: 如下报错
```python
Traceback (most recent call last):
File "/tmp/vmuser_tnryxwdmhw/quiz.py", line 1, in 
print(5/0)
ZeroDivisionError: division by zero
```
***
## Python两种报错类型
1. 异常 代码运行时发生的问题
2. 语法错误  Python 在运行代码之前检查代码时发现的问题
详戳[文档](https://docs.python.org/3/tutorial/errors.html)
***
## 布尔运算符、比较运算符、逻辑运算符
1. 布尔运算符：True 或 False，分别表示为 1 或 0
通常有 6 个比较运算符会获得布尔值：<、>、<=、>=、==、!=
2. 比较运算符：
|符号举例|布尔型|运算符|
|---|---|---|
|5 < 3|False|小于|
|5 > 3|True|大于|
|3 <= 3	|True|小于或等于|
|3 >= 5|False|大于或等于|
|3 == 5|False|等于|
|3 != 5|True|不等于|
3. 逻辑运算符：and、or、not
|逻辑使用情况|布尔型|运算符|
|---|---|---|
|5 < 3 and 5 == 5|False|and - 检查提供的所有语句是否都为 True|
|5 < 3 or 5 == 5|True|or - 检查是否至少有一个语句为 True|
|not 5 < 3|True|not - 翻转布尔值|
***
## 字符串
在 python 中，字符串的变量类型显示为 str。你可以使用双引号 " 或单引号 ' 定义字符串。
``` python
>>> my_string1 = 'Hello string1!'
>>> my_string2 = "Hello string2!"
>>> my_string3 = 'This is YC\'s website.' #在字符串中使用 \ 当做转义字符
```


### 字符串操作与方法
1. 字符串拼接
``` python
>>> first_word = 'Hello'
>>> second_word = 'World'
>>> print(first_word + second_word)
HelloWorld

>>> print(first_word + ' ' + second_word)
Hello World

>>> print(first_word * 5)
HelloHelloHelloHelloHello
```
2. 字符串长度
``` python
>>> print(len(first_word))
5
```
Q：如果len函数的参数是整数835，函数 len 会返回什么？
A：error

3. 字符串索引
``` python
>>> first_word[0]
H
>>> second_word[1]
o
```
4. 等等
![](/img/str1.png)
``` python
>>> my_string.islower() #字符串是否小写
True

>>> my_string.count('a') #字母a的个数
2

>>> my_string.find('a') #字母a的位置，如果有多个字母a，则返回第一个的位置
3
```
可见，count 和 find 方法都接受另一个参数。islower 方法不接受参数。

5. 更多内容戳[字符串方法文档](https://docs.python.org/3/library/stdtypes.html#string-methods)
***
## 类型和类型转换
四种数据类型：整型、浮点型、布尔型、字符串
``` python
>>> print(type(5))
int

>>> print(type(4.8))
float

>>> print(type('what'))
str

>>> print(type(True))
bool

>>> print("0" + "5")
'05'

>>> print(0 + 5)
5

>>> print(0 + "5")
TypeError: unsupported operand type(s) for +: 'int' and 'str'

>>> print("0" + 5)
TypeError: can only concatenate str (not "int") to str
```
***
## 列表
### 创建列表
使用[]创建列表
``` python
>>> list = [1, 2.5, '3', true]

```
### 列表索引
``` python
>>> list[0] #获取第一个元素
1

>>> list[1] #获取第3个元素
2.5

>>> list(len(list) - 1) #获取最后一个元素
true

>>> list(-1) #获取最后一个元素
true

>>> list(-2) #获取倒数第二个元素
'3'
```
### 列表切片
1. 使用切片功能从列表中提取多个值。在使用切片功能时，务必注意，**起始索引包含在内，终止索引排除在外**。
``` python
>>> list[1:2]
2.5
```
2. 要从列表的开头开始，也可以省略起始值
``` python
>>> list[:2]
[1,2.5]
```
3. 返回到列表结尾的所有值，可以忽略最后一个元素。
``` python
>>> list[1:]
[2.5, '3', true]
```
4. **in** OR **not in**
``` python
>>> 'hello' in 'hello world'
True

>>> 'wor' in 'hello world'
True

>>> 'low' in 'hello world'
False

>>> 6 not in [1, 2, 3, 4, 5]
True

>>> 6 in [1, 2, 3, 4, 5]
False
```

### 可变性和顺序
1. 可变性：对象创建完毕后，是否可以更改该对象。
如果对象（例如列表）可以更改，则是可变的。如果无法更改对象以创建全新的对象（例如字符串），则该对象是不可变的。
列表可变：
``` python
>>> list = [1, 2, 3, 4, 5]
>>> list[0] = 'one'
>>> print(list)

['one', 2, 3, 4, 5]
```
字符串不可变：
``` python
>>> my_string = "Hello YC"
>>> my_string[0] = 'M'
>>> print(my_string)

"Hello YC"
```
2. 字符串和列表都是有序的。有些数据类型是无序的。
3. **对于你要使用的每种数据类型，注意两个事项：**
    **可变吗？**
    **有序吗？**

### 列表函数
1. len() 返回列表中的元素数量
2. max() 返回列表中的最大元素。
    最大元素的判断依据是列表中的对象类型。
    数字列表中的最大元素是最大的数字。
    字符串列表中的最大元素是按照字母顺序排序时排在最后一位的元素。
    因为 max() 函数的定义依据是大于比较运算符。如果列表包含不同的无法比较类型的元素，则 max() 的结果是 undefined。
3. min() 返回列表中的最小元素。它是 max() 函数的对立面，返回列表中的最小元素。
4. sorted() 返回一个从最小到最大排序的列表**副本**，**并使原始列表保持不变**。
5. join 是一个字符串方法，将字符串列表作为参数，并返回一个由列表元素组成并由分隔符字符串分隔的字符串。
``` python
>>> my_str = "\n".join(["abc", "def", "ghi", "jkl"])
>>> print(my_str)
"abc"
"def"
"ghi"
"jkl"

>>> my_class = "-".join(["Class", "D"])
>>> print(my_class)
"Class-D"
```
6. append方法将元素添加到列表末尾
``` python
>>> my_num = [1, 2, 3, 4]
>>> my_num.append(5)
>>> print(my_num)

[1,2,3,4,5]
```
***
## 元祖
不可变有序元素数据类型。通常用来存储相关的信息。
``` python
>>> my_figure = (165, 50)
>>> print("Height:", my_figure[0])
>>> print("Weight:", my_figure[1])
```
与列表相同的是，它们都存储一个有序的对象集合，并且可以通过索引访问这些对象。
与列表不同的是，元组不可变，你无法向元组中添加项目或从中删除项目，或者直接对元组排序。

元组还可以用来以紧凑的方式为多个变量赋值。
``` python
>>> dimensions = 52, 40, 100 #可以忽略小括号，不影响解释代码
>>> length, width, height = dimensions # 元组解包: 根据元组 dimensions 的内容为三个变量赋了值

# 如果我们不需要直接使用 dimensions，可以将这两行代码简写为一行，一次性为三个变量赋值！
>>> print("The dimensions are {} x {} x {}".format(length, width, height)) 

"The dimensions are 52 x 40 x 100"
```
>注意：列表是可变有序的，元祖是不可变有序的
***
## 集合
集合是一个包含唯一元素的可变无序集合数据类型。
集合的一个用途是快速删除列表中的重复项。
``` pyhton
>>> my_numbers = [1, 2, 3, 4, 1, 2, 3]
>>> unique_nums = set(my_numbers)
>>> print(unique_nums)

{1, 2, 3, 4}
```
集合和列表一样支持 in 运算符。
和列表相似，你可以使用 add 方法将元素添加到集合中，并使用 pop 方法删除元素。
但是，当你从集合中拿出元素时，会随机删除一个元素。注意和列表不同，集合是无序的，因此没有“最后一个元素”。
你可以对集合执行的其他操作包括可以对数学集合执行的操作。可以对集合轻松地执行 union、intersection 和 difference 等方法，并且与其他容器相比，速度快了很多。

``` python
>>> fruit = {"apple", "banana", "orange", "grapefruit"}  # define a set

>>> print("watermelon" in fruit)  # check for element

>>> fruit.add("watermelon")  # add an element
>>> print(fruit)

>>> print(fruit.pop())  # remove a random element
>>> print(fruit)

False
{'grapefruit', 'orange', 'watermelon', 'banana', 'apple'}
grapefruit
{'orange', 'watermelon', 'banana', 'apple'}
```
检测学习成果来了，下面这个有趣的问题，你认为5还会在b集合中吗?
``` python
>>> a = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
>>> b = set(a)
>>> b.add(5)
>>> b.pop()
```
***
## 字典和恒等运算符
### 字典
字典是可变数据类型，其中存储的是唯一键到值的映射。下面是存储元素和相应原子序数的字典。
``` python
>>> fruits = {"apple": 3, "orange": 2, "lemon": 6}
```
字典的键可以是任何**不可变类型**，例如整数或元组，而不仅仅是字符串。
每个键都不一定要是相同的类型！使用方括号并在括号里放入键，查询字典中的值或向字典中插入新值。
``` python
>>> print(fruits["orange"])  # print the value mapped to "orange"
>>> fruits["peach"] = 5  # insert "peach" with a value of 5 into the dictionary
```
检查某个值是否在列表或集合中一样，使用关键字 in 检查值是否在字典中。字典有一个也很有用的相关方法，叫做 get。get 会在字典中查询值，但是和方括号不同，如果没有找到键，get 会返回 None（或者你所选的默认值）。
``` python
>>> print("lemon" in fruits)
>>> print(fruits.get("pineapple"))
>>> print(fruits["pineapple"])

True
None
KeyError错误
```
lemon 位于该字典中，因此输出 pineapple 不在字典中，因此 get 返回 None，然后系统输出 None。
>如果你预计查询有时候会失败，get 可能比普通的方括号查询更合适，因为错误可能会使程序崩溃。

Q:以下哪些项可以用作字典的键？（多选） 
  A. str
  B. list
  C. int
  D. float

### 恒等运算符
|关键字|运算符|
|---|---|
|is|检查两边是否恒等|
|is not|检查两边是否不恒等|

>你可以使用运算符 is 检查某个键是否返回了 None。或者使用 is not 检查是否没有返回 None。
``` python
>>> result = fruits.get("pineapple")
>>> print(result is None)
>>> print(result is not None)

True
False
```

Q:检查是否相等或恒等
``` python
>>> a = [1, 2, 3]
>>> b = a
>>> c = [1, 2, 3]

>>> print(a == b)
>>> print(a is b)
>>> print(a == c)
>>> print(a is c)

True
True
True
False
```
***
## 复合数据结构
在容器中包含容器，就可以创建复合数据结构。例如，下面的字典将键映射到也是字典的值！
``` python
>>> data = {"hydrogen": {"number": 1,
                         "weight": 1.00794,
                         "symbol": "H"},
              "helium": {"number": 2,
                         "weight": 4.002602,
                         "symbol": "He"}}
```
访问这个嵌套字典中的元素:
``` python
>>> helium = data["helium"]  # get the helium dictionary
>>> hydrogen_weight = elements["hydrogen"]["weight"]  # get hydrogen's weight
```
>总结：
>列表:有序、可变、使用.append添加项目
>集合：无序、可变、使用.add添加项目
>字典：无序、可嵌套
***
## 总结
1. 数据结构
|Data Structure|Ordered|Mutable|Constructor|Example|
|---|---|---|---|---|
|int|NA|NA|int()|5|
|float|NA|NA|float()|6.5|
|string|Yes|No|' ' or " " or str()|"this is a string"|
|bool|NA|NA|NA|True or False|
|list|Yes|Yes|[ ] or list()|[5, 'yes', 5.7]|
|tuple|Yes|No|( ) or tuple()|(5, 'yes', 5.7)|
|set|No|Yes|{ } or set()|{5, 'yes', 5.7}|
|dictionary|No|Keys: No|{ } or dict()|{'Jun':75, 'Jul':89}|
