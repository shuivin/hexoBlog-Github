---
title: Python进阶学习笔记
tags:
  - 进阶学习
  - 学习笔记
  - Python
categories: python从入门到精通
copyright: true
abbrlink: 1d8f9861
date: 2018-01-03 16:24:58
---

{% cq %} 进阶的基础是学会入门{% endcq %}

{% note  %} Python零基础入门课程学习完之后。我继续复习进阶知识。课程知识+个人总结以及知识点标注与相关难点探究。

- [√] 慕课网廖雪峰老师的: python进阶

{% endnote %}



<!--more-->

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/fmeLmg3Cfj.png?imageslim)

课程详细介绍Python强大的函数式编程和面向对象编程，掌握Python高级程序设计的方法。

# 打好基础再来进阶

在[基础入门笔记](http://blog.mtianyan.cn/2018/01/02/Python%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%85%A5%E9%97%A8%E7%AC%94%E8%AE%B0/#more)中我们学到了以下知识:

1. 安装Python环境
2. 变量和数据类型：Python内置的基本类型
3. List和Tuple：顺序的集合类型
4. 条件判断和循环：控制程序流程
5. Dict和Set：根据key访问的集合类型
6. 函数：定义和调用函数
7. 切片：如何对list进行切片
8. 迭代：如何用for循环迭代集合类型
9. 列表生成式:如何快速生成列表

注：我个人对于自认为重要的知识点都进行了`知识点`关键字标记。如果想复习的小伙伴可以
`ctrl + f` 输入关键字 `知识点` 进行查看。
对于重要以及较难的编程题目我进行了关键字 `天涯`的标记。

进阶课程中将会学到的知识：

- 函数式编程：注意与函数编程区别
- 模块：模块的使用
- 面向对象：概念，属性，方法，基础，多态。
- 定制类：利用Python的特殊方法定制类

学习目标：`掌握函数式编程` `掌握面向对象编程` `能够编写模块化的程序`

# Python函数式编程

讲解Python函数式编程概念，高阶函数的概念和实际用法，以及装饰器函数的原理和实现方式。

## 函数式编程简介

函数: function,入门课程学习过的
函数式：functional, 一种编程范式

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/2D0jkLJF7L.png?imageslim)

`函数式编程` 是一种抽象的编程模式

不同语言的抽象层次不同:

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/j5BFgIfGL2.png?imageslim)

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/kCAJl5AELJ.png?imageslim)

上图中语言越往上越高级，抽象程度越高。越往上抽象就逐渐向数学接近

知识点: 函数式编程的特点:

- 把计算视为函数而非指令(这样不贴近计算机而是贴进计算)
- 纯函数式编程: 不需要变量，没有副作用，测试简单。(函数任意执行多少次结果确定)
- 支持高阶函数，代码简洁

知识点: python支持的函数式编程

- 不是纯函数式编程：允许有变量
- 支持高阶函数：函数也可以作为变量传入
- 支持闭包：有了闭包就能返回函数
- 有限度的支持匿名函数。

## 高阶函数

高阶函数：

- 变量可以指向函数

demo:


直接输入`abs`返回的是一个函数对象。
而变量`f` 通过赋值运算符指向`abs函数对象`
然后此时`f`这个函数名就可以实现调用`abs()`

知识点: **函数名其实就是指向函数的一个变量(一个很普通的变量)**

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/mI85AiHJ0D.png?imageslim)

`abs` 就是一个**普通的**变量名。通过赋值运算符指向了python内置的`abs函数对象`。
我们可以把它当做普通变量处理。

知识点: **高阶函数高在自己能接受函数作为参数**

高阶函数: 能接收函数作为参数的函数。

- 变量可以指向函数
- 函数的参数可以接受变量 

所以一个函数可以接收另一个函数作为参数。这时我们把能接收函数做参数的函数成为高阶函数。

demo: 接受abs函数

- 定义一个函数，接收`x`,`y`,`f`三个参数。
- 其中`x`,`y `是数值，`f`是函数
- `def add(x,y,f)`
- `return f(x) + f(y)`

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/46d9BIKF7C.png?imageslim)

只要我们理解: 变量可以指向函数,函数可以作为一个变量传递给另一个函数就可以了。

待探究:

如果刚才我们一直没有关闭窗口。也就是我们的`abs`变量还指向的是`len`函数对象。

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/L4mgiEdD15.png?imageslim)

解决方案:

>暂无待续

## 把函数作为参数

上一节我们讲了高阶函数的概念，并编写了一个简单的高阶函数：

```python
def add(x, y, f):
    return f(x) + f(y)
```

如果传入`abs`作为参数`f`的值：

```python
add(-5, 9, abs)
```

根据函数的定义，函数执行的代码实际上是：

```python
abs(-5) + abs(9)
```

由于参数 `x`, `y` 和 `f `都可以任意传入，如果 `f `传入其他函数，就可以得到不同的返回值。

### 编程任务

>利用add(x,y,f)函数，计算：

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/C6Ib1GlF8A.png?imageslim)

注意: python中的`sqrt`函数在`math`包中。需要`import`进来
`import`的相关知识后面会讲的。这里只需要用一下。

```python
import math
# from math import sqrt

def add(x, y, f):
    return f(x) + f(y)

print add(25, 9,  math.sqrt)
# 如果采用第二行import方法调用时如下
print add(25, 9,  sqrt)
```

运行结果:

```
8.0
```
## map()函数

`map()`是 Python **内置**的高阶函数，它接收一个函数`f`和一个 `list`，并通过把函数`f`**依次作用**在`list`的每个元素上，得到一个新的`list`并返回这个`list`。

例如，对于`list [1, 2, 3, 4, 5, 6, 7, 8, 9]`

如果希望把list的每个元素都作平方，就可以用map()函数：

因此，我们只需要传入函数`f(x)=x*x`，就可以利用map()函数完成这个计算：

```python
def f(x):
    return x*x
print map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
```

输出结果：

```
[1, 4, 9, 10, 25, 36, 49, 64, 81]
```

知识点； 注意：map()函数不改变原有的 list，而是**返回一个新的 list**。

利用`map()`函数，可以把一个 list 转换为另一个 list，只需要传入转换函数。

由于list包含的元素可以是**任何类型**，因此，map() 不仅仅可以处理只包含数值的 list，事实上它可以处理包含任意类型的 list，**只要传入的函数f可以处理这种数据类型**。

### 编程任务
>假设用户输入的英文名字不规范，没有按照首字母大写，后续字母小写的规则，请利用`map()`函数.

把一个list（包含若干不规范的英文名字）变成一个包含规范英文名字的list：

输入：`['adam', 'LISA', 'barT']`
输出：`['Adam', 'Lisa', 'Bart']`

实现代码:

```python
def format_name(s):
    return s[0].upper() + s[1:].lower()
print map(format_name, ['adam', 'LISA', 'barT'])
```

运行结果:

```
['Adam', 'Lisa', 'Bart']
```
## reduce()函数

`reduce()`函数也是Python**内置的**一个高阶函数。reduce()函数接收的参数和 map()类似，一个函数`f`，一个`list`，但`知识点`：**行为和 `map()`不同，reduce()传入的函数 f 必须接收两个参数，reduce()对list的每个元素反复调用函数f，并返回最终结果值。**

例如，编写一个`f`函数，接收`x`和`y`，返回`x和y的和`：

```
def f(x, y):
    return x + y
```

调用 reduce(f, [1, 3, 5, 7, 9])时，reduce函数将做如下计算：

```
先计算头两个元素：f(1, 3)，结果为4；
再把结果和第3个元素计算：f(4, 5)，结果为9；
再把结果和第4个元素计算：f(9, 7)，结果为16；
再把结果和第5个元素计算：f(16, 9)，结果为25；
由于没有更多的元素了，计算结束，返回结果25。
```

上述计算实际上是对 list 的所有元素求和。虽然Python内置了求和函数`sum()`，但是，利用reduce()求和也很简单。

`知识点`：reduce()还可以接收第3个可选参数，作为计算的初始值。如果把初始值设为100，计算：

```
reduce(f, [1, 3, 5, 7, 9], 100)
```

结果将变为125，因为第一轮计算是：

- 计算初始值和第一个元素：f(100, 1)，结果为101。

### 编程任务
>Python内置了求和函数sum()，但没有求积的函数，请利用recude()来求积：

```
输入：[2, 4, 5, 7, 12]
输出：2*4*5*7*12的结果
```

实现代码:

```python
def prod(x, y):
    return x*y

print reduce(prod, [2, 4, 5, 7, 12])
```

运行结果：

```
3360
```

## filter()函数

`filter()`函数是 Python 内置的另一个有用的高阶函数，`filter()`函数接收一个函数 `f` 和一个`list`，这个函数 `f` 的作用是对每个元素进行判断，返回 `True`或 `False`，`filter()` 知识点：**根据判断结果自动过滤掉不符合条件的元素，返回由符合条件元素组成的新list。**

例如，要从一个`list [1, 4, 6, 7, 9, 12, 17]`
中删除偶数，保留奇数，首先，要编写一个判断奇数的函数：

```python
def is_odd(x):
    return x % 2 == 1
```
然后，利用`filter()`过滤掉偶数：

```python
filter(is_odd, [1, 4, 6, 7, 9, 12, 17])
结果：[1, 7, 9, 17]
```

利用`filter()`，可以完成很多有用的功能，例如，删除 `None` 或者`空字符串`：

```python
def is_not_empty(s):
    return s and len(s.strip()) > 0
filter(is_not_empty, ['test', None, '', 'str', '  ', 'END'])
```

结果：

```
['test', 'str', 'END']
```

知识点: 

注意: `s.strip(rm)` 删除 `s` 字符串中`开头、结尾处`的 `rm` 序列的字符。

当`rm`为空时，默认删除空白符（包括'\n', '\r', '\t', ' ')，如下：

```
a = '     123'
a.strip()
```

结果： '123'

```
a='\t\t123\r\n'
a.strip()
结果：'123'
```

### 编程任务
>请利用`filter()`过滤出1~100中平方根是整数的数，即结果应该是：

```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
实现代码:

```python
import math

def is_sqr(x):
    return math.sqrt(x)%1==0

print filter(is_sqr, range(1, 101))
```
注: `sqrt`函数是开根号的函数，返回值为`浮点数`。在`math`包中。

- `math.sqrt(4)` 结果是 `2.0`

运行结果:

```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

## 自定义排序函数

Python内置的 sorted()函数可对list进行排序：

```python
>>>sorted([36, 5, 12, 9, 21])
```
运行结果：

```
[5, 9, 12, 21, 36]
```
`知识点`: 但 `sorted()`也是一个高阶函数，它可以**接收一个比较函数**来实现**自定义排序**，比较函数的定义是，传入两个待比较的元素 `x`, `y`，如果 `x `应该排在`y`的前面，返回`-1`，如果`x` 应该排在 `y` 的后面，返回 `1`。如果 `x` 和 `y` 相等，返回 `0`。

因此，如果我们要实现倒序排序，只需要编写一个`reversed_cmp`函数：

```python
def reversed_cmp(x, y):
    if x > y:
        return -1
    if x < y:
        return 1
    return 0
```

解析上面函数:

- 当`x>y`时，return`-1`.向`sorted`表明`x`应排在`y`的前面。也就是越大的排越靠前(俗称逆序)
- 其他情况同理可得

这样，调用 `sorted()` 并传入 `reversed_cmp`就可以实现倒序排序：

```python
>>> sorted([36, 5, 12, 9, 21], reversed_cmp)
[36, 21, 12, 9, 5]
```
知识点：sorted()也可以对字符串进行排序，**字符串默认按照ASCII大小来比较：**

```python
>>> sorted(['bob', 'about', 'Zoo', 'Credit'])
['Credit', 'Zoo', 'about', 'bob']
```
'Zoo'排在'about'之前是因为'Z'的ASCII码比'a'小。

### 编程任务

对字符串排序时，有时候忽略大小写排序更符合习惯。请利用`sorted()`高阶函数，实现忽略大小写排序的算法。

