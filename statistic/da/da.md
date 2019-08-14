# Data Analysis

### Velen Kong



## 摘要

基于Python的数据分析入门笔记，希望能自学掌握基本的数据分析能力，毕竟是统计学的基础之一。

内容安排主要参考

(美) Wes McKinney 著. Python for Data Analysis:2nd Edition [M] USA: O'Reilly Media 2017

该书作者同时也是pandas库的作者，同时借用其在GitHub上的数据资料。



## 第三方库与Python入门



### IPython \& Jupyter

用到的库：ipython，jupyter，numpy，matplotlib，pandas，scipy，scikit-learn，statsmodels。

jupyter确实好用，扩展了$Tab,?,*$的功能。

还有一些快捷键仅限IPython使用。

另外就是一些常用的Magic Command，比如

```python
%run
%load
%debug
%xmode Plain # less detailed
%xmode Verbose # more detailed
%matplotlib inline # draw in Jupyter
import numpy as np
import matplotlib.pyplot as plt
plt.plot(np.random.rand(50).cumsum())
```

```python
# ----- Day 0 -----
```



### Python基础

#注释。

```python
# this is comment
```

所有变量都是对象(object)。

基本的函数调用，利用函数批量处理。

```python
def append_element(some_list, element):
    some_list.append(element)
    return

data = [1, 2, 3]
append_element(data, 4)
data
# Out: [1, 2, 3, 4]
```

变量赋值类似引用(reference)。

动态类型，利用type()和isinstance()进行类型检查。后者可以传入tuple代替逻辑或操作。

```python
a = 1.5
isinstance(a, (int, float))
# Out: True
```

print配合format输出。

```python
a = 1; b = 1.5
print('a is {1}, b is {0}'.format(type(b), type(a)))
# Out: a is <class 'int'>, b is <class 'float'>
```

Python中的object拥有各自的属性(attributes)和方法(methods)，可通过getattr, hasattr, setattr操作。其中getattr可以直接使用返回对象，setattr不改变原class。

```python
class A(object):        
    def set(self, a, b):
        x = a        
        a = b        
        b = x        
        print a, b   

a = A()                 
c = getattr(a, 'set')
c(a='1', b='2')
# Out: 2 1
```

可以利用try()检查容器是否是顺序，同时生成list。

```python
def isiterable(obj):
    try:
        iter(obj)
        return True
    except TypeError:
        return False
    return

x = 'string'
isiterable(x)
# Out: True
isiterable(5)
# Out: False

if not isinstance(x, list) and isiterable(x):
    x = list(x)
x
# Out: ['s', 't', 'r', 'i', 'n', 'g']
```

import和as的使用。

is和is not的使用。

```python
a = [1, 2, 3]
b = a
c = list(a)
d = None
print(a is b)
# Out: True
print(a is not c)
# Out: True
print(a == c)
# Out: True
print(d is None)
# Out: True
```

大部分Python的容器都是可变的(mutable)，而strings和tuples不可变(immutable)。

```python
a = ['foo', 2, [4, 5]]
a[2] = (3, 4)
a
# Out: ['foo', 2, (3, 4)]
```

```python
# ----- Day 1 -----
```

标量类型(scalar types)一般有$None, str, bytes, float, bool, int$。

多行字符串用三个引号。

```python
c = """
This is a longer string that
spans multiple lines
"""
c.count('\n')
# Out: 3
```

str()方法可以生成字符串，+可以直接拼接字符串。而replace()方法可以替换字符串内容，但不改变原串。

```python
a = 'this is a string'
b = a.replace('string', 'longer string')
print(b)
# Out: this is a longer string
print(a)
# Out: this is a string
```

Python采用$Unicode$编码，支持中文。对特殊字符可以采用\或者r进行转义。

```python
s = '12\\34'
print(s)
# Out: 12\34
s = r'this\has\no\special\characters'
s
# Out: 'this\\has\\no\\special\\characters'
```

format和{}可以进行格式化输出。

```python
template = '{0:.2f} {1:s} are worth US${2:d}'
template.format(4.5560, 'Argentine Pesos', 1)
# Out: '4.56 Argentine Pesos are worth US$1'
```

