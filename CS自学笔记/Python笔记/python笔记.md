
# python3基础语法

## 数字(Number)类型

python中数字有四种类型：整数、布尔型、浮点数和复数。

- **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
- **bool** (布尔), 如 True。
- **float** (浮点数), 如 1.23、3E-2
- **complex** (复数), 如 1 + 2j、 1.1 + 2.2j

## 字符串(String)

- Python 中单引号 ' 和双引号 " 使用完全相同。
- 使用三引号(''' 或 """)可以指定一个多行字符串。
- 反斜杠可以用来转义，使用 r 可以让反斜杠不发生转义。 如 **r"this is a line with \n"** 则 \n 会显示，并不是换行。
- 按字面意义**级联字符串**，如 **"this " "is " "string"** 会被自动转换为 **this is string**。
- 字符串可以用 + 运算符连接在一起，用 * 运算符重复。
- Python 中的字符串**有两种索引方式**，从左往右以 0 开始，从右往左以 -1 开始。
- Python 中的字符串不能改变。
- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。
- 字符串切片 str[start:end]，其中 start（包含）是切片开始的索引，**end（不包含）** 是切片结束的索引。
- 字符串的切片可以加上步长参数 step

## 同一行显示多条语句

Python 可以在同一行中使用多条语句，语句之间使用分号 ; 分割

## print 输出

**print** 默认输出是换行的，如果要实现不换行需要在变量末尾加上 end=""：

## import 与 from...import

在 python 用 import 或者 from...import 来导入相应的模块。

## Python3 基本数据类型

Python 中的变量不需要声明。每个变量在使用前都必须赋值

Python允许你同时为多个变量赋值

## 标准数据类型
Python3 中常见的数据类型有：

- Numberber（数字）
- String（字符串）
- bool（布尔类型）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）

python3 的六个标准数据类型中：

不可变数据（3 个）：Number（数字）、String（字符串）、Tuple（元组）；
可变数据（3 个）：List（列表）、Dictionary（字典）、Set（集合）。

Number（数字）
Python3 支持 int、float、bool、complex（复数typeypeype() 函数可以用来查询变量所指的对象类型。

**注意：**

-  Python可以同时为多个变量赋值，如a, b = 1, 2。
- 一个变量可以通过赋值指向不同类型的对象。
- 数值的除法包含两个运算符：/ 返回一个浮点数，// 返回一个整数。
- 在混合计算时，Python会把整型转换成为浮点数。
- 复数由实数部分和虚数部分构成，可以用 a + bj，或者 complex(a,b) 表示， 复数的实部 **a** 和虚部 **b** 都是浮点型。
## String（字符串）

Python中的字符串用单引号 ' 或双引号 " 括起来，同时使用反斜杠 \ 转义特殊字符。

字符串的截取的语法格式如下：
```
变量[头下标:尾下标]
```

## bool（布尔类型）
- bool 是 int 的子类，因此布尔值可以被看作整数来使用，其中 True 等价于 1
- 布尔类型也可以被转换成其他数据类型，比如整数、浮点数和字符串。在转换时，True 会被转换成 1，False 会被转换成 0。

## List（列表）

- 1、列表写在**方括号**之间，元素用逗号隔开。
- 2、和字符串一样，列表可以被索引和切片。
- 3、列表可以使用 + 操作符进行拼接。
- 4、列表中的元素是可以改变的
- 5、列表截取可以接收第三个参数，参数作用是截取的步长
## Tuple（元组）

元组（tuple）与列表类似，不同之处在于**元组的元素不能修改**。元组写在**小括号** () 里，元素之间用逗号隔开。
- 1、与字符串一样，元组的元素不能修改。
- 2、元组也可以被索引和切片，方法一样。
- 3、注意构造包含 0 或 1 个元素的元组的特殊语法规则。
- 4、元组也可以使用 + 操作符进行拼接。
- 5、列表中的对象可以是可变的
## Set（集合）

Python 中的集合（Set）是一种无序、可变的数据类型，用于存储**唯一**的元素。

集合中的元素**不会重复**，并且可以进行**交集&、并集|、差集-、不同时存在^**等常见的集合操作。

在 Python 中，集合使用**大括号 {}** 表示，元素之间用逗号 , 分隔。

另外，也可以使用 set() 函数创建集合。
**注意：** 创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。

## Dictionary（字典）

**列表是有序的**对象集合，**字典是无序的**对象集合。两者之间的区别在于：字典当中的元素是通过键来存取的，而不是通过偏移存取。
字典通过**键值对**存储数据 ：key 

## Python数据类型转换
数据类型的转换，你只需要将数据类型作为函数名即可

# Python3 数据类型转换
Python 数据类型转换可以分为两种：

- 隐式类型转换 - 自动完成 较低的数据类型会自动转换成较高的数据类型
- 显式类型转换 - 需要使用类型函数来转换
# Python3 解释器
# Python3 运算符

## Python逻辑运算符
与and
或or
非not

**注意**：对于数字类型，以下规则适用：
- 任何非零的数值（包括正整数、负整数、正浮点数、负浮点数）都被视为`True`。
- 数字`0`（无论是整数`0`还是浮点数`0.0`）被视为`False`。
## Python成员运算符

in
not in

## Python身份运算符
身份运算符用于**比较两个对象的存储单元**,或者说判断两个标识符**是不是引用自一个对象**
```python
is 与 == 区别：

is 用于判断两个变量**引用对象是否为同一个**， == 用于判断引用**变量的值**是否相等。

b = a[:] 这里是把列表a 浅拷贝给b
```


# Python3 数字(Number)

Python 数字数据类型用于存储数值。

数据类型是不允许改变的，这就意味着**如果改变数字数据类型的值，将重新分配内存空间**。

实例在变量赋值时 Number 对象将被创建

python 支持三种不同的数值类型

- 整形(int)
- 浮点型(float)
- 复数(complex)
# Python3 字符串

Python 不支持单字符类型，单字符在 Python 中也是作为一个字符串使用。

## f-string
是 python3.6 之后版本添加的，称之为字面量格式化字符串
**f-string** 格式化字符串以 f 开头，后面跟着字符串，字符串中的表达式用大括号 {} 包起来，它会将变量或表达式计算后的值替换进去，实例如下：
```python
>>> name = 'Runoob'
>>> f'Hello {name}'  # 替换变量
'Hello Runoob'
>>> f'{1+2}'         # 使用表达式
'3'

>>> w = {'name': 'Runoob', 'url': 'www.runoob.com'}
>>> f'{w["name"]}: {w["url"]}'
'Runoob: www.runoob.com'
```

## Python 的字符串内建函数
略

# Python3 列表list

序列是 Python 中最基本的数据结构

序列中的每个值都有对应的位置值，称之为索引，第一个索引是 0，第二个索引是 1，依此类推。

Python 有 6 个序列的内置类型，但最常见的是**列表**和**元组**。

创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：

```python
list1 = ['Google', 'Runoob', 1997, 2000]
list2 = [1, 2, 3, 4, 5 ]
list3 = ["a", "b", "c", "d"]
list4 = ['red', 'green', 'blue', 'yellow', 'white', 'black']
```

## 更新列表

append() 在列表末尾插入

## 删除列表元素

 del 语句来删除列表中的元素
## Python列表脚本操作符

+ 号用于组合列表，* 号用于重复列表。
## 列表比较

## Python列表函数&方法

关于列表的增删查改功能

# Python3 元组tuple

Python 的元组与列表类似，不同之处在于**元组里的元素不能修改**。

元组使用小括号 ( )，列表使用方括号 [ ]。

## 修改元组

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合，如下实例:

```python
#!/usr/bin/python3
 
tup1 = (12, 34.56)
tup2 = ('abc', 'xyz')
 
# 以下修改元组元素操作是非法的。
# tup1[0] = 100
 
# 创建一个新的元组
tup3 = tup1 + tup2
print (tup3)
```

## 删除元组

元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组

## 元组运算符

## 关于元组是不可变的

所谓元组的不可变指的是元组**所指向的内存中的内容**不可变。

```python
>>> tup = ('r', 'u', 'n', 'o', 'o', 'b')
>>> tup[0] = 'g'     # 不支持修改元素
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> id(tup)     # 查看内存地址
4440687904
>>> tup = (1,2,3)
>>> id(tup)
4441088800    # 内存地址不一样了
```

# Python3 字典dict

字典是另一种**可变**容器模型，且可存储任意类型对象。

用 key 和 value 来存储对象  对象和对象之间用,分割，整个字典包括在花括号{} 中

**键必须是唯一**的，但值则不必。

## 创建空字典

使用大括号 { } 创建空字典

使用内建函数 dict() 创建字典

## 访问字典里的值

把相应的键放入到**方括号**中，如下实例:

```python
#!/usr/bin/python3
 
tinydict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
 
print ("tinydict['Name']: ", tinydict['Name'])
print ("tinydict['Age']: ", tinydict['Age'])
```
## 修改字典

向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对

## 删除字典元素

能删单一的元素也能清空字典，清空只需一项操作。

显式删除一个字典用del命令，如下实例:

```python
#!/usr/bin/python3
 
tinydict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
 
del tinydict['Name'] # 删除键 'Name'
tinydict.clear()     # 清空字典
del tinydict         # 删除字典
 
print ("tinydict['Age']: ", tinydict['Age'])
print ("tinydict['School']: ", tinydict['School'])
```

### 字典键的特性

字典**值可以是任何的 python 对象**，既可以是标准的对象，也可以是用户定义的，但键不行。

两个重要的点需要记住：

1）唯一性：不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住

2）不可变性：键必须不可变，所以可以用数字，字符串或元组充当，**而用列表就不行**（因为列表是可变的 ）

# Python3 集合set

集合（set）是一个**无序的不重复**元素序列。

集合中的元素不会重复，并且可以进行交集、并集、差集等常见的集合操作。

可以使用**大括号 { }** 创建集合，元素之间用逗号 , 分隔， 或者也可以使用 **set() 函数**创建集

## 集合的基本操作

### 1、添加元素
**语法格式如下：**
```
s.add( x )
```

将元素 x 添加到集合 s 中，如果元素已存在，则不进行任何操作。

还有一个方法，也可以添加元素，且**参数可以是列表，元组，字典等**，语法格式如下：

```
s.update( x )
```

### 2、移除元素

**语法格式如下：**

```
s.remove( x )
```

将元素 x 从集合 s 中移除，**如果元素不存在，则会发生错误**。

此外还有一个方法也是移除集合中的元素，且**如果元素不存在，不会发生错误**。格式如下所示：

```
s.discard( x )
```

我们也可以设**置随机删除集合中的一个元素**，语法格式如下：
```
s.pop() 
```

### 3、计算集合元素个数

```
len(s)
```

### 4、清空集合

```
s.clear()
```

### 5、判断元素是否在集合中存在

```
x in s
```

# Python3 条件控制
## if 语句
```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
```
Python 中用 **elif** 代替了 **else if**，所以if语句的关键字为：**if – elif – else**。
**注意：**

- 1、每个条件后面要使用冒号 :，表示接下来是满足条件后要执行的语句块。
- 2、使用缩进来划分语句块，相同缩进数的语句在一起组成一个语句块。
- 3、在 Python 中没有 switch...case 语句

## if 嵌套
在嵌套 if 语句中，可以把 if...elif...else 结构放在另外一个 if...elif...else 结构中。

# Python3 循环语句
## while 循环
```
while 判断条件(condition)：
    执行语句(statements)……
```

### 无限循环

我们可以通过设置条件表达式永远不为 false 来实现无限循环

### while 循环使用 else 语句
如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

```
语法格式如下：

while <expr>:
    <statement(s)>
else:
    <additional_statement(s)>
```

### 简单语句组

如果你的 while 循环体中只有一条语句，你可以将该语句与 while 写在同一行中

## for 语句

Python for 循环可以遍历任何**可迭代对象**，如一个列表或者一个字符串。

for循环的一般格式如下：

```
for <variable> in <sequence>: 
	<statements> 
else: 
	<statements>
```

## for...else

在 Python 中，for...else 语句用于在**循环结束后**执行一段代码。但是如果在循环过程中遇到了 break 语句，则会中断循环，此时不会执行 else 子句。

## range() 函数

如果你需要遍历数字序列，可以使用内置 range() 函数。它会生成数列，例如:

您可以结合 range() 和 len() 函数以遍历一个序列的索引,如下所示:
```
>>>a = ['Google', 'Baidu', 'Runoob', 'Taobao', 'QQ']
>>> for i in range(len(a)):
...     print(i, a[i])
... 
0 Google
1 Baidu
2 Runoob
3 Taobao
4 QQ
>>>
```

## break 和 continue 语句及循环中的 else 子句

**break** 语句可以**跳出 for 和 while 的循环体**。如果你从 for 或 while 循环中终止，任何对应的循环 else 块将不执行。

**continue** 语句被用来告诉 Python **跳过当前循环块中的剩余语句**，然后继续进行下一轮循环。

## pass 语句
Python pass是**空语句**，是为了保持程序结构的完整性。

pass 不做任何事情，一般用做占位语句，如下：

```
>>>while True: ... pass # 等待键盘中断 (Ctrl+C)
```
# Python 推导式

Python 推导式是一种独特的数据处理方式，**可以从一个数据序列构建另一个新的数据序列的结构体**。
Python 支持各种数据结构的推导式：
- 列表(list)推导式
- 字典(dict)推导式
- 集合(set)推导式
- 元组(tuple)推导式
## 列表推导式

列表推导式格式为：
```
[表达式 for 变量 in 列表] 
[out_exp_res for out_exp in input_list]

或者 

[表达式 for 变量 in 列表 if 条件]
[out_exp_res for out_exp in input_list if condition]
```

- out_exp_res：列表生成元素表达式，可以是有返回值的函数。
- for out_exp in input_list：迭代 input_list 将 out_exp 传入到 out_exp_res 表达式中。
- if condition：条件语句，可以过滤列表中不符合条件的值。

过滤掉长度小于或等于3的字符串列表，并将剩下的转换成大写字母：

```
>>> names = ['Bob','Tom','alice','Jerry','Wendy','Smith']
>>> new_names = [name.upper()for name in names if len(name)>3]
>>> print(new_names)
['ALICE', 'JERRY', 'WENDY', 'SMITH']
```

## 字典推导式

字典推导基本格式：

```
{ key_expr: value_expr for value in collection }

或

{ key_expr: value_expr for value in collection if condition }


```

使用字符串及其长度创建字典：

```
listdemo = ['Google','Runoob', 'Taobao']
# 将列表中各字符串值为键，各字符串的长度为值，组成键值对
>>> newdict = {key:len(key) for key in listdemo}
>>> newdict
{'Google': 6, 'Runoob': 6, 'Taobao': 6}
```

## 集合推导式

集合推导式基本格式：
```
{ expression for item in Sequence }
或
{ expression for item in Sequence if conditional }
```
判断不是 abc 的字母并输出：
```
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'d', 'r'}
>>> type(a)
<class 'set'>
```
## 元组推导式（生成器表达式）

# Python3 迭代器与生成器
迭代是 Python 最强大的功能之一，是访问集合元素的一种方式。

迭代器是一个可以记住遍历的位置的对象。

迭代器对象**从集合的第一个元素开始访问**，**直到所有的元素被访问完结束**。迭代器只能往前不会后退。

迭代器有两个基本的方法：**iter()** 和 **next()**。

字符串，列表或元组对象都可用于创建迭代器
```python
>>> list=[1,2,3,4]
>>> it = iter(list)    # 创建迭代器对象
>>> print (next(it))   # 输出迭代器的下一个元素
1
>>> print (next(it))   #输出迭代器的下一个元素
2
>>>
```

迭代器对象可以使用常规for语句进行遍历：

```
#!/usr/bin/python3
 
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
for x in it:
    print (x, end=" ")
```
也可以使用 next() 函数,用法一样

### 创建一个迭代器

把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。

__iter__() 方法返回一个特殊的迭代器对象， 这个迭代器对象实现了 __next__() 方法并通过 StopIteration 异常标识迭代的完成。

__next__() 方法（Python 2 里是 next()）会返回下一个迭代器对象

### StopIteration

StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况，在 __next__() 方法中我们可以设置在完成指定循环次数后触发 StopIteration 异常来结束迭代。

## 生成器
在 Python 中，**使用了 yield 的函数**被**称为生成器（**generator）。

**yield** 是一个**关键字**，用于定义生成器函数，生成器函数是一种特殊的函数，可以在迭代过程中逐步产生值，而不是一次性返回所有结果。

跟普通函数不同的是，**生成器是一个返回迭代器的函数**，只能用于迭代操作，更简单点理解生成器就是一个迭代器。

当在生成器**函数中使用** **yield** 语句时，函数的执行将会暂停，并将 **yield 后面的表达式**作为当前迭代的值**返回**。（停）

然后，每次调用生成器的 **next()** 方法或使用 **for** 循环进行迭代时，函数会从上次暂停的地方继续执行，直到再次遇到 **yield** 语句。（动）

这样，生成器函数可以**逐步产生值**，而不需要一次性计算并返回所有结果。（使用next和yield进行生成控制）

调用一个生成器函数，返回的是一个迭代器对象。

下面是一个简单的示例，展示了生成器函数的使用：

```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1
 
# 创建生成器对象
generator = countdown(5)
 
# 通过迭代生成器获取值
print(next(generator))  # 输出: 5
print(next(generator))  # 输出: 4
print(next(generator))  # 输出: 3
 
# 使用 for 循环迭代生成器
for value in generator:
    print(value)  # 输出: 2 1
```

生成器函数的优势是它们可以按需生成值，避免一次性生成大量数据并占用大量内存。此外，生成器还可以与其他迭代工具（如for循环）无缝配合使用，提供简洁和高效的迭代方式。

# Python3 函数
## 定义一个函数

以下是简单的规则：

- 函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号 **()**。
- 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。
- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
- 函数内容以冒号 : 起始，并且缩进。
- **return [表达式]** 结束函数，选择性地返回一个值给调用方，不带表达式的 return 相当于返回 None。
### 语法

Python 定义函数使用 def 关键字，一般格式如下：

```
def 函数名（参数列表）:
    函数体
```

默认情况下，参数值和参数名称是按函数声明中定义的顺序匹配起来的。

## 函数调用

## 参数传递

在 python 中，类型属于对象，对象有不同类型的区分，变量是没有类型的：

```
a=[1,2,3]
a="Runoob"
```
以上代码中，**[1,2,3]** 是 List 类型，**"Runoob"** 是 String 类型，而变量 a 是没有类型，她仅仅是一个对象的引用（一个指针），可以是指向 List 类型对象，也可以是指向 String 类型对象。

### 可更改(mutable)与不可更改(immutable)对象

在 python 中，strings, tuples, 和 numbers 是不可更改的对象，而 list,dict 等则是可以修改的对象。

- **不可变类型：** 变量赋值 **a=5** 后再赋值 **a=10**，这里实际是**新生成一个** int 值对象 10，再让 a 指向它，而 5 被丢弃，不是改变 a 的值，相当于新生成了 a。
    
- **可变类型：** 变量赋值 **la=[1,2,3,4]** 后再赋值 **la[2]=5** 则是将 list la 的第三个元素值更改，本身la没有动，只是其内部的一部分值被修改了'

python 函数的参数传递：

- **不可变类型：** 类似 C++ 的值传递，如整数、字符串、元组。如 fun(a)，传递的只是 a 的值，没有影响 a 对象本身。如果在 fun(a) 内部修改 a 的值，则是**新生成一个 a 的对象**。
    
- **可变类型：** 类似 C++ 的引用传递，如 列表，字典。如 fun(la)，则是将 la 真正的传过去，**修改后 fun 外部的 la 也会受影响**
    

python 中一切都是对象，严格意义我们不能说值传递还是引用传递，我们应该说传不可变对象和传可变对象。

## 参数

以下是调用函数时可使用的正式参数类型：

- 必需参数
- 关键字参数
- 默认参数
- 不定长参数
### 必需参数

必需参数须**以正确的顺序传入函数**。**调用时的数量必须和声明时的一样**。

### 关键字参数

关键字参数和函数调用关系紧密，函数调用**使用关键字参数来确定传入的参数值。**

**使用关键字参数允许函数调用时参数的顺序与声明时不一致**，因为 Python 解释器能够用参数名匹配参数值。

### 默认参数
调用函数时，如果没有传递参数，则会使用默认参数。以下实例中如果没有传入 age 参数，则使用默认值：
#!/usr/bin/python3
 
```python
#可写函数说明
def printinfo( name, age = 35 ):
   "打印任何传入的字符串"
   print ("名字: ", name)
   print ("年龄: ", age)
   return
 
#调用printinfo函数
printinfo( age=50, name="runoob" )
print ("------------------------")
printinfo( name="runoob" )
```
### 不定长参数

一个函数能处理比当初声明时更多的参数。这些参数叫做不定长参数，和上述 2 种参数不同，声明时不会命名。基本语法如下：
```
def functionname([formal_args,] *var_args_tuple ):
   "函数_文档字符串"
   function_suite
   return [expression]
```

加了星号 * 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。
还有一种就是参数带两个星号 ** , 加了两个星号 ** 的参数会以字典的形式导入。


#!/usr/bin/python3
  
```
# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
# 调用printinfo 函数
printinfo( 70, 60, 50 )
```

```
#!/usr/bin/python3
  
# 可写函数说明
def printinfo( arg1, **vardict ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vardict)
 
# 调用printinfo 函数
printinfo(1, a=2,b=3)
```

如果在函数调用时没有指定参数，它就是一个空元组。我们也可以不向函数传递未命名的变量。

#!/usr/bin/python3
 
```
# 可写函数说明
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   for var in vartuple:
      print (var)
   return
 
# 调用printinfo 函数
printinfo( 10 )
printinfo( 70, 60, 50 )
```

声明函数时，参数中星号 * 可以单独出现，例如:
```
def f(a,b,*,c):
    return a+b+c
```
如果单独出现星号 * ，则星号 * 后的参数必须用关键字传入

## 匿名函数
Python 使用 lambda 来创建匿名函数。\

### 语法

lambda 函数的语法只包含一个语句，如下：
```python
lambda [arg1 [,arg2,.....argn]]:expression
```

以下实例匿名函数设置两个参数：

#!/usr/bin/python3
 
```
# 可写函数说明
sum = lambda arg1, arg2: arg1 + arg2
 
# 调用sum函数
print ("相加后的值为 : ", sum( 10, 20 ))
print ("相加后的值为 : ", sum( 20, 20 ))
```

我们可以将匿名函数封装在一个函数内，这样可以使用同样的代码来创建多个匿名函数。(套娃)
以下实例将匿名函数封装在 myfunc 函数中，通过传入不同的参数来创建不同的匿名函数：
```
def myfunc(n):
  return lambda a : a * n
 
mydoubler = myfunc(2)
mytripler = myfunc(3)
 
print(mydoubler(11))
print(mytripler(11))
```
## return 语句

**return [表达式]** 语句用于退出函数，**选择性地**向调用方返回一个表达式。不带参数值的 return 语句返回 None。

# Python lambda（匿名函数）

lambda 函数通常用于编写简单的、单行的函数，通常在需要函数作为参数传递的情况下使用，例如在 map()、filter()、reduce() 等函数中。
**lambda 语法格式：**
```
lambda arguments: expression
```
- `lambda`是 Python 的关键字，用于定义 lambda 函数。
- `arguments` 是参数列表，可以包含零个或多个参数，但必须在冒号(`:`)前指定。
- `expression` 是一个表达式，用于计算并返回函数的结果
# Python 装饰器

装饰器（decorators）是 Python 中的一种高级功能，它**允许你动态地修改函数或类的行为**。

**装饰器是一种函数**，它接受一个函数作为参数，并返回一个新的函数或修改原来的函数。

**装饰器是修改函数的函数**

装饰器的语法使用 @decorator_name 来应用在函数或方法上。

Python 还提供了一些内置的装饰器，比如 @staticmethod 和 @classmethod，用于定义静态方法和类方法。

### 基本语法

Python 装饰允许在不修改原有函数代码的基础上，动态地增加或修改函数的功能，装饰器本质上是一个接收函数作为输入并返回一个新的包装过后的函数的对象。

```python
def decorator_function(original_function):
    def wrapper(*args, **kwargs):
        # 这里是在调用原始函数前添加的新功能
        before_call_code()
        
        result = original_function(*args, **kwargs)
        
        # 这里是在调用原始函数后添加的新功能
        after_call_code()
        
        return result
    return wrapper

# 使用装饰器
@decorator_function
def target_function(arg1, arg2):
    pass  # 原始函数的实现
```

**解析：** decorator 是一个装饰器函数，它**接受一个函数 func 作为参数**，并**返回一个内部函数** **wrapper(包装)**，在 wrapper 函数内部，你可以执行一些额外的操作，然后调用原始函数 func，并返回其结果。

- `decorator_function` 是装饰器，它接收一个函数 `original_function` 作为参数。
- `wrapper` 是内部函数，它是实际会被调用的新函数，它包裹了原始函数的调用，并在其前后增加了额外的行为。
- 当我们使用 `@decorator_function` 前缀在 `target_function` 定义前，Python会自动将 `target_function` 作为参数传递给 `decorator_function`，然后将返回的 `wrapper` 函数替换掉原来的 `target_function`。
### 使用装饰器

装饰器通过 @ 符号应用在函数定义之前，例如：

```python
@time_logger
def target_function():
    pass
```

等同于：

```python
def target_function():
    pass
target_function = time_logger(target_function)
```

这会将 target_function 函数传递给 decorator 装饰器，并将返回的函数重新赋值给 target_function。从而，每次调用 target_function 时，实际上是调用了经过装饰器处理后的函数。

通过装饰器，开发者可以在保持代码整洁的同时，灵活且高效地扩展程序的功能。

### 类装饰器

除了函数装饰器，Python 还支持类装饰器。类装饰器是包含 __call__ 方法的类，它接受一个函数作为参数，并返回一个新的函数。

```
class DecoratorClass:
    def __init__(self, func):
        self.func = func
    
    def __call__(self, *args, **kwargs):
        # 在调用原始函数之前/之后执行的代码
        result = self.func(*args, **kwargs)
        # 在调用原始函数之后执行的代码
        return result

@DecoratorClass
def my_function():
    pass
```

# Python3 数据结构
## 列表
Python中列表是可变的，这是它区别于字符串和元组的最重要的特点，一句话概括即：列表可以修改，而字符串和元组不能。
## 将列表当做栈使用
列表提供了一些方法，使其非常适合用于栈操作，特别是 **append()** 和 **pop()** 方法。

用 append() 方法可以把一个元素添加到栈顶，用不指定索引的 pop() 方法可以把一个元素从栈顶释放出来。

## 将列表当作队列使用

在 Python 中，列表（list）可以用作队列（queue），但由于列表的特点，直接使用列表来实现队列并不是最优的选择。

使用列表时，如果频繁地在列表的开头插入或删除元素，性能会受到影响，因为这些操作的时间复杂度是 O(n)。为了解决这个问题，**Python 提供了 collections.deque，它是双端队列，可以在两端高效地添加和删除元素**。

deque(双端队列)

## 元组和序列

## 集合
注意：如果要创建一个空集合，你必须用 set() 而不是 {} ；后者创建一个空的字典

## 字典
理解字典的最佳方式是把它看做无序的键=>值对集合。在同一个字典之内，关键字必须是互不相同。一对大括号创建一个空的字典：{}。

## 遍历技巧

在字典中遍历时，关键字和对应的值可以使用 items() 方法同时解读出来：
```
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```

在序列中遍历时，索引位置和对应值可以使用 enumerate() 函数同时得到：

```
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```
同时遍历两个或更多的序列，可以使用 zip() 组合：

```
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```
要按顺序遍历一个序列，使用 sorted() 函数返回一个已排序的序列，并不修改原值：

```
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
```
# Python3 模块

模块是一个包含所有你定义的函数和变量的文件，其后缀名是.py。模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用 python 标准库的方法。
## import 语句

想使用 Python 源文件，只需在另一个源文件里执行 import 语句

## from … import 语句

Python 的 from 语句让你从模块中导入一个指定的部分到当前命名空间中，语法如下：

```
from modname import name1[, name2[, ... nameN]]
```

## from … import * 语句

把一个模块的所有内容全都导入到当前的命名空间也是可行的

## 深入模块

模块除了方法定义，还可以包括可执行的代码。这些代码一般用来初始化这个模块。这些代码只有在第一次被导入时才会被执行。

可以使用 import 直接把模块内（函数，变量的）名称导入到当前操作模块

```
>>> from fibo import fib, fib2
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

这种导入的方法不会把被导入的模块的名称放在当前的字符表中（所以在这个例子里面，fibo 这个名称是没有定义的）。

这还有一种方法，可以一次性的把模块中的所有（函数，变量）名称都导入到当前模块的字符表:

```
>>> from fibo import *
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

这将把所有的名字都导入进来，但是那些由单一下划线（_ ) 开头的名字不在此例。大多数情况， Python程序员不使用这种方法，因为**引入的其它来源的命名，很可能覆盖了已有的定义**。

## `__name__属性`


一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以**用__name__属性来使该程序块仅在该模块自身运行时执行**。

#!/usr/bin/python3
# Filename: using_name.py

```
#!/usr/bin/python3
# Filename: using_name.py

if __name__ == '__main__':
   print('程序自身在运行')
else:
   print('我来自另一模块')
```
运行输出如下：

```
$ python using_name.py
程序自身在运行

$ python
>>> import using_name
我来自另一模块
>>>
```

**说明：** 每个模块都有一个__name__属性，当其值是'__main__'时，表明该模块自身在运行，否则是被引入。
## dir() 函数

内置的函数 dir() 可以找到模块内定义的所有名称。以一个字符串列表的形式返回

如果没有给定参数，那么 dir() 函数会罗列出当前定义的所有名称

## 标准模块
Python 本身带着一些标准的模块库

## 包

包是一种管理 Python 模块命名空间的形式，采用"点模块名称"。

比如一个模块的名称是 A.B， 那么他表示一个包 A中的子模块 B 。

不妨假设你想设计一套统一处理声音文件和数据的模块（或者称之为一个"包"）。

现存很多种不同的音频文件格式（基本上都是通过后缀名区分的，例如： .wav，:file:.aiff，:file:.au，），所以你需要有一组不断增加的模块，用来在不同的格式之间转换。

并且针对这些音频数据，还有很多不同的操作（比如混音，添加回声，增加均衡器功能，创建人造立体声效果），所以你还需要一组怎么也写不完的模块来处理这些操作。

这里给出了一种可能的包结构（在分层的文件系统中）:

```
sound/                          顶层包
      __init__.py               初始化 sound 包
      formats/                  文件格式转换子包
              __init__.py
              wavread.py
              wavwrite.py
              aiffread.py
              aiffwrite.py
              auread.py
              auwrite.py
              ...
      effects/                  声音效果子包
              __init__.py
              echo.py
              surround.py
              reverse.py
              ...
      filters/                  filters 子包
              __init__.py
              equalizer.py
              vocoder.py
              karaoke.py
              ...
```

在导入一个包的时候，Python 会根据 sys.path 中的目录来寻找这个包中包含的子目录。

**目录只有包含一个叫做 init.py 的文件才会被认作是一个包**，主要是为了避免一些滥俗的名字（比如叫做 string）不小心的影响搜索路径中的有效模块。

最简单的情况，放一个空的 :file:__init__.py就可以了。当然这个文件中也可以包含一些初始化代码或者为__all__变量赋值。

用户可以每次只导入一个包里面的特定模块，比如:

```
import sound.effects.echo
```
这将会导入子模块:sound.effects.echo。 他必须使用全名去访问:

```
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
```

还有一种导入子模块的方法是:
```
from sound.effects import echo
```

这同样会导入子模块: echo，并且他不需要那些冗长的前缀，所以他可以这样使用:

```
echo.echofilter(input, output, delay=0.7, atten=4)
```

还有一种变化就是直接导入一个函数或者变量:

```
from sound.effects.echo import echofilter
```

同样的，这种方法会导入子模块: echo，并且可以直接使用他的 echofilter() 函数

```
echofilter(input, output, delay=0.7, atten=4)
```
**注意:** 当使用 from package import item 这种形式的时候，对应的 item 既可以是包里面的子模块（子包），或者包里面定义的其他名称，比如函数，类或者变量。

# Python3 输入和输出
## 输出格式美化

Python两种输出值的方式: 表达式语句和 print() 函数。

第三种方式是使用文件对象的 write() 方法，标准输出文件可以用 sys.stdout 引用。

如果你希望输出的形式更加多样，可以使用 str.format() 函数来格式化输出值。

如果你希望将输出的值转成字符串，可以使用 repr() 或 str() 函数来实现。

- **str()：** 函数返回一个用户易读的表达形式。
- **repr()：** 产生一个解释器易读的表达形式。
## 旧式字符串格式化

## 读取键盘输入

Python 提供了 [input() 内置函数](https://www.runoob.com/python3/python3-func-input.html)从标准输入读入一行文本，默认的标准输入是键盘。

## 读和写文件

open() 将会返回一个 file 对象，基本语法格式如下:

open(filename, mode)

- filename：包含了你要访问的文件名称的字符串值。
- mode：决定了打开文件的模式：只读，写入，追加等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。
## 文件对象的方法
### f.read()
### f.readline()
### f.readlines()
### f.write()
### f.tell()

### f.seek()

### f.close()

## pickle 模块

python的pickle模块实现了基本的数据序列和反序列化。

通过pickle模块的**序列化操作**我们能够**将程序中运行的对象信息保存到文件中去，永久存储**。

通过pickle模块的**反序列化操作**，我们**能够从文件中创建上一次程序保存的对象**。

# Python3 File(文件) 方法
### open() 方法

Python open() 方法用于打开一个文件，并返回文件对象。
**注意：** 使用 open() 方法一定要保证关闭文件对象，即调用 close() 方法。

### file 对象

file 对象使用 open 函数来创建

# Python3 OS 文件/目录方法
**os** 模块提供了非常丰富的方法用来处理文件和目录。

# Python3 错误和异常

Python 有两种错误很容易辨认：语法错误和异常。

Python assert（断言）用于判断一个表达式，在表达式条件为 false 的时候触发异常

## 语法错误

## 异常

即便 Python 程序的语法是正确的，在运行它的时候，也有可能发生错误。运行期检测到的错误被称为异常。（Java 中的 运行时异常） 
大多数的异常都不会被程序处理，都以错误信息的形式展现

## 异常处理
### try/except

异常捕捉可以使用 try/except 语句。
![[Pasted image 20240725113300.png]]以下例子中，让用户输入一个合法的整数，但是允许用户中断这个程序（使用 Control-C 或者操作系统提供的方法）。用户中断的信息会引发一个 KeyboardInterrupt 异常。

```
while True:
    try:
        x = int(input("请输入一个数字: "))
        break
    except ValueError:
        print("您输入的不是数字，请再次尝试输入！")
```
try 语句按照如下方式工作；

- 首先，执行 try 子句（在关键字 try 和关键字 except 之间的语句）。
    
- 如果没有异常发生，忽略 except 子句，try 子句执行后结束。
    
- 如果在执行 try 子句的过程中发生了异常，那么 try 子句余下的部分将被忽略。**如果异常的类型和 except 之后的名称相符**，那么对应的 except 子句将被执行。
    
- 如果一个异常没有与任何的 except 匹配，那么这个异常将会传递给上层的 try 中。
    

一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多只有一个分支会被执行。

处理程序将只针对对应的 try 子句中的异常进行处理，而不是其他的 try 的处理程序中的异常。

一个except子句可以同时处理多个异常，这些异常将被放在一个括号里成为一个元组, 例如:
```
except (RuntimeError, TypeError, NameError):
    pass
```

最后一个except子句可以忽略异常的名称，它将被当作通配符使用。你可以使用这种方法打印一个错误信息，然后再次把异常抛出。
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
    raise
    # 在这个Python代码片段中，`raise` 关键字被用于在捕获到除 `OSError` 和 `ValueError` 之外的任何异常时，重新抛出该异常。
```

### try/except...else

try/except 语句还有一个可选的 **else** 子句，如果使用这个子句，那么必须放在所有的 except 子句之后。

else 子句将在 **try 子句没有发生任何异常的时候执行**
![[Pasted image 20240725123237.png]]

### try-finally 语句

try-finally 语句**无论是否发生异常都将执行**最后的代码。
![[Pasted image 20240725123312.png]]
## 用户自定义异常

你可以通过创建一个新的异常类来拥有自己的异常。**异常类继承自 Exception 类**，可以直接继承，或者间接继承

```python
>>> class MyError(Exception):
        def __init__(self, value):
            self.value = value
        def __str__(self):
            return repr(self.value)
   
>>> try:
        raise MyError(2*2)
    except MyError as e:
        print('My exception occurred, value:', e.value)
   
My exception occurred, value: 4
>>> raise MyError('oops!')
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
__main__.MyError: 'oops!'
```

## 定义清理行为

try 语句还有另外一个可选的子句，它定义了无论在任何情况下都会执行的清理行为。

## 预定义的清理行为

一些对象定义了标准的清理行为，无论系统是否成功的使用了它，一旦不需要它了，那么这个标准的清理行为就会执行。
# Python3 面向对象
## 面向对象技术简介

- **类(Class):** 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
- **方法：** 类中定义的函数。
- **类变量：** 类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
- **数据成员：** 类变量或者实例变量用于处理类及其实例对象的相关的数据。
- **方法重写：** 如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
- **局部变量：** 定义在方法中的变量，只作用于当前实例的类。
- **实例变量：** 在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 self 修饰的变量。
- **继承：** 即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
- **实例化：** 创建一个类的实例，类的具体对象。
- **对象：** 通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

Python中的类提供了面向对象编程的所有基本功能：类的继承机制允许多个基类，派生类可以覆盖基类中的任何方法，方法中可以调用基类中的同名方法。

对象可以包含任意数量和类型的数据。

## 类定义

语法格式如下：

```
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```
类实例化后，可以使用其属性，实际上，创建一个类之后，可以通过类名访问其属性。

## 类对象
类对象支持两种操作：属性引用和实例化。

属性引用使用和 Python 中所有的属性引用一样的标准语法：**obj.name**。

类对象创建后，类命名空间中所有的命名都是有效属性名。所以如果类定义是这样:

```python
#!/usr/bin/python3
 
class MyClass:
    """一个简单的类实例"""
    i = 12345
    def f(self):
        return 'hello world'
 
# 实例化类
x = MyClass()
 
# 访问类的属性和方法
print("MyClass 类的属性 i 为：", x.i)
print("MyClass 类的方法 f 输出为：", x.f())
```
以上创建了一个新的类实例并将该对象赋给局部变量 x，x 为空的对象。

类有一个名为 \__ init \__ () 的特殊方法（**构造方法**），该方法在类实例化时会自动调用，像下面这样：

```
def __init__(self): 
	self.data = []
```

类定义了 __init__() 方法，类的实例化操作会自动调用 __init__() 方法。如下实例化类 MyClass，对应的 __init__() 方法就会被调用:

```
x = MyClass()
```

当然， __init__() 方法可以有参数，参数通过 __init__() 传递到类的实例化操作上。例如:

```python
#!/usr/bin/python3
 
class Complex:
    def __init__(self, realpart, imagpart):
        self.r = realpart
        self.i = imagpart
x = Complex(3.0, -4.5)
print(x.r, x.i)   # 输出结果：3.0 -4.5
```
### self 代表类的实例，而非类

**类的方法**与**普通的函数**只有一个特别的区别——它们必须有一个额外的**第一个参数名称**, 按照惯例它的名称是 self。
```python
class Test:
    def prt(self):
        print(self)
        print(self.__class__)
 
t = Test()
t.prt()
```
以上实例执行结果为：
```
<__main__.Test instance at 0x100771878>
__main__.Test
```

从执行结果可以很明显的看出，**self 代表的是类的实例**，**代表当前对象的地址**，**而 self.class 则指向类**。

self 不是 python 关键字，我们把他换成 runoob 也是可以正常执行的

**在 Python中，self 是一个惯用的名称，用于表示类的实例（对象）自身**。它是一个指向实例的引用，使得类的方法能够访问和操作实例的属性。

当你定义一个类，并在类中定义方法时，第一个参数通常被命名为 self，尽管你可以使用其他名称，但强烈建议使用 self，以保持代码的一致性和可读性。

```python
class MyClass:
    def __init__(self, value):
        self.value = value

    def display_value(self):
        print(self.value)

# 创建一个类的实例
obj = MyClass(42) 

# 调用实例的方法
obj.display_value() # 输出 42
```

## 类的方法

在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，**类方法必须包含参数 self, 且为第一个参数**，self 代表的是类的实例。                                       

## 继承

Python 同样支持类的继承

```
class DerivedClassName(BaseClassName):
    <statement-1>
    .
    .
    .
    <statement-N>
```

子类（派生类 DerivedClassName）会继承父类（基类 BaseClassName）的属性和方法。

BaseClassName（实例中的基类名）必须与派生类定义在一个作用域内。除了类，还可以用表达式，基类定义在另一个模块中时这一点非常有用:

```
class DerivedClassName(modname.BaseClassName):
```

```python
#!/usr/bin/python3
 
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
 
 
s = student('ken',10,60,3)
s.speak()
```

## 多继承

Python同样**有限的支持多继承形式**。(Java中不支持多继承)多继承的类定义形如下例:
```python
class DerivedClassName(Base1, Base2, Base3):
    <statement-1>
    .
    .
    .
    <statement-N>
```
需要注意圆括号中父类的顺序，若是父类中有相同的方法名，而在子类使用时未指定，**python从左至右搜索** 即方法在子类中未找到时，从左到右查找父类中是否包含方法
#!/usr/bin/python3
 
```python
#类定义
class people:
    #定义基本属性
    name = ''
    age = 0
    #定义私有属性,私有属性在类外部无法直接进行访问
    __weight = 0
    #定义构造方法
    def __init__(self,n,a,w):
        self.name = n
        self.age = a
        self.__weight = w
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
 
#单继承示例
class student(people):
    grade = ''
    def __init__(self,n,a,w,g):
        #调用父类的构函
        people.__init__(self,n,a,w)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
 
#另一个类，多继承之前的准备
class speaker():
    topic = ''
    name = ''
    def __init__(self,n,t):
        self.name = n
        self.topic = t
    def speak(self):
        print("我叫 %s，我是一个演说家，我演讲的主题是 %s"%(self.name,self.topic))
 
#多继承
class sample(speaker,student):
    a =''
    def __init__(self,n,a,w,g,t):
        student.__init__(self,n,a,w,g)
        speaker.__init__(self,n,t)
 
test = sample("Tim",25,80,4,"Python")
test.speak()   #方法名同，默认调用的是在括号中参数位置排前父类的方法
```

执行以上程序输出结果为：

```
我叫 Tim，我是一个演说家，我演讲的主题是 Python
```

## 方法重写
如果你的父类方法的功能不能满足你的需求，你可以在子类重写你父类的方法

## 类属性与方法
### 类的私有属性

**__private_attrs**：两个下划线开头。在类内部的方法中使用时 **self.__private_attrs**。

### 类的方法

在类的内部，使用 def 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self，且为第一个参数，self 代表的是类的实例。

self 的名字并不是规定死的，也可以使用 this，但是最好还是按照约定使用 self。(Java中一般用this)

### 类的私有方法

**__private_method**：**两个下划线开头**，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用。**self.__private_methods**。

### 类的专有方法：

- **__init__ :** 构造函数，在生成对象时调用
- **__del__ :** 析构函数，释放对象时使用
- **__repr__ :** 打印，转换
- **__setitem__ :** 按照索引赋值
- **__getitem__:** 按照索引获取值
- **__len__:** 获得长度
- **__cmp__:** 比较运算
- **__call__:** 函数调用
- **__add__:** 加运算
- **__sub__:** 减运算
- **__mul__:** 乘运算
- **__truediv__:** 除运算
- **__mod__:** 求余运算
- **__pow__:** 乘方
### 运算符重载

Python同样支持运算符重载，我们可以对类的专有方法进行重载

# Python3 命名空间和作用域

# Python3 标准库概览
# Python3 pip

pip 是 Python 包管理工具，该工具提供了对 Python 包的查找、下载、安装、卸载的功能。

查看是否已经安装 pip 可以使用以下命令：

```
pip --version
```

下载安装包使用以下命令：
```
pip install some-package-name
```

例如我们安装 numpy 包：

```
pip install numpy
```

我们也可以轻易地通过以下的命令来移除软件包：

```
pip uninstall some-package-name
```

例如我们移除 numpy 包：

```
pip uninstall numpy
```

如果要查看我们已经安装的软件包，可以使用以下命令：

```
pip list
```

### 导出当前 Python 环境的配置

要导出当前 Python 环境的配置，你可以使用 pip freeze 命令。**freeze (冷冻贮藏 冻结 )**

pip freeze 命令会列出当前环境中已安装的所有 Python 包及其版本信息，你可以将其保存到文件中，例如 requirements.txt，如下所示：

```
pip freeze > requirements.txt
```

以上命令将在当前目录下创建一个名为 **requirements.txt** 的文件，其中包含当前环境中已安装的所有包及其版本信息。

然后，你可以在其他地方使用该文件来重新创建相同的环境，运行以下命令：

```
pip install -r requirements.txt
```

以上命令会根据 **requirements.txt** 中列出的包及其版本信息重新安装所有必需的包，从而重建相同的环境。

# Python中的xml文件解析

`tree = ET.parse(repo_file)` 返回的 `tree` 是一个 `xml.etree.ElementTree.ElementTree` 类型的对象。这个对象代表了解析后的XML文档，并提供了访问和操作XML数据的方法和属性。

具体来说，`xml.etree.ElementTree.ElementTree` 是一个用于处理XML数据的类，它提供了以下主要功能：

1. **解析XML文件**：通过 `ET.parse(repo_file)` 方法将XML文件解析为一个 `ElementTree` 对象。
2. **访问根元素**：通过 `tree.getroot()` 方法获取XML文档的根元素（`Element` 对象）。
3. **查找和遍历元素**：通过 `find()`, `findall()`, `iter()`, `iterfind()` 等方法查找和遍历XML文档中的元素。
4. **修改和写回XML**：通过 `ElementTree` 对象的方法修改XML数据，并将其写回到文件中。

例如，在你的代码中，解析后的 `tree` 对象被用来获取根元素并遍历XML文档中的元素

# Python中的命令行参数解析器

命令行参数解析器对象（如`argparse.ArgumentParser`）的主要用途是解析命令行参数和选项。它使得开发者能够轻松地从用户输入的命令行中提取参数，并将其转换为程序可以使用的数据结构。

**简单来说**，就是你在命令行中使用python example.py 命令运行一个python文件的时候，可以在后面添加自定义参数，而这个自定义参数可以被读取到程序中
```python
parser = argparse.ArgumentParser(description='')

```

# Python 中的细小知识点
- **Python 2**中使用 `u` 前缀表示 Unicode 字符串。**Python 3**中所有字符串默认是 Unicode，因此不需要 `u` 前缀


# Python中Excel处理的相关方法和库

- `load_workbook`
在 Python 中，`load_workbook` 是 `openpyxl` 库中的一个函数，用于加载现有的 Excel 工作簿（Workbook）。该函数从指定的 Excel 文件中读取数据，并**返回一个 Workbook** 对象，您可以通过这个对象**访问和操作 Excel 文件中的工作表**和**单元格数据**。

# 字典推导式
filtered_dict = {k:v for k, v in items_dict.items() if v['Name'] == target_name}

## 算法

```python
table = {}
table.get(num,0) #这是字典的 `get` 方法，它尝试获取 `table` 中键为 `num` 的值。如果 `num` 不存在于 `table` 中，则返回默认值 `0`。
```

**取数值各个位上的单数操作**
```python
# 首先将整数转化为字符串
n_str = str(n)

# 然后使用字符串的操作取出每一位
for ch in n_str:
	#然后再将每一位转化为数字
	n = int(ch)
```

**枚举**
```
# 返回数组中的索引和值
for index,value in enumerate(nums):
	
```