```
输入：['bob', 'about', 'Zoo', 'Credit']
输出：['about', 'bob', 'Credit', 'Zoo']
```

实现代码:

```python
def cmp_ignore_case(s1, s2):
    return cmp(s1.lower(), s2.lower())

print sorted(['bob', 'about', 'Zoo', 'Credit'], cmp_ignore_case)
```

运行结果：

```
['about', 'bob', 'Credit', 'Zoo']
```
## 返回函数

Python的函数不但可以返回`int、str、list、dict`等数据类型，还可以返回函数！

解析：因为前面我们讲过Python中的函数为高阶函数。也就是可以把函数作为一个参数使用。既然是一个参数(变量)，那么可以被用来返回也不奇怪了。


例如，定义一个函数 `f()`，我们让它返回一个函数 `g`，可以这样写：

```python
def f():
    print 'call f()...'
    # 定义函数g:
    def g():
        print 'call g()...'
    # 返回函数g:
    return g
```

仔细观察上面的函数定义，我们在函数`f`内部又定义了一个函数 `g`。由于函数 `g`也是一个对象，函数名 `g` 就是一个指向函数 `g` 的变量，所以，最外层函数 `f` 可以返回变量 `g`，也就是函数 `g` 本身。

调用函数 f，我们会得到 f 返回的一个函数：

```python
>>> x = f()   # 调用f()
call f()...
>>> x   # 变量x是f()返回的函数：
<function g at 0x1037bf320>
>>> x()   # x指向函数，因此可以调用
call g()...   # 调用x()就是执行g()函数定义的代码
```

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/h8Ik6FD4gL.png?imageslim)

知识点: 图中`x = f()`对于`f()`进行调用的同时将返回值存入了`x`中。
因此`x`存放上了f函数的返回值: `g函数`。因为`x`指向一个函数对象。所以我们可以调用该函数对象。

请注意区分返回函数和返回值：

```python
def myabs():
    return abs   # 返回函数
def myabs2(x):
    return abs(x)   # 返回函数调用的结果，返回值是一个数值
```

知识点: 返回函数可以把一些**计算延迟执行**。例如，如果定义一个普通的求和函数：

```python
def calc_sum(lst):
    return sum(lst)
```

调用calc_sum()函数时，将立刻计算并得到结果：

```
>>> calc_sum([1, 2, 3, 4])
10
```

但是，如果返回一个函数，就可以`延迟计算`：

```python
def calc_sum(lst):
    def lazy_sum():
        return sum(lst)
    return lazy_sum
```

调用calc_sum()并没有计算出结果，而是返回函数:

```
>>> f = calc_sum([1, 2, 3, 4])
>>> f
<function lazy_sum at 0x1037bfaa0>
```

对返回的函数进行调用时，才计算出结果:

```
>>> f()
10
```

由于可以返回函数，我们在后续代码里就可以决定到底要不要调用该函数。

### 编程任务
>请编写一个函数calc_prod(lst)，它接收一个list，返回一个函数，返回函数可以计算参数的乘积。

实现代码:

```python
def calc_prod(lst):
    def prod():
        return reduce((lambda x, y : x * y),lst)
    return prod

f = calc_prod([1, 2, 3, 4])
print f()
```

解析: `reduce((lambda x, y : x * y),lst)`

reduce为一个高阶函数，传入两个参数。

- 参数一为`(lambda x, y : x * y)`这是一个`lambda`函数。表示传入参数`x`,`y`。然后进行`x * y`运算。
- 参数二: 一个可迭代对象。

过程:

- `1 * 2`得到结果 `2`
- `2 * 3`得到结果 `6`
- `6 * 4`得到结果 `24`  


运行结果：

```
24
```
## 闭包

在函数内部定义的函数和外部定义的函数是一样的，**只是他们无法被外部访问：**

```python
def g():
    print 'g()...'

def f():
    print 'f()...'
    return g
```

知识点；将 `g` 的定义移入函数 `f` 内部，防止其他代码调用 `g`：

```python
def f():
    print 'f()...'
    def g():
        print 'g()...'
    return g
```

但是，考察上一小节定义的 `calc_sum` 函数：

```python
def calc_sum(lst):
    def lazy_sum():
        return sum(lst)
    return lazy_sum
```

`知识点` 注意: 发现没法把 `lazy_sum` 移到 `calc_sum` 的外部，因为它引用了 `calc_sum` 的参数 `lst`。也就是在`calc_sum`函数外部定义的`lazy_sum`函数，就没办法接收传入`calc_sum`函数的参数。

`知识点:python闭包的定义`

像这种内层函数引用了外层函数的变量（参数也算变量），然后返回内层函数本身的情况，称为**闭包（Closure）**。

闭包的特点是**返回的函数还引用了外层函数的局部变量**

- 如被返回的`lazy_sum` 函数还引用了传入`calc_sum`函数的变量(局部)

所以，要`知识点:` 正确使用闭包，就要确保引用的局部变量在函数返回后不能变。举例如下：

希望一次返回3个函数，分别计算1x1,2x2,3x3:

```python
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        fs.append(f)
    return fs

f1, f2, f3 = count()

print f1(), f2(), f3()
```

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/jamj54aBiF.png?imageslim)

你可能认为调用`f1()`，`f2()`和`f3()`结果应该是`1，4，9`，但实际结果全部都是 `9`。

`知识点:` 原因就是当count()函数返回了3个函数时，这3个函数所引用的变量 i 的值已经变成了3。由于f1、f2、f3并没有被调用，所以，此时他们并未计算 `i*i`，当 `f1` 被调用时：

`个人解析：`  `f1, f2, f3 = count()`调用`count()`函数, 进入`count()`函数内部。

- `fs = []`创建一个空的集合
- `for i in range(1, 4):` 循环执行三次代码块

```
for i in range(1, 4):
        def f():
             return i*i
        fs.append(f)
```

- 第一次执行时，定义一个`f()`函数，该函数此时被直接调用时的返回值为 `i*i` ;然后将f函数作为一个元素加入空列表`fs`中。验证代码如下

```python
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        print "我现在的返回值：%d",f()
        fs.append(f)
    return fs

f1, f2, f3 = count()

print f1(), f2(), f3()
```

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/FHdEl98B64.png?imageslim)

- 然后继续执行。直到把三个函数都当做元素存入`fs`。至此`f1, f2, f3 = count()`运行完毕
- `print f1(), f2(), f3()` 调用这三个函数。此时`f()`被调用。执行`i*i`,但是现在的`i` 值为3.所以三个值都为9.


```python
>>> f1()
9     # 因为f1现在才计算i*i，但现在i的值已经变为3
```

**因此，返回函数不要引用任何循环变量，或者后续会发生变化的变量。**

### 编程任务(天涯)
>返回闭包不能引用循环变量，请改写count()函数，让它正确返回能计算`1x1、2x2、3x3`的函数。

实现代码:

```python
def count():
    fs = []
    for i in range(1, 4):
        def f(i):
            return  lambda : i*i
        fs.append(f(i))
    return fs

f1, f2, f3 = count()
print f1(), f2(), f3()
```

解析：往`fs`中添加的元素不在是`f函数`本身。此时添加的对象是`f函数的调用`也就是他被调用后的返回值`lambda : i*i` 一个`lambda`函数对象。

`lambda : i*i`时它使用的变量是当次循环传入的i值。而不是循环变量`i`

解析二：

考察下面的函数 f:

```python
def f(j):
    def g():
        return j*j
    return g
```
它可以正确地返回一个闭包`g`，`g`所引用的变量`j`不是循环变量，因此将正常执行。

使用下一个函数来将循环变量在单词循环之时持久化。

参考代码:

```python
def count():
    fs = []
    for i in range(1, 4):
        def f(j):
            def g():
                return j*j
            return g
        r = f(i)
        fs.append(r)
    return fs
f1, f2, f3 = count()
print f1(), f2(), f3()
```

运行结果：

```
1 4 9
```

附加解法:

```python
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        print "我现在的返回值：%d",f()
        fs.append(f())
    return fs

f1, f2, f3 = count()

print f1, f2, f3
```
## 匿名函数

高阶函数可以接收函数做参数，有些时候，我们不需要显式地定义函数，直接传入匿名函数更方便。

在Python中，对匿名函数提供了有限支持。还是以`map()`函数为例，计算 `f(x)=x的平方` 时，除了定义一个`f(x)`的函数外，还可以直接传入`匿名函数`：

```python
>>> map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9])
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```
通过对比可以看出，匿名函数 `lambda x: x * x `实际上就是：

```python
def f(x):
    return x * x
```

关键字lambda 表示匿名函数，**冒号前面的 x 表示函数参数**。

`知识点:` 匿名函数有个限制，**就是只能有一个表达式，不写return，返回值就是该表达式的结果。**

使用匿名函数，可以不必定义函数名，直接创建一个函数对象，很多时候可以简化代码：

```python
>>> sorted([1, 3, 9, 5, 0], lambda x,y: -cmp(x,y))
[9, 5, 3, 1, 0]
```
注：`cmp(x,y)` 函数用于比较2个对象，如果 `x < y `返回 `-1`, 如果 `x == y` 返回 0, 如果 `x > y` 返回 1。

前面我们知道排序函数。是接收到return`-1`.向`sorted`表明`x`应排在`y`的前面。也就是小的`x`排前面,那么此时是正序排列。而`-cmp(x,y)`则是逆序排列。

返回函数的时候，也可以返回匿名函数：

```python
>>> myabs = lambda x: -x if x < 0 else x 
>>> myabs(-1)
1
>>> myabs(1)
1
```

解析:

匿名函数本质上就是一个函数，它所抽象出来的东西是一组运算。
Python lambda总共以下2种写法，一种是不含`if…else…`的，一种是包含`if…else…`的：

```
lambda <args>: <return-expression>
lambda <args>: <return-expression> if <cond-expression> else <return-expression>
```

更多学习资源:

http://locatino.github.io/2015/08/03/playing-python-lambda/

如果想要在匿名函数中做一些除了return-expression，其他事情（比如说print()）,应该怎么写？
确实不太好写，不过我还是想出了一个非常投机取巧的办法：

```python
lambda x: True if x % 2 == 0 and print(x) == None else x")
```
上面这个函数不仅返回了x的值，并且还打印了x.
这里我把需要执行的语句(print())转换成了逻辑表达式，而且是一个永远为真的表达式，它一定会执行，并且对业务的逻辑判断没有影响。
前提是你必须准确的知道需要执行的语句的返回值，才能写出永远为真的表达式。

and语句的短路：所以一定要保证前面x%2 == 0为真。此时`if x % 2 == 0 and print(x)`
返回`print(x)`

### 编程任务
>利用匿名函数简化以下代码：

```python
def is_not_empty(s):
    return s and len(s.strip()) > 0
filter(is_not_empty, ['test', None, '', 'str', '  ', 'END'])
```

实现代码:

```python
print filter(lambda s:s and len(s.strip()) > 0, ['test', None, '', 'str', '  ', 'END'])
```

既要满足s非空，又要满足s不是结束字符等。

注意: `s.strip(rm)` 删除 `s` 字符串中`开头、结尾处`的 `rm` 序列的字符。

当`rm`为空时，默认删除空白符（包括'\n', '\r', '\t', ' ')

运行结果：

```
['test', 'str', 'END']
```
## Python中的装饰器
![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/1B7l8FLjij.png?imageslim)

在不改变原函数的情况下，想在运行时动态的增加新功能。可以极大地简化代码，避免每个函数编写重复性代码。

示例:

- 希望对下列函数调用增加log功能，打印出函数调用

```python
def f1(x):
    return x*2
def f2():
    return x*x
def f3():
    return x*x*x
```

方法一: 直接修改原函数

```python
def f1(x):
    print 'call f1()'
    return x*2
def f2():
    print 'call f2()'
    return x*x
def f3():
    print 'call f3()'
    return x*x*x
```

高阶函数：

- 可以接收函数作为参数
- 可以返回函数
- 是否可以接收一个函数，对其包装，然后返回一个新函数。

方法二: 通过高阶函数返回新函数