利用encode()和decode()函数可以对字符进行加解码。利用b生成二进制串。

```python
val = "español"
val_utf8 = val.encode('utf-8')
val_utf8
# Out: b'espa\xc3\xb1ol'
type(val_utf8)
# Out: bytes
val_utf8.decode('utf-8')
# Out: 'español'
bytes_val = b'this is bytes'
bytes_val
# Out: b'this is bytes'
decoded = bytes_val.decode('utf8')
decoded
# Out: 'this is bytes'
```

None是一个单独的类型，常见于函数的默认参数中。

```python
def add_and_maybe_multiply(a, b, c=None):
    result = a + b
    if c is not None:
        result = result * c
    return result

type(None)
# Out: NoneType
```

and和or运算。

Python自带时间与日期库。datetime是不可变类型，所以所有的操作都会产生新的对象而不改变原对象。

```python
from datetime import datetime, date, time
dt = datetime(2011, 10, 29, 20, 30, 21)
dt.day
# Out: 29
dt.date()
# Out: datetime.date(2011, 10, 29)
dt.strftime('%m/%d/%Y %H:%M')
# Out: '10/29/2011 20:30'
datetime.strptime('20091031', '%Y%m%d')
# Out: datetime.datetime(2009, 10, 31, 0, 0)
dt.replace(minute=0, second=0)
# Out: datetime.datetime(2011, 10, 29, 20, 0)
```

时间差用timedelta表示，单位是天和秒。

```python
dt2 = datetime(2011, 11, 15, 22, 30)
delta = dt2 - dt
delta
# Out: datetime.timedelta(17, 7179)
type(delta)
# Out: datetime.timedelta
dt + delta
# Out: datetime.datetime(2011, 11, 15, 22, 30)
```

时间的格式符号(format specification)如下

```python
%Y #4位年数
%y #2位年数
%m #2位月数
%d #2位天数
%H #24小时制(2位)
%I #12小时制(2位)
%M #2位分钟数
%S #2位秒数，由于闰秒存在，范围为[00, 61]
%w #星期，范围为[0, 6]
%U #一年的第几个星期，以周日为标准，第一个周日之前的算00
%W #同上，以周一为标准
%z #用+HHMM或-HHMM表示相对于格林威治的时区偏移
%Z #时区名称，默认为空
%F #等价于%Y-%m-%d
%D #等价于%m/%d/%y
```

if, elif, else语句。单行if。

```python
a = [1,2,3]
b = a if len(a) != 0 else ""
print(b)
# Out: [1, 2, 3]
```

for in语句。多变量for循环。

```python
starts = [0,1,2,3,4]
ends = [5,6,7,8,9]
for start, end in zip(starts, ends):
    print((start, end))
'''
Out:
(0, 5)
(1, 6)
(2, 7)
(3, 8)
(4, 9)
'''
```

while语句。

range()函数。

```python
# ----- Day 2 -----
```



### 数据结构

Tuple是Python的基本数据结构之一，可用逗号分隔直接创建，或者分解顺序容器，也可以通过range构造序列。

```python
tup = 3, (4, 5, 6), (7, 8)
tup
# Out: (3, (4, 5, 6), (7, 8))
tuple([4, 0, 2])
# Out: (4, 0, 2)
tuple('string')
# Out: ('s', 't', 'r', 'i', 'n', 'g')
tuple(['foo', [1, 2], True])
# Out: ('foo', [1, 2], True)
tuple(range(10))
# Out: (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```

tuple也可以直接进行$+,*$运算，和解压操作。

```python
(4, None, 'foo') + (6, 0) + ('bar',)
# Out: (4, None, 'foo', 6, 0, 'bar')
('foo', 'bar') * 4
# Out: ('foo', 'bar', 'foo', 'bar', 'foo', 'bar', 'foo', 'bar')
tup = 4, 5, (6, 7)
a, b, (c, d) = tup
d
# Out: 7
a, b = 1, 2
b, a = a, b
print(a,b)
# Out: 2 1
```

也可以配合多变量for循环。

```python
seq = [(1, 2, 3), (4, 5, 6), (7, 8, 9)]
for a, b, c in seq:
    print('a={0}, b={1}, c={2}'.format(a, b, c))
'''
Out:
a=1, b=2, c=3
a=4, b=5, c=6
a=7, b=8, c=9
'''
```

用*可以代指tuple的剩余部分。

```python
values = 1, 2, 3, 4, 5
a, b, *rest = values
rest
# Out: [3, 4, 5]
```

count是tuple的常用方法。

```python
a = (1, 2, 2, 2, 3, 4, 2)
a.count(2)
# Out: 4
```

List近似于可变的tuple，定义方法和tuple类似，也可以进行$+,*$操作。

利用append，insert，extend，pop，remove可以对list进行修改。但extend比$+$速度快。

```python
tup = ('foo', 'bar', 'baz')
b_list = list(tup)
b_list
# Out: ['foo', 'bar', 'baz']
b_list.append('dwarf')
b_list
# Out: ['foo', 'bar', 'baz', 'dwarf']
b_list.insert(1, 'red')
b_list
# Out: ['foo', 'red', 'bar', 'baz', 'dwarf']
b_list.extend([7, 8, (2, 3)])
b_list
# Out: ['foo', 'red', 'bar', 'baz', 'dwarf', 7, 8, (2, 3)]
b_list.pop(2)
b_list
# Out: ['foo', 'red', 'baz', 'dwarf', 7, 8, (2, 3)]
b_list.append('foo')
b_list.remove('foo')
b_list
# Out: ['red', 'baz', 'dwarf', 7, 8, (2, 3), 'foo']
```

sort可以对一个list排序，bisect库可以进行二分操作。但bisect需要预先排序。sorted可以生成排序后的list。还可以设置排序的key。

```python
import bisect
a = [7, 2, 2, 5, 1, 3]
a.sort()
a
# Out: [1, 2, 2, 3, 5, 7]
b = ['saw', 'small', 'He', 'foxes', 'six']
b.sort(key=len)
b
# Out: ['He', 'saw', 'six', 'small', 'foxes']
import bisect
bisect.bisect(a, 2)
# Out: 3
bisect.bisect(a, 6)
# Out: 5
bisect.insort(a, 6)
a
# Out: [1, 2, 2, 3, 5, 6, 7]
sorted('horse race')
# Out: [' ', 'a', 'c', 'e', 'e', 'h', 'o', 'r', 'r', 's']
sorted('horse race', key = lambda x : -ord(x))
# Out: ['s', 'r', 'r', 'o', 'h', 'e', 'e', 'c', 'a', ' ']
```

利用[begin: end: step]可以轻松实现部分list的选取和修改，其中step也可以为负数。reverse能反转整个容器。

```python
list(reversed(range(10)))
# Out: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

enumerate和zip可以用于生成变量组合。

```python
some_list = ['foo', 'bar', 'baz']
mapping = {}
for i, v in enumerate(some_list):
    mapping[v] = i
mapping
# Out: {'foo': 0, 'bar': 1, 'baz': 2}
seq1 = ['foo', 'bar', 'baz']
seq2 = ['one', 'two', 'three']
zipped = zip(seq1, seq2)
list(zipped)
# Out: [('foo', 'one'), ('bar', 'two'), ('baz', 'three')]
seq3 = [False, True]
list(zip(seq1, seq2, seq3))
# Out: [('foo', 'one', False), ('bar', 'two', True)]
for i, (a, b) in enumerate(zip(seq1, seq2)):
    print('{0}: {1}, {2}'.format(i, a, b))
'''
Out:
0: foo, one
1: bar, two
2: baz, three
'''
```

zip也可以反过来进行解压。

```python
pitchers = [('Nolan', 'Ryan'), ('Roger', 'Clemens'),
            ('Schilling', 'Curt')]