```python
def f1(x):
    return x*2
def new_fn(f):
    def fn(x):
        print 'call' + f.__name__ + '()'
        return f(x)
    return fn
```

代码解析：我们可以定义一个`new_fn`这样一个函数。接收`f`参数。
返回一个`fn新函数` 

- 在这个新函数内部首先我们用print语句打印出了一行日志。
紧接着我们对原函数进行调用。返回原函数的结果。

至此我们就得到了一个新的函数。它即包含了原函数的调用（也就是返回原函数调用后的值，又有一行日志来增强原函数的功能。

这里的`new_fn(f)`这个高阶函数就是装饰器函数：

知识点： 调用装饰器函数:

```python
g1 = new_fn(f1)
print g1(5)
```
向`new_fn`传入`f1`，然后会

- 先定义一个`fn(x)`函数。
- 进入`fn(x)`函数内部：执行第一行打印log，然后如果有对于`fn(x)`的调用会返回传入的`f`函数并为其传入参数`x`.

但是很明显：现在只是定义了这个函数`fn(x)`,并没有进行调用。

- 所以此时`g1 = new_fn(f1)`的执行结果便是`new_fn`的返回值。返回`fn`
对象，并被存入了`g1`变量中。此时对于`g1`的调用就是对于`fn`的调用。

`print g1(5)`实际就是调用了`fn`函数。

- 即打印了日志
- 得到了原函数的返回值`return f(x)`

方法2：

```python
f1 = new_fn(f1)
print f1(5)
```

将`f1`作为参数传入的`new_fn`的返回值 `fn` 保存回`f1`本身
因为函数名本身也是变量。所以我们就用这种方法彻底的隐藏了`f1`
的原始定义函数。这时候f1就是装饰以后的函数。

注： `_name_` 是函数的一个属性，取到函数名。


Python内置的`@`语法就是为了简化装饰器的调用。

```
@new_fn
def f1(x):
    return x*2
```
![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/Jkbm893lC7.png?imageslim)

**装饰器的作用**

可以极大地简化代码，避免每个函数编写重复性代码

- 打印日志`@log`
- 检测性能`@performance`
- 数据库事务`@transaction`
- URL路由`@post('/register')`

`@post('/register')`让这个函数来处理指定的url。

## 编写无参数decorator

知识点：Python的 `decorator` 本质上就是一个高阶函数，它**接收一个函数作为参数，然后，返回一个新函数。**

使用 `decorator` 用Python提供的 `@` 语法，这样可以避免手动编写 `f = decorate(f)` 这样的代码。

考察一个`@log`的定义：

```python
def log(f):
    def fn(x):
        print 'call ' + f.__name__ + '()...'
        return f(x)
    return fn
```

对于阶乘函数，@log工作得很好：

```python
@log
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))
print factorial(10)
```

结果：

```
call factorial()...
3628800
```

但是，对于参数不是一个的函数，调用将报错：

```python
@log
def add(x, y):
    return x + y
print add(1, 2)
```
结果：

```
Traceback (most recent call last):
  File "test.py", line 15, in <module>
    print add(1,2)
TypeError: fn() takes exactly 1 argument (2 given)
```


因为 `add()` 函数需要传入两个参数，但是`@log`写死了只含一个参数的返回函数。

要让 `@log` 自适应任何参数定义的函数，可以利用Python的 `*args` 和 `**kw`，保证任意个数的参数总是能正常调用：

```python
def log(f):
    def fn(*args, **kw):
        print 'call ' + f.__name__ + '()...'
        return f(*args, **kw)
    return fn
```

现在，对于任意函数，`@log` 都能正常工作。

注：

- `*args`表示任何多个无名参数，它是一个`tuple`
- `**kw`表示关键字参数，它是一个`dict`。
- 并且同时使用`*args和**kwargs`时，必须`*args`参数列要在`**kw`前

参考博客：
- http://blog.csdn.net/feisan/article/details/1729905
- https://n3xtchen.github.io/n3xtchen/python/2014/08/08/python-args-and-kwargs

Python里，`带*的参数`就是用来接受可变数量参数的。

```python
def funcD(a, b, *c):
  print a
  print b
  print "length of c is: %d " % len(c)
  print c
```
调用`funcD(1, 2, 3, 4, 5, 6)`结果是

```
1
2
length of c is: 4
(3, 4, 5, 6)
```
如果一个函数定义中的最后一个形参有 `**`前缀,所有正常形参之外的其他的`关键字参数`都将被放置在一个字典中传递给函数，比如：

```python
def funcF(a, **b):
  print a
  for x in b:
    print x + ": " + str(b[x])
```

调用`funcF(100, c='你好', b=200)`，执行结果

```
100
c: 你好
b: 200
```

大家可以看到，`b`是一个`dict`对象实例，它接受了关键字参数`b`和`c`。

### 应用

使用 Mysql Python 库时候,经常看到这个样子的代码，db_conf 一般都从配置文件读取，这时优雅的不定字典参数就派上用途了！

```python
import mysql.connector  

db_conf = {
	user='xx',
	password='yy', 
	host='xxx.xxx.xxx.xxx',
	database='zz'
}

cnx = mysql.connector.connect(
	user=db_conf['user'],
	password=db_conf['password'], 
	host=db_conf['host'],
	database=db_conf['database']
	)
```

修改版：

```python
import mysql.connector  

db_conf = {
	user='xx',
	password='yy', 
	host='xxx.xxx.xxx.xxx',
	database='zz'
}

cnx = mysql.connector.connect(**db_conf)
...
```

### 编程任务(天涯)

>请编写一个`@performance`，它可以打印出函数调用的时间。

实现代码:

```python
import time

def performance(f):
    def log_time(x):
        t1= time.time()
        res = f(x)
        t2=time.time()
        print 'call %s() in %fs' % (f.__name__, (t2 - t1))
        return res
    return log_time

@performance
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))

print factorial(10)
```

解析：

- `performance(f)`是一个高阶函数，传入一个参数：函数对象,返回包装后的新函数。
- `log_time(x)`是被高阶函数包裹的新函数。它复杂把旧函数的参数作为自己的参数。
在自己内部执行想要额外添加的功能。然后调用原函数，将原函数调用后的返回值作为自己的返回值。

`time`模块(参考time模块内容)

运行结果：

```
call factorial() in 0.004899s
3628800
```

## 编写带参数decorator

考察上一节的 `@log` 装饰器：

```python
def log(f):
    def fn(x):
        print 'call ' + f.__name__ + '()...'
        return f(x)
    return fn
```

发现对于被装饰的函数，`log`打印的语句是不能变的（除了函数名）。


如果有的函数非常重要，希望打印出`'[INFO] call xxx()...'`，有的函数不太重要，希望打印出`'[DEBUG] call xxx()...'`，这时，`log`函数本身就需要传入`'INFO'`或`'DEBUG'`这样的参数，类似这样：

```python
@log('DEBUG')
def my_func():
    pass
```

把上面的定义翻译成高阶函数的调用，就是：

```
my_func = log('DEBUG')(my_func)
```

解：`log('DEBUG')(my_func)`装饰器函数`log('DEBUG')'`被调用传入`my_func`原函数对象

上面的语句看上去还是比较绕，再展开一下：

```
log_decorator = log('DEBUG')
my_func = log_decorator(my_func)
```
也就是装饰器函数本身是`log('DEBUG')`,然后为该函数调用时传入参数`my_func`

上面的语句又相当于：

```
log_decorator = log('DEBUG')
@log_decorator
def my_func():
    pass
```

知识点：所以，带参数的`log`函数首先返回一个`decorator`函数，再让这个d`ecorator`函数接收`my_func`并返回新函数：

```python
def log(prefix):
    def log_decorator(f):
        def wrapper(*args, **kw):
            print '[%s] %s()...' % (prefix, f.__name__)
            return f(*args, **kw)
        return wrapper
    return log_decorator

@log('DEBUG')
def test():
    pass
print test()
```
执行结果：

```
[DEBUG] test()...
None
```

与上一节无参数做比较:

```python
def log(f):
    def fn(x):
        print 'call ' + f.__name__ + '()...'
        return f(x)
    return fn

```

可以看出它在log(f)的上层又多加了一层函数外壳。使得
带参数的log函数首先返回一个decorator函数。

知识点：无参数装饰器为两层结构。有参数装饰器为三层结构

对于这种`3层嵌套`的`decorator`定义，你可以先把它拆开：



```python
# 标准decorator:
def log_decorator(f):
    def wrapper(*args, **kw):
        print '[%s] %s()...' % (prefix, f.__name__)
        return f(*args, **kw)
    return wrapper

# 返回decorator:
def log(prefix):
    return log_decorator(f)

```

拆开以后会发现，调用会失败，因为在3层嵌套的`decorator`定义中，最内层的`wrapper`引用了最外层的参数`prefix`，所以，**把一个闭包拆成普通的函数调用会比较困难。**不支持闭包的编程语言要实现同样的功能就需要更多的代码。

那么我们如何拆开才能保证正确呢？

```python
未完待续
```

### 编程任务(天涯)
上一节的`@performance`只能打印秒，请给 `@performace`增加一个参数，允许传入`'s'`或`'ms'`：

```python
@performance('ms')
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))
```

实现代码(天涯):

```python
import time

def performance(unit):
    def perf_decorator(f):
        def wrapper(*args, **kw):
            t1 = time.time()
            r = f(*args, **kw)
            t2 = time.time()
            t = (t2 - t1)*1000 if unit =='ms' else (t2 - t1)
            print 'call %s() in %f %s'%(f.__name__, t, unit)
            return r
        return wrapper
    return perf_decorator

@performance('ms')  
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))

print factorial(10)
```
- 最外层输入：参数`unit `，返回：接收了参数的装饰器函数对象。
- 次外层输入：参数`f` 函数对象。返回: 被包装过的函数对象`wrapper`
- 最内层输入：参数为`*args, **kw`。进行额外的处理加返回：返回`f`函数调用的返回值。

人肉运行：

```
perf_decorator = performance('ms')
factorial = perf_decorator(factorial(10))
factorial = wrapper
factorial(10) = wrapper(10)
# 然后执行 print 并返回 f(*args, **kw)的值
```

运行结果：

```
call factorial() in 6.043911 ms
3628800
```

## 完善decorator

`@decorator`可以动态实现函数功能的增加，但是，经过`@decorator`“改造”后的函数，和原函数相比，除了功能多一点外，有没有其它不同的地方？

在没有decorator的情况下，打印函数名：

```python
def f1(x):
    pass
print f1.__name__
```

输出： `f1`


有decorator的情况下，再打印函数名：

```python
def log(f):
    def wrapper(*args, **kw):
        print 'call...'
        return f(*args, **kw)
    return wrapper
@log
def f2(x):
    pass
print f2.__name__
```

输出： `wrapper`

可见，由于`decorator`返回的新函数函数名已经不是`'f2'`，而是`@log`内部定义的`'wrapper'`。这对于那些依赖函数名的代码就会失效。`decorator`还改变了函数的`__doc__`等其它属性。`知识点:` 如果要让调用者看不出一个函数经过了`@decorator`的“改造”，**就需要把原函数的一些属性复制到新函数中：**

```python
def log(f):
    def wrapper(*args, **kw):
        print 'call...'
        return f(*args, **kw)
    wrapper.__name__ = f.__name__
    wrapper.__doc__ = f.__doc__
    return wrapper
```

这样写`decorator`很不方便，因为我们也很难把原函数的所有必要属性都一个一个复制到新函数上，所以Python内置的`functools`可以用来自动化完成这个“复制”的任务：

```python
import functools
def log(f):
    @functools.wraps(f)
    def wrapper(*args, **kw):
        print 'call...'
        return f(*args, **kw)
    return wrapper
```

最后需要指出，由于我们把原函数签名改成了`(*args, **kw)`，因此，**无法获得原函数的原始参数信息。**即便我们采用固定参数来装饰只有一个参数的函数：

```python
def log(f):
    @functools.wraps(f)
    def wrapper(x):
        print 'call...'
        return f(x)
    return wrapper
```