first_names, last_names = zip(*pitchers)
first_names
# Out: ('Nolan', 'Roger', 'Schilling')
```

```python
# ----- Day 3 -----
```

字典(dict)是Python最重要的数据结构之一，存储键值对(key-value pair)，基本操作如下。

```python
d1 = {'a' : 'some value', 'b' : [1, 2, 3, 4]}
d1
# Out: {'a': 'some value', 'b': [1, 2, 3, 4]}
d1['b']
# Out: [1, 2, 3, 4]
d1['dummy'] = 'another value'
d1
# Out: {'a': 'some value', 'b': [1, 2, 3, 4], 'dummy': 'another value'}
del d1['a']
d1
# Out: {'b': [1, 2, 3, 4], 'dummy': 'another value'}
ret = d1.pop('dummy')
ret
# Out: 'another value'
d1
# Out: {'b': [1, 2, 3, 4]}
'b' in d1
# Out: True
list(d1.keys())
# Out: ['b']
list(d1.values())
# Out: [[1, 2, 3, 4]]
d1['b'] = 1
d1
# Out: {'b': 1}
d1.update({'b': 2, 2: ['a', 'b']})
d1
# Out: {'b': 2, 2: ['a', 'b']}
```

dict()可以直接生成dict。

```python
map1 = dict(zip(range(5), range(5, -5, -1)))
map1
# Out: {0: 5, 1: 4, 2: 3, 3: 2, 4: 1}
map2 = dict(zip(range(10), range(5, 0, -1)))
map2
# Out: {0: 5, 1: 4, 2: 3, 3: 2, 4: 1}
```

读取dict值时还可以利用get设置默认值。如果不使用get，则会发生KeyError，比如pop()和del。所以使用dict前务必用in检查key是否存在。

```python
# value = some_dict.get(key, default_value)
```

在使用list作为值时，要注意将default设为空list。可以使用setdefault方法或者defaultdict类型。

```python
words = ['apple', 'bat', 'bar', 'atom', 'book']
by_letter = {}
for word in words:
    letter = word[0]
    by_letter.setdefault(letter, []).append(word)
by_letter
# Out: {'a': ['apple', 'atom'], 'b': ['bat', 'bar', 'book']}
from collections import defaultdict
by_letter = defaultdict(list)
by_letter
# Out: defaultdict(list, {})
for word in words:
    by_letter[word[0]].append(word)
by_letter
# Out: defaultdict(list, {'a': ['apple', 'atom'], 'b': ['bat', 'bar', 'book']})
```

dict利用了hash()，所以key必须是可以被hash的对象。例如list无法作为key使用，需要转化为tuple。因为在list变化后，hash值也被改变，因而dict中保存的list将找不到对应的value产生错误。

set是无序无重复的容器。利用set()或者{}来生成set。

set可以利用union(), intersection(), difference(), symmetrice_difference()来进行操作，也可以使用|, &, -, ^。

常见方法有:

add(), clear(), remove(), pop(), copy(), len();

union(), update(), intersection(), intersection_update(), difference(), difference_update(), symmetrice_difference(), symmetrice_difference_update();

issubset(), issuperset(), isdisjoint()。

和dict类似，remove()和pop()需要先用in检查，否则会抛出KeyError。

同样，set也利用了hash，所以也不能加入list。

for in if语句常被用于list，dict，set中。可以轻松进行条件筛选。

```python
strings = ['a', 'as', 'bat', 'car', 'dove', 'python']
[x.upper() for x in strings if len(x) > 2]
# Out: ['BAT', 'CAR', 'DOVE', 'PYTHON']
unique_lengths = {len(x) for x in strings}
unique_lengths
# Out: {1, 2, 3, 4, 6}
loc_mapping = {val : index for index, val in enumerate(strings)}
loc_mapping
# Out: {'a': 0, 'as': 1, 'bat': 2, 'car': 3, 'dove': 4, 'python': 5}
all_data = [['John', 'Emily', 'Michael', 'Mary', 'Steven'],
            ['Maria', 'Juan', 'Javier', 'Natalia', 'Pilar']]
result = [name for names in all_data for name in names
          if name.count('e') >= 1]
result
# Out: ['Michael', 'Steven', 'Javier']
```

也可以使用map函数，对顺序容器做一个映射。

```python
set(map(len, strings))
# Out: {1, 2, 3, 4, 6}
list(map(lambda k: k ** 2, [1, 2, 3, 4, 5]))
# Out: [1, 4, 9, 16, 25]
dict(map(lambda x, y: (x, y), [1, 3, 5, 7, 9], [2, 4, 6, 8, 10]))
# Out: {1: 2, 3: 4, 5: 6, 7: 8, 9: 10}
```

多重for in语句。

```python
some_tuples = [(1, 2, 3), (4, 5, 6), (7, 8, 9)]
[[x for x in tup] for tup in some_tuples]
# Out: [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