也可能改变原函数的参数名，因为新函数的参数名始终是 `'x'`，原函数定义的参数名不一定叫 `'x'`。

### 编程任务
请思考带参数的`@decorator`，`@functools.wraps`应该放置在哪：

```python
def performance(unit):
    def perf_decorator(f):
        def wrapper(*args, **kw):
            ???
        return wrapper
    return perf_decorator
```

实现代码:

```python
import time, functools

def performance(unit):
    def perf_decorator(f):
        @functools.wraps(f)
        def wrapper(*args,**kv):
            t0 = time.time()
            r = f(*args,**kv)
            t1 = time.time()
            t = (t1 - t0) if unit =='s' else (t1 - t0) * 1000
            print 'call %s() in %s %s' % (f.__name__, t, unit)
            return r
        return wrapper
    
    return perf_decorator

@performance('ms')
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))

print factorial.__name__
```
tips:

- 最外层输入：参数`unit `，返回：接收了参数的装饰器函数对象。
- 次外层输入：参数`f` 函数对象。返回: 被包装过的函数对象`wrapper`
- 最内层输入：参数为`*args, **kw`。进行额外的处理加返回：返回`f`函数调用的返回值。

搞清每一层的输入输出就可以成功写出来

运行结果：

```
factorial
```

## 偏函数

当一个函数有很多参数时，调用者就需要提供多个参数。如果减少参数个数，就可以简化调用者的负担。

比如，`int()`函数可以把字符串转换为整数，当仅传入字符串时，`int()`函数默认按`十进制`转换：

```python
>>> int('12345')
12345
```

但`int()`函数还提供额外的`base`参数，默认值为10。如果传入base参数，就可以做`N`进制的转换：

```python
>>> int('12345', base=8)
5349
>>> int('12345', 16)
74565
```

`知识点`：假设要转换大量的二进制字符串，每次都传入`int(x, base=2)`非常麻烦，于是，我们想到，可以定义一个`int2()`的函数，默认把`base=2`传进去：

```python
def int2(x, base=2):
    return int(x, base)
```

这样，我们转换二进制就非常方便了：

```python
>>> int2('1000000')
64
>>> int2('1010101')
85
```

`functools.partial`就是帮助我们创建一个**偏函数**的，不需要我们自己定义`int2()`，可以直接使用下面的代码创建一个新的函数`int2`：

```
>>> import functools
>>> int2 = functools.partial(int, base=2)
>>> int2('1000000')
64
>>> int2('1010101')
85
```

所以，`functools.partial`可以把一个参数多的函数变成一个参数少的新函数，少的参数需要在创建时指定**默认值**，这样，新函数调用的难度就降低了。

`知识点`：偏函数是为一个多参数函数设定参数的默认值，可以降低函数调用的难度。

### 编程任务
>在第7节中，我们在`sorted`这个高阶函数中传入自定义排序函数就可以实现忽略大小写排序。请用`functools.partial`把这个复杂调用变成一个简单的函数：

```
sorted_ignore_case(iterable)
```

实现代码:

```python
import functools

sorted_ignore_case = functools.partial(sorted,key=str.lower)

print sorted_ignore_case(['bob', 'about', 'Zoo', 'Credit'])
```

运行结果：

```
['about', 'bob', 'Credit', 'Zoo']
```

`functools.partial` 传入两个参数，一个是原函数。一个是原函数包含的默认参数。

官方文档对于`sorted`的说明：

key specifies a function of one argument that is used to extract a comparison key from each list `element:key=str.lower`. The default value isNone.

课外知识：

`sort` 与 `sorted` 区别：

- `sort` 是应用在 `list` 上的方法，`sorted` 可以对`所有可迭代的对象`进行排序操作。
- `list` 的 `sort` 方法返回的是对已经存在的列表进行操作，而内建函数 `sorted `方法返回的是一个新的 `list`，而不是在原来的基础上进行的操作。

`sorted` 语法：

`sorted(iterable[, cmp[, key[, reverse]]])`

参数说明：

- iterable -- 可迭代对象。
- cmp -- 比较的函数，这个具有两个参数，参数的值都是从可迭代对象中取出，此函数必须遵守的规则为，大于则返回1，小于则返回-1，等于则返回0。
- key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
- reverse -- 排序规则，reverse = True 降序 ， reverse = False 升序（默认）。

# Python的模块
如何编写和导入模块，以及如何安装并使用第三方模块

## 模块和包。 

概念：模块和包。

当我们的代码越来越多的时候:

- 将所有代码放入一个py文件:难以维护

我们如果将代码分拆放入多个py文件,好处:

	- 同一个名字变量互不影响

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/jgfCd55HCf.png?imageslim)

存在于两个文件中的同名变量，函数互不影响。

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/A78d86Bf66.png?imageslim)

这时我们称文件`a`为`模块a`,`b`为`模块b`.

知识点： 模块的名字就是python文件的名字。

引用其他模块方法：

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/EidCflgfg6.png?imageslim)

当模块变多之后他们很容易重名。

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/98jd95BjkJ.png?imageslim)

路人甲与路人乙都写了`util.py`,产生了冲突。

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/8LDiD7EJHL.png?imageslim)

同名的模块放入不同的包中。就可以了。
此时即使有同名的模块，但是他们的完整名字变成了`p1.util` 和 `p2.util`
，就不冲突了。

- 引用完整模块

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/4dcEACCI50.png?imageslim)

全部都要写完整名称。`p1.util` `p1.util.f(2,10)`

- 包就是文件夹
- 模块就是`xxx.py`文件
- 包可以有多级

区分包和普通目录

包下面必须有一个`__init__.py`这样一个特殊的文件。
每一个包的**每一层目录**都要有这个文件。

即使这个文件是空文件，也必须让这个文件存在。这样Python才能识别这是一个包。

## 导入模块

要使用一个模块，我们必须首先导入该模块。Python使用`import`语句导入一个模块。例如，导入**系统自带**的模块 `math`：

```python
import math
```

你可以认为`math`就是一个指向已导入模块的变量，通过该变量，我们可以访问math模块中所定义的所有公开的函数、变量和类：

```python
>>> math.pow(2, 0.5) # pow是函数
1.4142135623730951

>>> math.pi # pi是变量
3.141592653589793
```

注意：`pow() `方法返回 `x的y次方` 的值。

内置的 `pow()` 方法

```
pow(x, y[, z])
```
函数是计算x的y次方，如果z在存在，则再对结果进行取模，其结果等效于`pow(x,y) %z`
但是会更有效率一点。

如果我们只希望导入用到的`math`模块的某几个函数，而不是所有函数，可以用下面的语句：

```
from math import pow, sin, log
```

这样，可以直接引用 `pow`, `sin`, `log` 这3个函数，但`math`的其他函数没有导入进来：

```
>>> pow(2, 10)
1024.0
>>> sin(3.14)
0.0015926529164868282
```
如果遇到名字冲突怎么办？比如`math`模块有一个`log`函数，`logging`模块也有一个`log`函数，如果同时使用，如何解决名字冲突？

如果使用`import`导入模块名，由于**必须通过模块名引用函数名，因此不存在冲突：**

```
import math, logging
print math.log(10)   # 调用的是math的log函数
logging.log(10, 'something')   # 调用的是logging的log函数
```

如果使用 `from...import` 导入 `log` 函数，势必引起冲突。这时，可以给函数起个**“别名”**来避免冲突：

```python
from math import log
from logging import log as logger   # logging的log现在变成了logger
print log(10)   # 调用的是math的log
logger(10, 'import from logging')   # 调用的是logging的log
```

### 编程任务

>Python的`os.path`模块提供了 `isdir()` 和 `isfile()`函数，请导入该模块，并调用函数判断指定的目录和文件是否存在。

注意: 可以在本机上测试是否存在相应的文件夹和文件。

实现代码:

```python
import os
print os.path.isdir(r'C:\Windows')
print os.path.isfile(r'C:\Windows\notepad.exe')
```

运行结果：

```
True
True
```

## 动态导入模块

如果导入的模块不存在，Python解释器会报 `ImportError` 错误：

```python
>>> import something
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named something
```

有的时候，两个不同的模块提供了相同的功能，比如 `StringIO` 和 `cStringIO` 都提供了`StringIO`这个功能。

这是因为Python是动态语言，解释执行，因此Python代码运行速度慢。

如果要提高Python代码的运行速度，最简单的方法是把某些关键函数用 C 语言重写，这样就能大大提高执行速度。

同样的功能，`StringIO` 是纯Python代码编写的，而 `cStringIO` **部分**函数是 C 写的，因此 `cStringIO`运行速度更快。

利用`ImportError`错误，我们经常在Python中**动态**导入模块：

```python
try:
    from cStringIO import StringIO
except ImportError:
    from StringIO import StringIO
```

上述代码先尝试从cStringIO导入，如果失败了（比如cStringIO没有被安装），再尝试从StringIO导入。这样，如果cStringIO模块存在，则我们将获得更快的运行速度，如果cStringIO不存在，则顶多代码运行速度会变慢，但不会影响代码的正常执行。

`try` 的作用是捕获错误，并在捕获到指定错误时执行 `except` 语句。

这里先用一下，更多内容在Python错误与异常处理中讲。

### 编程任务
>利用`import ... as ...，`还可以动态导入不同名称的模块。
Python 2.6/2.7提供了`json` 模块，但Python 2.5以及更早版本没有json模块，不过可以安装一个`simplejson`模块，这两个模块提供的函数签名和功能都一模一样。

试写出导入json 模块的代码，能在Python 2.5/2.6/2.7都正常运行。

实现代码:

```python
try:
    import json
except ImportError:
    import simplejson

print json.dumps({'python':2.7})
```

运行结果：

```

```

注：Python的`Json`模块`序列化`与`反序列化`的过程分别是 `encoding`和 `decoding`

- encoding(编码)：把一个`Python对象编码`转换成`Json`字符串
- decoding(解码)：把`Json`格式字符串解码转换成`Python对象`

对于简单数据类型`string、unicode、int、float、list、tuple、dict`，可以直接处理。

`json.dumps`方法对简单数据类型`encoding`

`知识点`联系对比：

在Python入门中接触的`Unicode`编码中。

- `decode`的作用是将其他编码的字符串转换成`unicode`编码，如`str1.decode('gb2312')`，表示将`gb2312`编码的字符串`str1`转换成`unicode`编码。
- `encode`的作用是将`unicode`编码转换成其他编码的字符串，如`str2.encode(‘gb2312’)`，表示将`unicode`编码的字符串`str2`转换成`gb2312`编码

## 使用__future__

Python的新版本会引入新的功能，但是，实际上这些功能在上一个老版本中就已经存在了。要“试用”某一新的特性，就可以通过导入`__future__`模块的某些功能来实现。

例如，Python 2.7的整数除法运算结果仍是整数：

```
>>> 10 / 3
3
```

python2.7下：

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180104/j3CefF1Lji.png?imageslim)

但是，Python 3.x已经改进了整数的除法运算，`/`除将得到浮点数，`//`除才仍是整数：

```python
>>> 10 / 3
3.3333333333333335
>>> 10 // 3
3
```

要在Python 2.7中引入3.x的除法规则，导入`__future__`的`division`：

```python
>>> from __future__ import division
>>> print 10 / 3
3.3333333333333335
```

当新版本的一个特性与旧版本不兼容时，该特性将会在旧版本中添加到`__future__`中，以便旧的代码能在旧版本中测试新特性。

### 编程任务

>在Python 3.x中，字符串统一为`unicode`，不需要加前缀 `u`，而以字节存储的`str`则必须加前缀 `b`。请利用`__future__`的`unicode_literals`在Python 2.7中编写`unicode`字符串。

实现代码:

```python
from __future__ import unicode_literals

s = 'am I an unicode?'
print isinstance(s, unicode)
```

运行结果：

```
True
```

## 安装第三方模块

虽然内置了许多模块，但是很多有用的第三方包需要我们自己下载。

两种方法安装第三方模块
- easy_install
- pip install(推荐，因为pip内置)