```python
# ----- Day 4 -----
```

### 函数

函数定义时可以设置默认参数。调用时可以无视默认参数。也可以乱序设定参数。

定义在函数内部的本地变量会在return时被销毁。但可以使用global来定义。但不建议过多使用全局变量，那说明需要使用class和面向对象编程(object-oriented programming)。

Python可以返回多个参数。

```python
def f():
    a = 5
    b = 6
    c = 7
    return a, b, c

c = 1
a, b, d = f()
print(a, b, c)
# Out: 5 6 1
```

Python中函数也是一种对象。由此可以将不同函数进行组合。

```python
import re
states = ['   Alabama ', 'Georgia!', 'Georgia', 'georgia', 
          'FlOrIda', 'south   carolina##', 'West virginia?']

def remove_punctuation(value):
    return re.sub('[!#?]', '', value)

clean_ops = [str.strip, remove_punctuation, str.title]

def clean_strings(strings, ops):
    result = []
    for value in strings:
        for function in ops:
            value = function(value)
        result.append(value)
    return result

clean_strings(states, clean_ops)
'''
Out:
['Alabama',
 'Georgia',
 'Georgia',
 'Georgia',
 'Florida',
 'South   Carolina',
 'West Virginia']
'''
```

在数据分析中，还会经常使用匿名函数(anonymous function)。其本身在创建时没有\__name__属性。

```python
anon = lambda x: x * 2
anon(4)
# Out: 8
def apply_to_list(some_list, f):
    return [f(x) for x in some_list]

ints = [4, 0, 1, 5, 6]
apply_to_list(ints, lambda x: x * 2)
# Out: [8, 0, 2, 10, 12]
strings = ['foo', 'card', 'bar', 'aaaa', 'abab']
strings.sort(key=lambda x: len(set(list(x))))
strings
# Out: ['aaaa', 'foo', 'abab', 'bar', 'card']
```

偏函数用于对函数进行局部套用，可以理解为封装。

```python
# functools.partial(func, *args, **keywords)
def add(*args, **kwargs):
    for n in args:
        print(n)
    print("-"*10)
    for k, v in kwargs.items():
       print('%s=%s' % (k, v))

add(1, 2, 3, k1=10, k2=20)
'''
Out:
1
2
3
----------
k1=10
k2=20
'''
from functools import partial
add_partial = partial(add, 10, k1=10, k2=20)
add_partial(1, 2, 3, k3=20)
'''
Out:
10
1
2
3
----------
k1=10
k2=20
k3=20
'''
add_partial(1, k1=0)
'''
Out:
10
1
----------
k1=0
k2=20
'''
```

Python的生成器(generator)在数据科学领域有着广泛的应用，占用计算机资源较小。生成器也可以进行迭代，但与普通的顺序容器不同的是，它不会把所有数据存入内存中，而是只能被读取一次，实时生成数据。

生成器可以通过()构建，也可以使用关键字yield。每次生成器返回一个值时就会被冻结，直到下次调用再返回一个值。

```python
gen = (x for x in range(5))
print(gen)
# Out: <generator object <genexpr> at 0x0000023E97215830>
for item in gen:
    print(item)
'''
Out:
0
1
2
3
4
'''
def createGenerator() :
    mylist = range(3)
    for i in mylist :
        yield i*i

mygenerator = createGenerator()
print(mygenerator)
# Out: <generator object createGenerator at 0x0000023E97215938>
for res in mygenerator:
    print(res)
'''
Out:
0
1
4
'''
mygenerator = createGenerator()
print(next(mygenerator))
# Out: 0
```

生成器可以用来代替列表推导式(list comprehension)。

```python
dict((x, x ** 2) for x in range(5))
# Out: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

标准库itertools提供了许多常用生成器。

```python
import itertools as it
list(it.combinations(range(3), 2))
# Out: [(0, 1), (0, 2), (1, 2)]
list(it.permutations(range(3), 2))
# Out: [(0, 1), (0, 2), (1, 0), (1, 2), (2, 0), (2, 1)]
import itertools
first_letter = lambda x: x[0]
allnames = ['Alan', 'Adam', 'Wes', 'Will', 'Albert', 'Steven']
for letter, names in itertools.groupby(allnames, first_letter):
    print(letter, list(names)) # names is a generator