我推荐安装的**Anaconda**也已经内置了`pip`

安装体验。

`pip install web.py`

cmd下进入python命令行就可以导入web.py了

查找第三方模块名字：

https://pypi.python.org/pypi

在这里可以搜索。

# Python面向对象编程
如何创建类和实例，如何定义类的属性和方法。

## 面向对象简介

面向对象编程是一种程序设计范式: 把程序看做不同对象的相互调用。

是对于**现实世界**建立的对象模型。


面向对象编程的基本思想(类和实例):

- `类`：用于定于抽象类型（比如人、汽车、花等抽象的一类事物）
- `实例`：根据类的定义被创建出来的


类的定义：

```python
class Person:
    pass
```
通过类创建具体的实例，通过类名与一个类似于函数调用。

```python
xiaoming = Person()
xiaojun = Person()
xiaohong = Person()
```

比如人的实例有小明、小胡等具体的人，他们有年龄、性别和爱好等不同的属性和方法

**面向对象最重要的思想就是：数据封装**

在类中把数据封装起来。不同的实例它具有相同的数据类型，但是他拥有不同的属性。

## 定义类并创建实例

在Python中，类通过 `class` 关键字定义。以 `Person` 为例，定义一个`Person`类如下：

```python
class Person(object):
    pass
```

按照 Python 的编程习惯，**类名以大写字母开头，紧接着是(object)**，表示该类是从哪个类`继承`下来的。类的继承将在后面的章节讲解，现在我们只需要简单地从object类继承。

有了`Person`类的定义，就可以创建出具体的`xiaoming、xiaohong`等实例。创建实例使用 `类名+()`，类似函数调用的形式创建：

```python
xiaoming = Person()
xiaohong = Person()
```

### 编程任务
>请练习定义Person类，并创建出两个实例，打印实例，再比较两个实例是否相等。


实现代码:

```python
class Person:
    pass

xiaoming = Person()
xiaohong = Person()

print xiaoming
print xiaohong
print xiaoming==xiaohong
```

运行结果：

```
<__main__.Person instance at 0x7f434c37d050>
<__main__.Person instance at 0x7f434c3813f8>
False
```

## 创建实例属性

虽然可以通过`Person`类创建出`xiaoming、xiaohong`等实例，但是这些实例看上除了地址不同外，没有什么其他不同。在现实世界中，区分`xiaoming、xiaohong`要依靠他们各自的`名字`、`性别`、`生日`等属性。

如何让每个实例拥有各自不同的属性？由于Python是动态语言，对每一个实例，都可以直接给他们的属性赋值.

例如，给xiaoming这个实例加上`name、gender和birth`属性：

```python
xiaoming = Person()
xiaoming.name = 'Xiao Ming'
xiaoming.gender = 'Male'
xiaoming.birth = '1990-1-1'
```

给xiaohong加上的属性不一定要和xiaoming相同：

```python
xiaohong = Person()
xiaohong.name = 'Xiao Hong'
xiaohong.school = 'No. 1 High School'
xiaohong.grade = 2
```

实例的属性可以像普通变量一样进行操作：

```python
xiaohong.grade = xiaohong.grade + 1
```

### 编程任务
>请创建包含两个 Person 类的实例的 list，并给两个实例的 name 赋值，然后按照 name 进行排序。

实现代码:

```python
class Person(object):
    pass

p1 = Person()
p1.name = 'Bart'

p2 = Person()
p2.name = 'Adam'

p3 = Person()
p3.name = 'Lisa'

L1 = [p1, p2, p3]
L2 = sorted(L1,key=lambda x:x.name)

print L2[0].name
print L2[1].name
print L2[2].name
```

运行结果：

```
Adam
Bart
Lisa
```
python3下该代码只需要`print`加上括号。也可以正常运行。

## 初始化实例属性

虽然我们可以自由地给一个实例绑定各种属性，但是，现实世界中，一种类型的实例应该拥有相同名字的属性。例如，**Person**类应该在创建的时候就拥有`name`、`gender` 和 `birth` 属性，怎么办？

在定义 `Person` 类时，可以为Person类添加一个特殊的`__init__()`方法被自动调用，我们就能在此为每个实例都统一加上以下属性：

```python
class Person(object):
    def __init__(self, name, gender, birth):
        self.name = name
        self.gender = gender
        self.birth = birth
```

`__init__()` 方法的第一个参数必须是 `self`（**也可以用别的名字，但建议使用习惯用法**），后续参数则可以自由指定，和定义函数没有任何区别。


相应地，创建实例时，就**必须要提供除 self 以外的参数**：

```python
xiaoming = Person('Xiao Ming', 'Male', '1991-1-1')
xiaohong = Person('Xiao Hong', 'Female', '1992-2-2')
```

有了`__init__()`方法，每个`Person`实例在创建时，都会有 `name`、`gender` 和`birth` 这3个属性，并且，被赋予不同的属性值，访问属性使用.操作符：

```python
print xiaoming.name
# 输出 'Xiao Ming'
print xiaohong.birth
# 输出 '1992-2-2'
```

知识点：要特别注意的是，初学者定义`__init__()`方法常常忘记了 `self` 参数：

```python
>>> class Person(object):
...     def __init__(name, gender, birth):
...         pass
... 
>>> xiaoming = Person('Xiao Ming', 'Male', '1990-1-1')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: __init__() takes exactly 3 arguments (4 given)
```

这会导致创建失败或运行不正常，因为第一个参数name被Python解释器传入了实例的引用，从而导致整个方法的调用参数位置全部没有对上。

### 编程任务
>请定义Person类的`__init__`方法，除了接受 `name、gender 和 birth` 外，还可接受任意关键字参数，并把他们都作为属性赋值给实例。


实现代码:

```python
class Person(object):
    def __init__(self, name, gender, birth,**kw):
        self.name = name
        self.gender = gender
        self.birth = birth
        self.__dict__.update(kw)
        # setattr(self, k, v)也可以 

xiaoming = Person('Xiao Ming', 'Male', '1990-1-1', job='Student')

print xiaoming.name
print xiaoming.job
```

运行结果：

```
Xiao Ming
Student
```

`**kw`是一个可变的存入`dict`的变量。

知识点:

- `self.__dict__.update(kw)`

解释器内部会将`**kw`拆分成对应的dict.

`setattr()`方法接受3个参数：`setattr(对象，属性，属性的值)`

`setattr(self,k,v)`相当于`self.k = v`

`kw.iteritems()`历遍字典kw的所有`key`和`value`，分别匹配k，v

我们在运行期定义的属性和类定义时定义的属性都被放在了`__dict__`里。

推荐文章：http://hbprotoss.github.io/posts/python-descriptor.html

## 访问限制

我们可以给一个实例绑定很多属性，如果有些属性不希望被外部访问到怎么办？

Python对属性权限的控制是通过**属性名**来实现的，如果一个属性由`双下划线`开头`(__)`，该属性就无法被外部访问。看例子：

```python
class Person(object):
    def __init__(self, name):
        self.name = name
        self._title = 'Mr'
        self.__job = 'Student'
p = Person('Bob')
print p.name
# => Bob
print p._title
# => Mr
print p.__job
# => Error
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Person' object has no attribute '__job'
```

可见，只有以双下划线开头的`__job`不能直接被外部访问。

知识点： 但是，如果一个属性以`__xxx__`的形式定义，那它又可以被外部访问了，以"__xxx__"定义的属性在Python的类中被称为**特殊属性**，有很多`知识点:`**预定义**的特殊属性可以使用，通常我们不要把普通属性用`__xxx__`定义。

以单下划线开头的属性`_xxx`虽然也可以被外部访问，但是，按照习惯，他们**不应该被外部访问**。

### 编程任务
>请给Person类的`__init__`方法中添加`name`和`score`参数，并把`score`绑定到`__score`属性上，看看外部是否能访问到。

实现代码:

```python
class Person(object):
    def __init__(self, name, score):
        self.name = name
        self.__score = score

p = Person('Bob', 59)

print p.name
try :
    print p.__score
except AttributeError:
    print 'attributeerror'
```

运行结果：

```
Bob
attributeerror
```

## 创建类属性

类是`模板`，而实例则是根据类创建的对象。

`知识点:` 绑定在一个实例上的属性不会影响其他实例，但是，类本身也是一个对象，如果在类上绑定一个属性，则所有实例都可以访问类的属性，并且，所有实例访问的类属性都是同一个！也就是说，实例属性每个实例各自拥有，互相独立，**而类属性有且只有一份。**

定义类属性可以直接在 `class` 中定义：

```python
class Person(object):
    address = 'Earth'
    def __init__(self, name):
        self.name = name
```

因为类属性是直接绑定在类上的，所以，`知识点：` 访问`类属性`不需要`创建实例`，就可以**直接访问**：

```python
print Person.address
# => Earth
```

对一个实例调用类的属性也是可以访问的，所有实例都可以访问到它所属的类的属性：

```python
p1 = Person('Bob')
p2 = Person('Alice')
print p1.address
# => Earth
print p2.address
# => Earth
```

由于Python是动态语言，**类属性也是可以动态添加和修改的：**

```
Person.address = 'China'
print p1.address
# => 'China'
print p2.address
# => 'China'
```

因为**类属性只有一份，所以，当Person类的address改变时，所有实例访问到的类属性都改变了**。

### 编程任务

>请给 `Person` 类添加一个类属性 `count`，每创建一个实例，`count` 属性就加 1，这样就可以统计出一共创建了多少个 Person 的实例。

实现代码:

```python
class Person(object):
    count = 0
    def __init__(self,name):
        self.name=name
        Person.count=Person.count+1

p1 = Person('Bob')
print Person.count

p2 = Person('Alice')
print Person.count

p3 = Person('Tim')
print Person.count
```

运行结果：

```
1
2
3
```

## 类属性和实例属性名字冲突怎么办

修改类属性会导致所有实例访问到的类属性全部都受影响，但是，如果在实例变量上修改类属性会发生什么问题呢？

```python
class Person(object):
    address = 'Earth'
    def __init__(self, name):
        self.name = name

p1 = Person('Bob')
p2 = Person('Alice')

print 'Person.address = ' + Person.address

p1.address = 'China'
print 'p1.address = ' + p1.address

print 'Person.address = ' + Person.address
print 'p2.address = ' + p2.address
```

结果如下：

```
Person.address = Earth
p1.address = China
Person.address = Earth
p2.address = Earth
```

我们发现，在设置了 `p1.address = 'China'` 后，`p1`访问 `address` 确实变成了 `China`，但是，`Person.address`和`p2.address`仍然是`Earth`，怎么回事？

知识点: 原因是 `p1.address = 'China'`并没有改变 `Person` 的 `address`，而是给`p1`这个实例绑定了`实例属性address` ，对p1来说，它有一个**实例属性address（值是'China'）**，而它所属的类Person也有一个类属性address，所以:

- 访问 p1.address 时，优先查找实例属性，返回'China'。
- 访问 p2.address 时，p2没有实例属性address，但是有类属性address，因此返回'Earth'。

知识点：当实例属性和类属性重名时，**实例属性优先级高，它将屏蔽掉对类属性的访问。**

当我们把 `p1` 的 `address` 实例属性删除后，访问 `p1.address` 就又返回类属性的值 `'Earth'`了：

```
del p1.address
print p1.address
# => Earth
```

可见，**千万不要在实例上修改类属性**，它实际上并没有修改类属性，而是给实例绑定了一个实例属性。

### 编程任务

>请把上节的 `Person` 类属性 `count` 改为 `__count`，再试试能否从实例和类访问该属性。

实现代码:

```python
class Person(object):

    __count = 0

    def __init__(self, name):
        self.name = name
        Person.__count += 1
        print Person.__count

p1 = Person('Bob')
p2 = Person('Alice')

try:
    print Person.__count
except AttributeError:
    print 'attributeerror'
```

运行结果：

```
1
2
attributeerror
```

## 定义实例方法

一个实例的`私有属性`就是以`__`开头的属性，无法被外部访问，那这些属性定义有什么用？

虽然私有属性无法从外部访问，但是，从类的内部是可以访问的。除了可以定义实例的属性外，还可以定义**实例的方法**。

实例的方法就是在类中定义的函数，**它的第一个参数永远是 self，指向调用该方法的实例本身，**其他参数和一个普通函数是完全一样的：

```python
class Person(object):

    def __init__(self, name):
        self.__name = name

    def get_name(self):
        return self.__name\
```

`get_name(self)` 就是一个实例方法，它的第一个参数是`self`。`__init__(self, name)`其实也可看做是一个特殊的实例方法。

调用实例方法必须在实例上调用：

```python
p1 = Person('Bob')
print p1.get_name()  # self不需要显式传入
# => Bob
```

在实例方法内部，可以访问所有实例属性，这样，**如果外部需要访问私有属性**，可以通过方法调用获得，这种数据封装的形式除了**能保护内部数据一致性外**，还可以简化外部调用的难度。

### 编程任务

> 请给 Person 类增加一个私有属性 `__score`，表示分数，再增加一个实例方法 `get_grade()`，能根据 `__score` 的值分别返回 `A-优秀, B-及格, C-不及格`三档。

实现代码:

```python
class Person(object):

    def __init__(self, name, score):
        self.__name = name
        self.__score = score


    def get_grade(self):
        score = self.__score
        if score >85:
            return 'A'
        elif score >60:
            return 'B'
        elif score <60:
            return 'C'

p1 = Person('Bob', 90)
p2 = Person('Alice', 65)
p3 = Person('Tim', 48)

print p1.get_grade()
print p2.get_grade()
print p3.get_grade()
```

注：可以在访问数据时顺便通过`get_grade`做一些其他操作。

运行结果：

```
A
B
C
```

## 方法也是属性

我们在 `class`中定义的`实例方法`其实也是`属性`，它实际上是一个`函数对象`：

```python
class Person(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def get_grade(self):
        return 'A'
```

```python
p1 = Person('Bob', 90)
print p1.get_grade
# => <bound method Person.get_grade of <__main__.Person object at 0x109e58510>>
print p1.get_grade()
# => A
```

`知识点:` 也就是说，`p1.get_grade` 返回的是一个函数对象，但这个函数是一个绑定到实例的函数，`p1.get_grade()` 才是方法调用。

知识点；因为方法也是一个属性，所以，它也可以动态地添加到实例上，只是需要用 `types.MethodType()` 把一个函数变为一个方法：

```python

import types
def fn_get_grade(self):
    if self.score >= 80:
        return 'A'
    if self.score >= 60:
        return 'B'
    return 'C'

class Person(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score

p1 = Person('Bob', 90)
p1.get_grade = types.MethodType(fn_get_grade, p1, Person)
print p1.get_grade()
# => A
p2 = Person('Alice', 65)
print p2.get_grade()
# ERROR: AttributeError: 'Person' object has no attribute 'get_grade'
# 因为p2实例并没有绑定get_grade
```

知识点: `types.MethodType`传入三个参数，(方法，对象，类)实现将函数变为对象的一个方法。

给一个实例动态添加方法并不常见，直接在`class`中定义要更直观。

### 编程任务
>由于属性可以是普通的值对象，如 `str，int `等，也可以是方法，还可以是函数，大家看看下面代码的运行结果，请想一想 `p1.get_grade` 为什么是函数而不是方法：

```python
class Person(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
        self.get_grade = lambda: 'A'

p1 = Person('Bob', 90)
print p1.get_grade
print p1.get_grade()
```

注：
- `p1.get_grade`是属性，只不过这里的属性是一个函数对象，即`f`
- `p1.get_grade()`是方法，前面的p1就是调用这个方法的对象

实现代码:

```python
class Person(object):

    def __init__(self, name, score):
        self.name = name
        self.score = score
        self.get_grade = lambda: 'A'

p1 = Person('Bob', 90)
print p1.get_grade
print p1.get_grade()
```

运行结果：

```
 at 0x7fa7202fb5f0>
A
```

## 定义类方法

和属性类似，方法也分`实例方法`和`类方法`。

在class中定义的全部是`实例方法`，实例方法第一个参数 `self` 是实例本身。

要在class中定义类方法，需要这么写：

```python
class Person(object):
    count = 0
    @classmethod
    def how_many(cls):
        return cls.count
    def __init__(self, name):
        self.name = name
        Person.count = Person.count + 1

print Person.how_many()
p1 = Person('Bob')
print Person.how_many()
```

`知识点:` 通过标记一个 `@classmethod`，该方法将绑定到 Person 类上，而非类的实例。**类方法的第一个参数将传入类本身，通常将参数名命名为 cls**，上面的 `cls.count`实际上相当于 `Person.count`。

`知识点:` 因为是在类上调用，而非实例上调用，因此类方法无法获得任何实例变量，只能获得类的引用。

### 编程任务
>如果将类属性 `count` 改为私有属性`__count`，则外部无法读取`__score`，但可以通过一个类方法获取，请编写类方法获得`__count`值。

实现代码:

```python
class Person(object):

    __count = 0
    @classmethod
    def how_many(cls):
        return cls.__count
    def __init__(self, name):
        self.name = name
        Person.__count = Person.__count + 1
    

print Person.how_many()

p1 = Person('Bob')

print Person.how_many()
```

运行结果：

```
0
1
```

# Python类的继承

如何判断实例类型，多态以及如何获取对象信息。

## 什么是继承

继承：

- 新类不必从头编写，
- 可以直接从现有类继承，就自动拥有了现有类的所有功能，
- 新类只需要编写现有类缺少的新功能即可。

继承优点：

- 复用已有代码
- 自动拥有了现有类的所有功能
- 只需要编写缺少的新功能