'''
Out:
A ['Alan', 'Adam']
W ['Wes', 'Will']
A ['Albert']
S ['Steven']
'''
list(it.product(range(2), ['a', 'b'], repeat = 1))
# Out: [(0, 'a'), (0, 'b'), (1, 'a'), (1, 'b')]
```

```python
# ----- Day 5 -----
```

### 异常处理

可以通过try expect语句进行异常抛出。同时可以设置异常类型，还能使用as和Exception。

```python
def attempt_float(x):
    try:
        return float(x)
    except (ValueError, TypeError) as e:
        print(e)
        return x
    except Exception:
        return x
attempt_float('1.234')
# Out: 1.234
attempt_float('1')
# Out: 1.0
attempt_float('1.a')
'''
Out:
could not convert string to float: '1.a'
'1.a'
'''
```

同时还可以使用else和finally。

```python
try:
    f = open(path, 'w')
except:
    print('Not Found')
else:
    try:
        write_to_file(f)
    except:
        print('Failed')
    else:
        print('Succeeded')
    finally:
        f.close()
```

还可以使用raise触发异常。

```python
# raise [Exception [, args [, traceback]]]
def ThorwErr():
    raise Exception("抛出一个异常")
ThorwErr()
```

捕捉到了异常，但是又想重新引发它(传递异常)，可以使用不带参数的raise语句。

```python
class MuffledCalculator:
    muffled = False
    def calc(self, expr):
        try:
            return eval(expr)
        except ZeroDivisionError:
            if self.muffled:
                print('Division by zero is illegal')
            else:
                raise
a = MuffledCalculator()
# a.muffled = True
a.calc('2/0')
```

也可以自定义异常类型，对Exception类进行继承即可。

```python
class ShortInputException(Exception):
    def __init__(self, length, atleast):
        self.length = length
        self.atleast = atleast
try:
    s = input()
    if len(s) < 3:
        raise ShortInputException(len(s), 3)
except ShortInputException as e:
    print('输入长度是%s,长度至少是%s' %(e.length, e.atleast))
else:
    print(s)
# In: ab
# Out: 输入长度是2,长度至少是3
```

### 文件系统

利用open()和close()打开关闭文件，可以设置编码方式，r只读，w只写，x新建只写，a添加，r+读写，b二进制模式，t文本模式。打开后tell()表示当前位置，不同编码tell()效果不同。

```python
path = 'segismundo.txt'
f1 = open(path, 'rb')
lines = (x.rstrip() for x in open(path))
a = f1.read(10)
a.decode(encoding = 'utf-8')
# Out: 'Sueña el '
f2 = open(path)
lines = (x.rstrip() for x in open(path))
a = f2.read(10)
a.encode(encoding = 'gbk').decode('utf-8')
# Out: 'Sueña el r'
print(f1.tell(), f2.tell())
# Out: 10 11
f1.close()
f2.close()
```

也可以用with open读取文件。

```python
with open('segismundo.txt', 'r', encoding='gbk') as f:
    lines = [x.rstrip().encode('cp936').decode('utf-8')\
             for x in open(path)]
lines[0]
# Out: 'Sueña el rico en su riqueza,'
```

文件读取也与系统默认编码有关，可以通过sys和locale库查看系统默认编码和Python默认编码。

```python
import sys
sys.getdefaultencoding()
# Out: 'utf-8'
import locale
locale.getpreferredencoding()
# Out: 'cp936'
# cp936 = gbk
```

seek()和read()分别用来移动到指定位置和读取字符。慎用seek()，因为seek()转移到某个多字节字符中间时进行read()会发生UnicodeDecodeError。

```python
f = open(path, 'r')
f.seek(3)
# Out: 3
f.read(1).encode('gbk').decode('utf-8')
# Out: 'ñ'
```

文件的常用方法还有readlines(), write(), writelines(), flush(), closed。
```python
# ----- Day 6 -----
```



## Numpy库