![mark](http://myphoto.mtianyan.cn/blog/180104/aCHbG7F851.png?imageslim)

会形成一棵继承树

继承的特点：

- 子类和父类是is关系

![mark](http://myphoto.mtianyan.cn/blog/180104/EC9KfiGb5j.png?imageslim)
![mark](http://myphoto.mtianyan.cn/blog/180104/GKLI9Hi0kL.png?imageslim)

如果一个实例是一个子类，则它也是一个父类；如果实例是父类，则它不是子类。
`is`关系指的是：小狗是鸟，却不能说动物是小狗

`has`关系指的是：学生有一本书，不能说学生是一本书

两个`has`关系的类不能继承，只能以属性组合到类中.

```python
class Student(Person):
    def __init__(self , bookName):
        self.book=Book(bookName)
```

继承特点：
1. 总是从某个类继承，没有合适的类时使用`object`类继承
2. 调用`super().__init__`方法（用来初始化父类），如果不用父类的属性有可能没有被正确初始化。

`Student`类从父类继承`name`和`gender`：

`super(Student,self).__init__(name,gender)`调用这一句来初始化父类。

## 继承一个类

如果已经定义了`Person`类，需要定义新的`Student`和`Teacher`类时，可以直接从`Person`类继承：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
```

定义`Student`类时，只需要把额外的属性加上，例如`score`：

```python
class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
```

`知识点：`一定要用 `super(Student, self).__init__(name, gender)`去初始化父类，否则，继承自 `Person`的 `Student` 将没有 `name` 和 `gender`。

函数`super(Student, self)`将返回当前类继承的父类，即 `Person` ，然后调用`__init__()`方法，注意`self`参数已在`super()`中传入，在__init__()中将隐式传递，**不需要写出（也不能写）**。

### 编程任务
>请参考 `Student` 类，编写一个 `Teacher`类，也继承自 `Person`。

实现代码:

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Teacher(Person):

    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course
        

t = Teacher('Alice', 'Female', 'English')
print t.name
print t.course
```

运行结果：

```
Alice
English
```

## 判断类型

函数`isinstance()`可以判断一个`变量的类型`，既可以用在Python内置的数据类型如`str、list、dict`，也可以用在我们自定义的类，`它们本质上都是数据类型`。

假设有如下的 `Person`、`Student` 和 `Teacher` 的定义及继承关系如下：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score

class Teacher(Person):
    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course

p = Person('Tim', 'Male')
s = Student('Bob', 'Male', 88)
t = Teacher('Alice', 'Female', 'English')
```

当我们拿到变量 `p`、`s`、`t` 时，可以使用 `isinstance` 判断类型：

```python
>>> isinstance(p, Person)
True    # p是Person类型
>>> isinstance(p, Student)
False   # p不是Student类型
>>> isinstance(p, Teacher)
False   # p不是Teacher类型
```
这说明在继承链上，一个父类的实例不能是子类类型，因为**子类比父类多了一些属性和方法。**

我们再考察 `s `：

```python
>>> isinstance(s, Person)
True    # s是Person类型
>>> isinstance(s, Student)
True    # s是Student类型
>>> isinstance(s, Teacher)
False   # s不是Teacher类型
```

`s `是`Student`类型，不是`Teacher`类型，这很容易理解。但是，`s` 也是`Person`类型，因为`Student`继承自`Person`，虽然它比**Person多了一些属性和方法**，但是，把 s 看成Person的实例也是可以的。

这说明在一条继承链上，**一个实例可以看成它本身的类型，也可以看成它父类的类型。**

### 编程任务
>请根据继承链的类型转换，依次思考 `t `是否是 `Person，Student，Teacher，object `类型，并使用`isinstance()`判断来验证您的答案。

实现代码:

```python
class Person(object):

    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):

    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score

class Teacher(Person):

    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course

t = Teacher('Alice', 'Female', 'English')

print isinstance(t, Person)
print isinstance(t, Student)
print isinstance(t, Teacher)
print isinstance(t, object)
```

运行结果：

```
True
False
True
True
```

## 多态

类具有继承关系，并且子类类型可以向上转型看做父类类型，如果我们从 `Person` 派生出`Student`和`Teacher` ，并都写了一个`whoAmI()` 方法：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
    def whoAmI(self):
        return 'I am a Person, my name is %s' % self.name

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
    def whoAmI(self):
        return 'I am a Student, my name is %s' % self.name

class Teacher(Person):
    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course
    def whoAmI(self):
        return 'I am a Teacher, my name is %s' % self.name
```

在一个函数中，如果我们接收一个变量 x，则无论该 x 是 Person、Student还是 Teacher，都可以正确打印出结果：

```python
def who_am_i(x):
    print x.whoAmI()

p = Person('Tim', 'Male')
s = Student('Bob', 'Male', 88)
t = Teacher('Alice', 'Female', 'English')

who_am_i(p)
who_am_i(s)
who_am_i(t)
```

运行结果：

```
I am a Person, my name is Tim
I am a Student, my name is Bob
I am a Teacher, my name is Alice
```

`知识点`：这种行为称为多态。也就是说，方法调用将作用在 `x `的实际类型上。`s 是Student类型`，它实际上拥有自己的 `whoAmI()`方法以及从 `Person继承的 whoAmI方法`，但调用 `s.whoAmI()`总是先查找它自身的定义，如果没有定义，则顺着继承链向上查找，直到在某个父类中找到为止。

由于Python是动态语言，所以，传递给函数 `who_am_i(x)`的参数 `x` 不一定是 `Person` 或 `Person 的子类型`。任何数据类型的实例都可以，只要它有一个whoAmI()的方法即可：

```python
class Book(object):
    def whoAmI(self):
        return 'I am a book'
```

知识点：这是动态语言和静态语言（例如Java）最大的差别之一。动态语言调用实例方法，不检查类型，只要方法存在，参数正确，就可以调用。

### 编程任务
>Python提供了`open()`函数来打开一个磁盘文件，并返回 `File `对象。`File对象`有一个`read()`方法可以读取文件内容：

例如，从文件读取内容并解析为JSON结果：

```python
import json
f = open('/path/to/file.json', 'r')
print json.load(f)
```

由于Python的动态特性，`json.load()`并不一定要从一个`File对象`读取内容。任何对象，只要有`read()`方法，就称为`File-like Object`，都可以传给`json.load()`。

请尝试编写一个`File-like Object`，把一个字符串 `r'["Tim", "Bob", "Alice"]'包装成 File-like Object` 并由 `json.load()` 解析。

实现代码:

```python
import json

class Students(object):
    def __init__(self, strlist):
        self.strlist = strlist
        
    def read(self):
        return(self.strlist)

s = Students('["Tim", "Bob", "Alice"]')

print json.load(s)
```

运行结果：

```
[u'Tim', u'Bob', u'Alice']
```

## 多重继承

除了从`一个`父类继承外，Python允许从`多个父类`继承，称为**多重继承。**

多重继承的继承链就不是一棵树了，它像这样：

```python
class A(object):
    def __init__(self, a):
        print 'init A...'
        self.a = a

class B(A):
    def __init__(self, a):
        super(B, self).__init__(a)
        print 'init B...'

class C(A):
    def __init__(self, a):
        super(C, self).__init__(a)
        print 'init C...'

class D(B, C):
    def __init__(self, a):
        super(D, self).__init__(a)
        print 'init D...'
```

看下图:

![mark](http://myphoto.mtianyan.cn/blog/180104/IJ2jKJHFBJ.png?imageslim)


像这样，`D` 同时继承自 `B`和 `C`，也就是 `D` 拥有了 `A、B、C `的全部功能。多重继承通过 `super()`调用`__init__()`方法时，A 虽然被继承了两次，但`__init__()`只调用一次：

```python
>>> d = D('d')
init A...
init C...
init B...
init D...
```

多重继承的目的是从**两种继承树中分别选择并继承出子类，**以便组合功能使用。

举个例子，Python的网络服务器有`TCPServer`、`UDPServer`、`UnixStreamServer`、`UnixDatagramServer`，而服务器运行模式有 多进程`ForkingMixin` 和 多线程`ThreadingMixin`两种。

要创建多进程模式的 `TCPServer`：

```python
class MyTCPServer(TCPServer, ForkingMixin)
    pass
```

要创建多线程模式的 `UDPServer`：

```python
class MyUDPServer(UDPServer, ThreadingMixin):
    pass
```

如果没有**多重继承，要实现上述所有可能的组合需要 4x2=8 个子类**。

### 编程任务
```
+-Person
  +- Student
  +- Teacher

是一类继承树；

+- SkillMixin
   +- BasketballMixin
   +- FootballMixin

是一类继承树。
```

通过多重继承，请定义“会打篮球的学生”和“会踢足球的老师”。

实现代码:

```python
class Person(object):
    pass

class Student(Person):
    pass

class Teacher(Person):
    pass

class SkillMixin(object):
    pass

class BasketballMixin(SkillMixin):
    def skill(self):
        return 'basketball'

class FootballMixin(SkillMixin):
    def skill(self):
        return 'football'

class BStudent(BasketballMixin,Student):
    pass

class FTeacher(FootballMixin,Teacher):
    pass

s = BStudent()
print s.skill()

t = FTeacher()
print t.skill()
```

运行结果：

```
basketball
football
```

## 获取对象信息(知识点)

拿到一个变量，除了用`isinstance()`判断它是否是某种类型的实例外，还有没有别的方法获取到更多的信息呢？

例如，已有定义：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
    def whoAmI(self):
        return 'I am a Student, my name is %s' % self.name
```

首先可以用 `type()` 函数获取变量的类型，它返回一个 `Type 对象`：

```python
>>> type(123)
<type 'int'>
>>> s = Student('Bob', 'Male', 88)
>>> type(s)
<class '__main__.Student'>
```

其次，可以用 `dir()` 函数获取变量的`所有属性`：

```python
>>> dir(123)   # 整数也有很多属性...
['__abs__', '__add__', '__and__', '__class__', '__cmp__', ...]

>>> dir(s)
['__class__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'gender', 'name', 'score', 'whoAmI']
```

对于实例变量，`dir()`返回所有实例属性，包括`__class__`这类有特殊意义的属性。注意到方法`whoAmI`也是 `s` 的一个属性。

如何去掉`__xxx__`这类的特殊属性，只保留我们自己定义的属性？回顾一下filter()函数的用法。

`dir()`返回的属性是字符串列表，如果已知一个属性名称，要获取或者设置对象的属性，就需要用 `getattr()` 和 `setattr( )`函数了：

```python
>>> getattr(s, 'name')  # 获取name属性
'Bob'

>>> setattr(s, 'name', 'Adam')  # 设置新的name属性

>>> s.name
'Adam'

>>> getattr(s, 'age')  # 获取age属性，但是属性不存在，报错：
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Student' object has no attribute 'age'

>>> getattr(s, 'age', 20)  # 获取age属性，如果属性不存在，就返回默认值20：
20
```

### 编程任务
对于Person类的定义：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
````
希望除了 `name`和`gender` 外，可以提供任意`额外的关键字参数`，并绑定到实例，请修改 Person 的 `__init__()`定 义，完成该功能。

实现代码:

```python
class Person(object):

    def __init__(self, name, gender, **kw):
        for k,v in kw.items():
            setattr(self, k, v)


p = Person('Bob', 'Male', age=18, course='Python')
print p.age
print p.course
```

运行结果：

```
18
Python
```

# Python的特殊方法(魔术方法)
以及如何利用特殊方法定制类，实现各种强大的功能。

## 什么是特殊方法？

demo：

比较`print`的结果：

```
>>> print lst
[1,2,3]
```
![mark](http://myphoto.mtianyan.cn/blog/180104/mCLK742CDH.png?imageslim)

对于一个`Person`类的实例进行`print`，会得到一个对象地址。

python如何把任意变量变成str?

python能够将任意变量变成str是因为任何数据类型的实例都有一个特殊方法：`__str__()`
思考：Person类并没有定义`__str__()`，为什么能调用？

![mark](http://myphoto.mtianyan.cn/blog/180104/HbCH7j0hDf.png?imageslim)

对应调用`list`和`Person`实例的`__str__()`方法。

如果我们给Person类加上特殊方法`__str__()`，我们就可以根据自己需要打印出Person实例来。
![mark](http://myphoto.mtianyan.cn/blog/180104/1CdDk608fB.png?imageslim)

- 用于print的__str__
- 用于len的__len__
- 用于cmp的__cmp__

python的特殊方法特点：

- 特殊方法定义在`class`中
- 不需要直接调用
- python的某些函数或操作符会自动调用对应的特殊方法。

Python定义的一部分特殊方法:

![mark](http://myphoto.mtianyan.cn/blog/180104/25k9LCamf4.png?imageslim)

正确实现特殊方法：

- 只需编写用到的特殊方法
- 有关联性的特殊方法都必须实现 

如：

```python
__getattr__
__setattr__
__delattr__
```
这三个方法需要同时编写

##  `__str__`和`__repr__`

如果要把一个类的实例变成 `str`，就需要实现特殊方法`__str__()`：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
    def __str__(self):
        return '(Person: %s, %s)' % (self.name, self.gender)
```

现在，在交互式命令行下用 print 试试：

```python
>>> p = Person('Bob', 'male')
>>> print p
(Person: Bob, male)
```

但是，如果直接敲变量 p：

```
>>> p
<main.Person object at 0x10c941890>
```
似乎`__str__() `不会被调用。

`知识点`: 因为 Python 定义了`__str__()`和`__repr__()`两种方法，`__str__()`用于显示给用户，而`__repr__()`用于显示给开发人员。

有一个偷懒的定义`__repr__`的方法：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
    def __str__(self):
        return '(Person: %s, %s)' % (self.name, self.gender)
    __repr__ = __str__
```
### 编程任务
请给`Student` 类定义`__str__`和`__repr__`方法，使得能打印出`<Student: name, gender, score>`：

```python
class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
```

实现代码:

```python
class Person(object):

    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):

    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score

    def __str__(self):
        return '(Student: %s, %s, %s)' % (self.name, self.gender, self.score)

s = Student('Bob', 'male', 88)
print s
```

运行结果：

```
(Student: Bob, male, 88)
```

##  `__cmp__`

对 `int、str` 等内置数据类型排序时，Python的 `sorted()` 按照默认的比较函数 `cmp `排序，但是，如果对一组 `Student 类`的实例排序时，就必须提供我们自己的特殊方法 `__cmp__()`：

```python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def __str__(self):
        return '(%s: %s)' % (self.name, self.score)
    __repr__ = __str__

    def __cmp__(self, s):
        if self.name < s.name:
            return -1
        elif self.name > s.name:
            return 1
        else:
            return 0
```

上述 Student 类实现了`__cmp__()`方法，`__cmp__`用实例自身`self`和传入的实例`s`进行比较，如果 `self` 应该排在前面，就返回 `-1`，如果 `s `应该排在前面，就返回`1`，如果两者相当，返回 `0`。

`Student`类实现了按`name`进行排序：

```python
>>> L = [Student('Tim', 99), Student('Bob', 88), Student('Alice', 77)]
>>> print sorted(L)
[(Alice: 77), (Bob: 88), (Tim: 99)]
```

注意: 如果`list`不仅仅包含 `Student` 类，则 `__cmp__` 可能会报错：

```python
L = [Student('Tim', 99), Student('Bob', 88), 100, 'Hello']
print sorted(L)
```
请思考如何解决。
(未完待续)

### 编程任务
>请修改 `Student` 的 `__cmp__` 方法，让它按照分数从高到底排序，分数相同的按名字排序。

实现代码:

```python
class Student(object):

    def __init__(self, name, score):
        self.name = name
        self.score = score

    def __str__(self):
        return '(%s: %s)' % (self.name, self.score)

    __repr__ = __str__

    def __cmp__(self, s):
        if self.score>s.score:

            return -1

        elif self.score<s.score:

            return 1

        elif self.name<s.name:

            return -1

        elif self.nae>s.name:

            return 1

        else:

            return 0

L = [Student('Tim', 99), Student('Bob', 88), Student('Alice', 99)]
print sorted(L)
```

运行结果：

```
[(Alice: 99), (Tim: 99), (Bob: 88)]
```

## `__len__`

如果一个类表现得像一个`list`，要获取有多少个元素，就得用 `len()` 函数。

要让 `len()` 函数工作正常，类必须提供一个特殊方法`__len__()`，它返回元素的个数。

例如，我们写一个 `Students` 类，把名字传进去：

```python
class Students(object):
    def __init__(self, *args):
        self.names = args
    def __len__(self):
        return len(self.names)
```

只要正确实现了`__len__()`方法，就可以用len()函数返回`Students实例`的“长度”：

```
>>> ss = Students('Bob', 'Alice', 'Tim')
>>> print len(ss)
3
```

### 编程任务(天涯)
斐波那契数列是由 `0, 1, 1, 2, 3, 5, 8...`构成。

请编写一个`Fib`类，`Fib(10)`表示数列的前10个元素，`print Fib(10) `可以打印出数列的前 10 个元素，`len(Fib(10))`可以正确返回数列的个数`10`。

实现代码:

```python
class Fib(object):

    def __init__(self, num):
        self.num = num
        self.fibo = [0,1]
        i = 2
        while i < self.num:
            self.fibo.append(self.fibo[i-2] + self.fibo[i-1])
            i = i + 1
    
    def __str__(self):
        return str(self.fibo)

    def __len__(self):
        return len(self.fibo)

f = Fib(10)
print f
print len(f)
```

运行结果：

```
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
10
```

## 数学运算

Python 提供的基本数据类型 `int、float `以做整数和浮点的四则运算以及乘方等运算。

但是，四则运算不局限于int和float，还可以是`有理数、矩阵`等。

要表示有理数，可以用一个`Rational类`来表示：

```
class Rational(object):
    def __init__(self, p, q):
        self.p = p
        self.q = q
```

p、q 都是整数，表示有理数 p/q。

如果要让`Rational`进行`+`运算，需要正确实现`__add__`：

```python
class Rational(object):
    def __init__(self, p, q):
        self.p = p
        self.q = q
    def __add__(self, r):
        return Rational(self.p * r.q + self.q * r.p, self.q * r.q)
    def __str__(self):
        return '%s/%s' % (self.p, self.q)
    __repr__ = __str__
```

现在可以试试有理数加法：

```
>>> r1 = Rational(1, 3)
>>> r2 = Rational(1, 2)
>>> print r1 + r2
5/6
```

### 编程任务(天涯)
>`Rational`类虽然可以做加法，但无法做减法、乘方和除法，请继续完善Rational类，实现四则运算。

提示：

```
减法运算：__sub__
乘法运算：__mul__
除法运算：__div__
```

实现代码:

```python
def gcs(a,b,c=1):
    if 0==a%2 and 0==b%2:
        return gcs(a/2,b/2,c*2);
        
    s = abs(a-b)
    m = min(a,b)
    if s == m:
        return m*c
    return gcs(s,m,c)
    

class Rational(object):
    def __init__(self, p, q):
        self.p = p
        self.q = q

    def __add__(self, r):
        return Rational(self.p * r.q + self.q * r.p, self.q * r.q)

    def __sub__(self, r):
        return Rational(self.p * r.q - self.q * r.p, self.q * r.q)

    def __mul__(self, r):
        return Rational(self.p * r.p, self.q * r.q)

    def __div__(self, r):
        return Rational(self.p * r.q , self.q * r.p)

    def __str__(self):
        c = gcs(self.p, self.q)
        return '%s/%s' % (self.p/c, self.q/c)

    __repr__ = __str__

r1 = Rational(1, 2)
r2 = Rational(1, 4)
print r1 + r2
print r1 - r2
print r1 * r2
print r1 / r2
```
推荐阅读评论区：https://www.imooc.com/code/6253

运行结果：

```
3/4
1/4
1/8
2/1
```

## 类型转换

Rational类实现了有理数运算，但是，如果要把结果转为 `int` 或 `float` 怎么办？

考察整数和浮点数的转换：

```python
>>> int(12.34)
12
>>> float(12)
12.0
```

如果要把 `Rational` 转为 `int`，应该使用：

```python
r = Rational(12, 5)
n = int(r)
```
要让`int()`函数正常工作，只需要实现特殊方法`__int__()`:

```python
class Rational(object):
    def __init__(self, p, q):
        self.p = p
        self.q = q
    def __int__(self):
        return self.p // self.q
```

结果如下：

```python
>>> print int(Rational(7, 2))
3
>>> print int(Rational(1, 3))
0
```

同理，要让`float()`函数正常工作，只需要实现特殊方法`__float__()`。

### 编程任务

>请继续完善`Rational`，使之可以转型为`float`。

实现代码:

```python
class Rational(object):
    def __init__(self, p, q):
        self.p = p
        self.q = q

    def __int__(self):
        return self.p // self.q

    def __float__(self):
        return float(self.p)/self.q

print float(Rational(7, 2))
print float(Rational(1, 3))
```

运行结果：

```
3.5
0.333333333333
```

## `@property`

考察 `Student` 类：

```python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
```

当我们想要修改一个 `Student` 的 `scroe` 属性时，可以这么写：

```
s = Student('Bob', 59)
s.score = 60
```

但是也可以这么写：

```
s.score = 1000
```

显然，直接给属性赋值无法检查分数的有效性。

如果利用两个方法：

```
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.__score = score
    def get_score(self):
        return self.__score
    def set_score(self, score):
        if score < 0 or score > 100:
            raise ValueError('invalid score')
        self.__score = score
```
这样一来，`s.set_score(1000)` 就会报错。

这种使用 `get/set` 方法来封装对一个**属性的访问**在许多面向对象编程的语言中都很常见。

`知识点:` 但是写 `s.get_score()` 和 `s.set_score()` 没有直接写 s.score 来得直接。
有没有两全其美的方法？----有。

因为Python支持高阶函数，在函数式编程中我们介绍了`装饰器函数`，可以用`装饰器函数`把 `get/set` 方法“装饰”成`属性调用`：

```python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.__score = score
    @property
    def score(self):
        return self.__score
    @score.setter
    def score(self, score):
        if score < 0 or score > 100:
            raise ValueError('invalid score')
        self.__score = score
```

注意: 第一个`score(self)`是`get`方法，用`@property`装饰，第二个`score(self, score)`是`set`方法，用`@score.setter`装饰，`@score.setter`是前一个`@property`装饰后的副产品。

现在，就可以像使用属性一样设置score了：

```python
>>> s = Student('Bob', 59)
>>> s.score = 60
>>> print s.score
60
>>> s.score = 1000
Traceback (most recent call last):
  ...
ValueError: invalid score
```

说明对 `score` 赋值实际调用的是 `set`方法。

### 编程任务
>如果没有定义`set`方法，就不能对“属性”赋值，这时，就可以创建一个只读“属性”。
请给`Student`类加一个`grade`属性，根据 `score `计算 `A（>=80）、B、C（<60）`。

实现代码:

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Date    : 2018-01-04 07:44:12
# @Author  : Your Name (you@example.org)
# @Link    : http://example.org
# @Version : $Id$

class Student(object):

    def __init__(self, name, score):
        self.name = name
        self.__score = score

    @property
    def score(self):
        return self.__score

    @score.setter
    def score(self, score):
        if score < 0 or score > 100:
            raise ValueError('invalid score')
        self.__score = score

    @property
    def grade(self):
        if self.score >= 80:
            return "A"
        elif self.score >=60:
            return "B"
        else:
            return "C"

s = Student('Bob', 59)
print s.grade

s.score = 60
print s.grade

s.score = 99
print s.grade

```

`@property`,可以将python定义的函数“当做”属性访问，从而提供更加友好访问方式
注意`self.score` 不要写成`score` 会报错。

运行结果：

```
C
B
A
```

##  `__slots__`

由于Python是动态语言，**任何实例在运行期都可以动态地添加属性。**

`知识点`：如果要限制添加的属性，例如，`Student`类只允许添加 `name、gender和score` 这3个属性，就可以利用Python的一个特殊的`__slots__`来实现。

顾名思义，`__slots__`是指一个类允许的属性列表：

```python
class Student(object):
    __slots__ = ('name', 'gender', 'score')
    def __init__(self, name, gender, score):
        self.name = name
        self.gender = gender
        self.score = score
```

现在，对实例进行操作：

```
>>> s = Student('Bob', 'male', 59)
>>> s.name = 'Tim' # OK
>>> s.score = 99 # OK
>>> s.grade = 'A'
Traceback (most recent call last):
  ...
AttributeError: 'Student' object has no attribute 'grade'
```

`__slots__`的目的是**限制当前类所能拥有的属性，**如果不需要添加任意动态的属性，使用`__slots__`也能节省内存。

### 编程任务
>假设`Person`类通过`__slots__`定义了`name`和`gender`，请在派生类`Student`中通过`_slots__`继续添加`score`的定义，使`Student`类可以实现`name、gender和score` 3个属性。

实现代码:

```python
class Person(object):

    __slots__ = ('name', 'gender')

    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):

    __slots__ = ('score')

    def __init__(self,name,gender,score):
        self.name = name
        self.score = score
        self.gender = gender 

s = Student('Bob', 'male', 59)
s.name = 'Tim'
s.score = 99
print s.score
```

运行结果：

```
99
```

##  `__call__`

在Python中，函数其实是一个对象：

```python
>>> f = abs
>>> f.__name__
'abs'
>>> f(-123)
123
```

由于 `f` 可以被调用，所以，`f` 被称为可调用对象。

**所有的函数都是可调用对象。**

一个`类实例`也可以变成一个可调用对象，只需要实现一个特殊方法`__call__()`。

我们把 `Person` 类变成一个可调用对象：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

    def __call__(self, friend):
        print 'My name is %s...' % self.name
        print 'My friend is %s...' % friend
```

现在可以对 Person 实例直接调用：

```
>>> p = Person('Bob', 'male')
>>> p('Tim')
My name is Bob...
My friend is Tim...
```

单看 `p('Tim') `你无法确定 p 是一个函数还是一个类实例，所以，在Python中，函数也是**对象，对象和函数的区别并不显著。**

### 编程任务
>改进一下前面定义的斐波那契数列：

```python
class Fib(object):
    ???
```

请加一个`__call__`方法，让调用更简单：

```
>>> f = Fib()
>>> print f(10)
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

实现代码:

```python
class Fib(object):
    def __call__(self,num):
        a,b,c = 0,1,[]
        for n in range(num):
            c.append(a)
            a,b = b,a+b
        return c

f = Fib()
print f(10)
```

运行结果：

```
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

# 课程总结

Python的函数式编程：

- 函数式与函数的区别。
- 支持高阶函数：
    - 函数本身可作为变量传入另一个函数。
    - 抽象度很高的模型。
    - 内置函数`map` `sorted` `reduce` `filter`中都有高阶函数应用。
- 闭包：利用闭包来返回函数
- 匿名函数：限制,匿名函数只能有一个表达式：表达式的结果就是匿名函数的返回值。
- 装饰器：高阶函数的应用，可以把一个函数装饰成另一个函数。以便能在运行时动态增加函数功能。

Python的模块和包：

- 模块的目的：避免名字冲突。
- 包可以看成具有目录层次的模块(`__init__.py`)
- 引用模块
- 引用__future__添加新版本中的特性。

Python的面向对象编程:

- 类和实例(类是模板，实例是根据模板创健的对象)
- 属性和方法。(可以把属性看成是一个方法？)，绑定到实例的函数对象。
- 区分类属性和实例属性(优先级，尽量不要重名)

类的继承中：

- 继承的概念和目的(代码复用)
- 多态（从一个父类派生出多个子类。可以使子类具有各自不同的行为。）
- 多重继承

定制类：

- 定制类的目的：为了让我们编写的类应用到普通函数中。`len()` `cmp()`
- 特殊方法
- 类型转换(把任意类型转化为string类型，int类型)
- `__call__`方法：把实例变成一个可以跟函数一样调用的对象。

1. 任何数据类型的实例都有一个特殊方法`__str__()`类似于`toString`
2. 特殊方法的特征：
      - 特殊方法定义在class中
      - 不需要直接调用
      - Python的某些函数或者操作符会调用对应的特殊方法
3. 正确实现特殊方法：
      只需要编写用到的特殊方法
      有关联性的特殊方法都必须实现：
```
        如 __getattr__
           __setattr__
           __delattr__
```

4. python中`__str__`和`__repr__`
如果要把一个类的实例变成 `str`，就需要实现特殊方法`__str__()`：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
    def __str__(self):
        return '(Person: %s, %s)' % (self.name, self.gender)
```

`__str__()`用于显示给用户，而`__repr__()`用于显示给开发人员。

有一个偷懒的定义`__repr__`的方法：


```
#正常定义完__str__后
__repr__ = __str__  #把__str__赋予__repr__
```

5. 特殊方法之 `__cmp__`
对一组 `Student` 类的实例排序时，就必须提供我们自己的特殊方法 `__cmp__()`：

```python
 def __cmp__(self, s):
        if self.name < s.name:
            return -1
        elif self.name > s.name:
            return 1
        else:
            return 0
```
上述 `Student` 类实现了`__cmp__()`方法，`__cmp__`用实例自身`self`和传入的实例 `s`进行比较.

6. 在`class`中定义`__init__(self),__float__(self)`方法：数据类型转换

7. python中 `@property`
`get/set` 方法来封装对一个属性的访问
用装饰器函数把 `get/set` 方法“装饰”成属性调用

`@property和@method.setter`是搭配使用的，
`@property`对应`get`方法（相当于只读不可更改），`@method.setter`对应`set`方法。


8. python中`__slots__`
任何实例在运行期都可以动态地添加属性
如果要限制添加的属性，例如，`Student`类只允许添加 `name、gender和score` 这3个属性，
就可以利用Python的一个特殊的`__slots__`来实现。

```
__slots__ = ('name', 'gender', 'score')
```
顾名思义，`__slots__`是指一个类允许的属性列表

子类继续父类的场合：
`__slots__`定义的属性仅对当前类起作用，对继承的子类是不起作用的。
除非在子类中也定义`__slots__`，此时，子类允许定义的属性就是自身的`__slots__加上父类中定义的__slots__`。


下一步进阶：

- IO：文件和Socket
- 多任务：进程和线程
- 数据库
- Web开发

























































