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

and和or运算。注意Python没有位运算操作符，&, |, ~都是逻辑运算。

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



## NumPy库



### N维数组

numpy库全称Numerical Python，专用于科学计算，由于底层C语言的实现，速度比纯python快几十倍。rand()返回[0, 1)上的均匀分布，randn()返回标准正态分布。

```python
import numpy as np
data = np.random.randn(2, 3)
data
'''
Out:
array([[-0.97835473,  0.41601724, -0.75555622],
       [ 1.90504659,  0.22870654, -0.45414597]])
'''
```

可以直接对数组进行数学运算。shape()和dtype()可以查看数组信息。

```python
data * 10
'''
Out:
array([[-9.7835,  4.1602, -7.5556],
       [19.0505,  2.2871, -4.5415]])
'''
data + data
'''
Out:
array([[-1.9567,  0.832 , -1.5111],
       [ 3.8101,  0.4574, -0.9083]])
'''
data.shape
# Out: (2, 3)
data.dtype
# Out: dtype('float64')
```

array()方法可以将传入参数转化为数组，而如果参数是数组那么会产生一个副本，而使用asarray()会直接返回传入的数组。

用ndim返回第一维的维数。

```python
data1 = [[1, 2, 3], [2, 4, 6]]
arr1 = np.array(data1)
arr1.ndim
# Out: 2
```

zeros(), ones(), zeros_like(), ones_like(), full(), full_like()用来创建新数组。

最好不要使用没有初始化的empty()。

arange()创建一个一维顺序数组。

eye()和identity()用来创建单位矩阵。

默认数据类型均为float64。

通过设定dtype参数改变数据类型。

```python
arr2 = np.identity(3)
arr2
'''
Out:
array([[1., 0., 0.],
       [0., 1., 0.],
       [0., 0., 1.]])
'''
arr3 = np.full_like(arr2, 3, dtype=np.int32)
arr3
'''
Out:
array([[3, 3, 3],
       [3, 3, 3],
       [3, 3, 3]])
'''
```

numpy支持的数据类型有：

int8, uint8, int16, uint16, int64, uint64;

float16, float32, float64, float128;

complex64, complex128, complex256;

bool, object, string_, unicode\_。

缩写为i1, u1, i2, u2, i4, u4, i8, u8;

f2, f4 or f, f8 or d, f16 or g;

c8, c16, c21;

?, 0, S, U。

对于非数学类型最好使用pandas。

astype()可以进行类型转换，调用时总会创建一个新的array。

```python
arr4 = arr3.astype('f8')
arr4
'''
Out:
array([[3., 3., 3.],
       [3., 3., 3.],
       [3., 3., 3.]])
'''
```

除了array相互加减乘之外，numpy还支持常数乘除法和指数运算。

对size相同的array使用不等号还可以返回一个bool类型的数组。

```python
arr5 = np.random.randn(2, 3)
arr6 = 1 / arr5
arr6 < arr5
'''
Out:
array([[False, False, False],
       [ True,  True, False]])
'''
```

和list类似，array可以使用[begin1: end1, begin2: end2, ... ]来获得子数组。注意获得子数组并未新建，利用copy()来获得副本。

```python
arr0 = np.array([[1, 2, 3], 
                 [4, 5, 6], 
                 [7, 8, 9]])
arr7 = arr0[0]
arr7
# Out: array([1, 2, 3])
arr7[:] = 0
arr0
'''
Out:
array([[0, 0, 0],
       [4, 5, 6],
       [7, 8, 9]])
'''
arr8 = arr0[1:3, :2].copy()
arr8
'''
Out:
array([[4, 5],
       [7, 8]])
'''
```

```python
# ----- Day 7 -----
```

除了基本索引之外，还可以使用布尔索引，但要保证维数相同，Python并不会报错。也可以两者结合使用。

```python
import numpy as np
names = np.array(['A', 'B', 'A', 'C'])
data = np.eye(4, dtype='i4')
names == 'A'
# Out: array([ True, False,  True, False])
data[names == 'A']
'''
Out:
array([[1, 0, 0, 0],
       [0, 0, 1, 0]])
'''
data[names == 'A', :2]
'''
Out:
array([[1, 0],
       [0, 0]])
'''
data[~((names == 'A') | (names == 'C')), 2:]
# Out: array([[1, 0, 0]])
```

也可以利用逻辑表达式来改变array的内容。

```python
data[data > 0] = -1
data
'''
Out:
array([[-1,  0,  0,  0],
       [ 0, -1,  0,  0],
       [ 0,  0, -1,  0],
       [ 0,  0,  0, -1]])
'''
data[names != 'A'] = 1
data
'''
Out:
array([[-1,  0,  0,  0],
       [ 1,  1,  1,  1],
       [ 0,  0, -1,  0],
       [ 1,  1,  1,  1]])
'''
```

花式索引(fancy index)是一种智能索引。通过传递索引数组来一次获得多个元素。

```python
arr = np.zeros((8, 4))
for i in range(8):
    arr[i] = i
arr[[4, 3, -1]]
'''
Out:
array([[4., 4., 4., 4.],
       [3., 3., 3., 3.],
       [7., 7., 7., 7.]])
'''
arr = np.arange(20).reshape(5, 4) + 1
arr
'''
Out:
array([[ 1,  2,  3,  4],
       [ 5,  6,  7,  8],
       [ 9, 10, 11, 12],
       [13, 14, 15, 16],
       [17, 18, 19, 20]])
'''
arr[[1, 2, -1], [3, 0, -1]]
# Out: array([ 8,  9, 20])
```

也可以多重嵌套fancy index。

```python
arr[[1, 2]]
'''
Out:
array([[ 5,  6,  7,  8],
       [ 9, 10, 11, 12]])
'''
arr[[1, 2]][:, [1, 0]]
'''
Out:
array([[ 6,  5],
       [10,  9]])
'''
```

可用dot()来计算array的点积。T获得转置，也可以使用transpose()，高维建议使用后者，前者相当于整个array倒置。swapaxes()则能交换两个维度。

```python
arr = np.arange(24).reshape((2, 4, 3)) +1
arr
'''
Out:
array([[[ 1,  2,  3],
        [ 4,  5,  6],
        [ 7,  8,  9],
        [10, 11, 12]],

       [[13, 14, 15],
        [16, 17, 18],
        [19, 20, 21],
        [22, 23, 24]]])
'''
arr.T
'''
Out:
array([[[ 1, 13],
        [ 4, 16],
        [ 7, 19],
        [10, 22]],

       [[ 2, 14],
        [ 5, 17],
        [ 8, 20],
        [11, 23]],

       [[ 3, 15],
        [ 6, 18],
        [ 9, 21],
        [12, 24]]])
'''
arr.transpose((1, 0, 2))
'''
Out:
array([[[ 1,  2,  3],
        [13, 14, 15]],

       [[ 4,  5,  6],
        [16, 17, 18]],

       [[ 7,  8,  9],
        [19, 20, 21]],

       [[10, 11, 12],
        [22, 23, 24]]])
'''
arr.swapaxes(0, 1)
'''
Out:
array([[[ 1,  2,  3],
        [13, 14, 15]],

       [[ 4,  5,  6],
        [16, 17, 18]],

       [[ 7,  8,  9],
        [19, 20, 21]],

       [[10, 11, 12],
        [22, 23, 24]]])
'''
```

```python
# ----- Day 8 -----
```

### 通用函数

array有许多通用函数都可以使用，比如sqrt, exp等。常用的函数有：

abs, fabs;

sqrt, square, exp, expm1, log, log10, log2, log1p;

其中expm1相当于exp(x)-1，与log1p相当于ln(x+1)互逆，常用来数据预处理，比如求RMSLE(均方根对数误差)。

sign, ceil, floor, rint, modf;

分别是符号函数，和四个取整函数(返回float)，其中modf会返回两个数组。

```python
arr = np.random.randn(3) * 5
arr
# Out: array([1.40907511, 4.3517101 , 2.37764427])
remainded, whole_part = np.modf(arr)
remainded
# Out: array([0.40907511, 0.3517101 , 0.37764427])
whole_part
# Out: array([1., 4., 2.])
np.ceil(whole_part)
whole_part
# Out: array([1., 4., 2.])
```

isnan, isfinite, isinf;

注意nan不能使用==来判断，而且会被同时当作极大和极小。

```python
np.nan == np.nan
# Out: False
np.nan is np.nan
# Out: True
import math
math.nan is np.nan
# Out: False
np.isnan(math.nan)
# Out: True
```

cos, cosh, sin, sinh, tan, tanh, arccos, arccosh, arcsin, arcsinh, arctan, arctanh;

logical_not(等价于~array);

还有一些带有两个参数的通用函数：

add(), subtract(), multiply(), divide(), floor_divide(), power();

这些函数可以接受单个值也可以接受array。

```python
arrd = np.divide(arr, 2)
arrd
# Out: array([0.70453755, 2.17585505, 1.18882213])
arrd = np.divide(arr, whole_part)
arrd
# Out: array([1.40907511, 1.08792752, 1.18882213])
arrp = np.power(arr, 2)
arrp
# Out: array([ 1.98549266, 18.93738078,  5.65319227])
arrp = np.power(arr, remainded)
arrp
# Out: array([1.15060233, 1.67734792, 1.38691458])
```

maximum, fmax, minimum, fmin;

其中fmax和fmin无视NaN。

```python
arr0 = np.array([np.nan, 1, 3, 1])
arr1 = np.array([2, 1, 1, 1])
print(np.maximum(arr0, arr1))
# Out: [nan  1.  3.  1.]
print(np.fmax(arr0, arr1))
# Out: [2. 1. 3. 1.]
```

copysign();

greater(), greater_equal(), less(), less_equal(), equal(), not_equal();

等价于不等号判断，返回boolean数组。

logical_and(), logical_or(), logical_xor();

等价于$\&,|,\hat{} $。

```python
# ----- Day 9 -----
```



### 面向数组编程

NumPy提供了许多面向数组的函数和方法，能更快速地对array进行操作。

比如当我们需要网格点时，可以利用meshgrid()对x, y坐标数组做笛卡儿积。

```python
points = np.arange(-5, 5, 1)
plt.plot(points, points, 'r')
plt.show()
```

![img](data:image/png;base64,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)

```python
xs, ys = np.meshgrid(points, points)
plt.plot(xs, ys, 'o')
plt.show()
```

![img](data:image/png;base64,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)

```python
z = np.sqrt(xs**2 + ys**2)
plt.imshow(z, cmap=plt.cm.gray)
plt.colorbar()
plt.title('Image plot of $\sqrt{x^2 + y^2}$\
for a grid of values')
plt.show()
```

![img](data:image/png;base64,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)

where()是一个三元函数，用来进行类似if else的操作，需要传入一个boolean数组和两个其他数组。也可以传入值。

```python
xarr = [1, 2, 3]
yarr = [-1, -2, -3]
cond = [True, False, True]
result = np.where(cond, xarr, yarr)
result
# Out: array([ 1, -2,  3])
arr = np.random.randn(3, 3)
np.where(arr > 0, 1, arr)
'''
Out:
array([[ 1.        ,  1.        , -0.49359797],
       [ 1.        , -1.88837102, -1.03168442],
       [-0.04999441, -1.3569411 ,  1.        ]])
'''
```

NumPy还自带了很多数学函数。比如mean()和sum()，可以使用axis来控制计算的维度，axis=0即表示将除了0号维度之外全部相同的元素进行计算，从而消去0号维度。

```python
arr.mean()
# Out: -0.04499350890122711
np.sum(arr)
# Out: -0.404941580111044
arr.sum(axis=0)
# Out: array([ 2.13961385, -1.55606646, -0.98848896])
arr = np.ones((2, 3, 4))
arr.sum(axis=0)
'''
Out:
array([[2., 2., 2., 2.],
       [2., 2., 2., 2.],
       [2., 2., 2., 2.]])
'''
```

还有累加和累乘，cumsum(), cumprod()，也可以用axis控制维度。如果不控制纬度则会顺序遍历返回一个一维数组。

```python
arr.cumsum(axis = 1)
'''
Out:
array([[[1., 1., 1., 1.],
        [2., 2., 2., 2.],
        [3., 3., 3., 3.]],

       [[1., 1., 1., 1.],
        [2., 2., 2., 2.],
        [3., 3., 3., 3.]]])
'''
```

除此以外还有var(), std(), argmin(), argmax()等函数。其中后两者返回最值第一次出现的位置。

```python
# ----- Day 10 -----
```

boolean数组也可以执行sum()，同时还有any(), all()来进行整体与或。这也能用在其他array中。

array还可以执行sort()，利用axis参数将给定维度坐标不同，其余坐标相同的元素排序。

```python
arr = np.random.randn(3, 3, 3) *5
arr = np.ceil(arr)
arr
'''
Out:
array([[[ -3.,  -0.,  -0.],
        [  5.,   8.,  -3.],
        [  1.,   1.,   5.]],

       [[  5.,   4.,  -3.],
        [ -1.,   2.,   1.],
        [ -2.,  -6.,  -8.]],

       [[ -1.,   6.,   6.],
        [  3.,  -4.,   6.],
        [  3., -11.,  -0.]]])
'''
arr.sort(axis=1)
arr
'''
Out:
array([[[ -3.,  -0.,  -3.],
        [  1.,   1.,  -0.],
        [  5.,   8.,   5.]],

       [[ -2.,  -6.,  -8.],
        [ -1.,   2.,  -3.],
        [  5.,   4.,   1.]],

       [[ -1., -11.,  -0.],
        [  3.,  -4.,   6.],
        [  3.,   6.,   6.]]])
'''
```

利用sort()可以很方便地计算q分位数。

```python
arr = np.random.randn(1000)
arr.sort()
arr[int(0.05 * len(arr))]
# Out: -1.5488900316485399
```

另外还有一些常用函数：

unique(x), intersect1d(x, y), union1d(x, y), in1d(x, y), setdiff1d(x, y), setxor1d(x, y)。

其中intersect1d等返回的都是一维值数组。in1d()返回一个一维的boolean数组。

```python
arr1 = np.array([[3, 4, 5],
                 [4, 2, 3],
                 [5, 3, 5]])
arr2 = np.array([[1, 2, 5],
                 [3, 4, 3],
                 [5, 3, 5]])
np.unique(arr1)
# Out: array([0, 2, 3, 4, 5])
np.union1d(arr1, arr2)
# Out: array([0, 1, 2, 3, 4, 5])
np.in1d(arr1, arr2)
# Out: array([ True,  True,  True,  True,  True,  True,  True,  True, False])
np.setdiff1d(arr1, arr2)
# Out: array([0])
```



### 文件读写

NumPy拥有自己的文件读写函数。

通过save(), load(), savez(), savez_compressed()可以进行基本的读写。其中savez类似于dict，而compressed进行了压缩。

```python
arr = np.arange(5)
np.save('some_array', arr)
np.load('some_array.npy')
np.savez('array_archive.npz', a=arr, b=arr)
arch = np.load('array_archive.npz')
arch['b']
# Out: array([0, 1, 2, 3, 4, 5])
np.savez_compressed('arrays_compressed.npz', a=arr, b=arr)
```

```python
# ----- Day 11 -----
```



### 线性代数

在NumPy中，$*$并不能进行矩阵乘法，而是单纯地将各个位置上的元素相乘。进行点乘需要使用dot()。

```python
x = np.array([[2, 3],
              [0, 1]])
y = np.array([[0, 1],
              [1, 0]])
x * y
'''
Out:
array([[0, 3],
       [0, 0]])
'''
x.dot(y)
'''
Out:
array([[3, 2],
       [1, 0]])
'''
```

另外，在点乘中一个二维矩阵和一个一维数组相乘，后者会被转化成向量，并返回一个一维数组。这个操作也可以用运算符$@$实现。

```python
x.dot(np.array([1, 2]))
# Out: array([8, 2])
x @ np.array([2, 1])
# Out: array([7, 1])
```

numpy.linalg拥有许多常用函数，比如inv(), qr()用来获得逆矩阵和QR分解。

```python
from numpy.linalg import inv, qr
x_ = inv(x)
x_
'''
Out:
array([[ 0.5, -1.5],
       [ 0. ,  1. ]])
'''
mat = np.random.randn(3, 3)
q, r = qr(mat)
r
'''
Out:
array([[ 0.79869179,  1.18877944,  0.19382584],
       [ 0.        , -2.24303773,  0.08872422],
       [ 0.        ,  0.        ,  0.86608074]])
'''
```

trace()获得矩阵的迹，而diag()对于二维矩阵可以获取对角线元素，对于一维数组则会创建对应的对角阵。

```python
x.trace()
# Out: 3
np.diag(x)
# Out: array([2, 1])
np.diag(np.diag(x))
'''
Out:
array([[2, 0],
       [0, 1]])
'''
```

linalg.det()用来计算array的行列式，但要求最后两个维度大小相同。

linalg.eig()用来计算矩阵的特征值和特征向量。

```python
from numpy.linalg import eig
w, v = eig(np.diag((1, 2, 3)))
w
# Out: array([1., 2., 3.])
v
'''
Out:
array([[1., 0., 0.],
       [0., 1., 0.],
       [0., 0., 1.]])
'''
```

linalg.pinv()用来计算Moore-Penrose广义逆矩阵。

linalg.svd()对矩阵进行奇异值分解，返回三个分解矩阵。

linalg.solve()解线性方程组。

linalg.lstsq()求最小二乘解，返回解向量，残差和，秩，奇异值。

```python
x = np.array([[1, 2, 1],
              [1, 0, 0],
              [0, 4, 0]])
pinv(x)
'''
Out:
array([[ 2.06415723e-16,  1.00000000e+00, -2.86157572e-16],
       [ 1.18467981e-16, -1.07459905e-16,  2.50000000e-01],
       [ 1.00000000e+00, -1.00000000e+00, -5.00000000e-01]])
'''
svd(x)
'''
Out:
(array([[-0.4856289 , -0.70136375, -0.52177912],
        [-0.02497309, -0.58551396,  0.81027757],
        [-0.87380828,  0.40652464,  0.26682728]]),
 array([4.52173541, 1.48251813, 0.59669834]),
 array([[-0.11292169, -0.98778246, -0.10739879],
        [-0.86803506,  0.15067004, -0.4730895 ],
        [ 0.48349129,  0.03980385, -0.87444373]]))
'''
solve(x, np.array([1, 1, 1]))
# Out: array([ 1.  ,  0.25, -0.5 ])
x = np.array([[1, 2],
              [1, 0],
              [0, 4]])
lstsq(x, np.array([1, 1, 1]), rcond=None)
'''
Out:
(array([0.77777778, 0.22222222]),
 array([0.11111111]),
 2,
 array([4.49661478, 1.33433712]))
'''
```

```python
# ----- Day 12 -----
```



### 伪随机数的产生

NumPy有许多的随机数生成器，比如可以用normal()来生成正态分布。

```python
sample = np.random.normal(size=(3, 3))
```

通过normal()生成的一系列随机数速度很快，比逐个生成要快很多。

```python
from random import normalvariate
N = 1000000
%timeit samples = [normalvariate(0, 1) for _ in range(N)]
%timeit np.random.normal(size=N)
'''
Out:
882 ms ± 24.3 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)
38.1 ms ± 449 µs per loop (mean ± std. dev. of 7 runs, 10 loops each)
'''
```

另外可以通过seed()改变随机种子，RandomState()来创建局部随机生成器。

```python
np.random.seed(123)
sample = np.random.RandomState(123)
sample.randn(5)
# Out: array([-1.0856306 ,  0.99734545,  0.2829785 , -1.50629471, -0.57860025])
```

permutation()和shuffle()都可以用来打乱array，多维数组则只打乱第一维。

但前者还能传入int，相当于随机打乱arange()。而且前者返回一个打乱后的副本，后者会直接改变array并且返回None。

```python
sample = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])
np.random.permutation(sample)
'''
Out:
array([[4, 5, 6],
       [7, 8, 9],
       [1, 2, 3]])
'''
sample
'''
Out:
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
'''
np.random.shuffle(sample)
sample
'''
Out:
array([[4, 5, 6],
       [1, 2, 3],
       [7, 8, 9]])
'''
sample = np.random.permutation(5)
sample
# Out: array([0, 4, 2, 3, 1])
```

rand()返回$[0,1)$上的均匀随机变量。而randint()得到$[0,low)$或者$[low, high)$的随机整数。randn返回标准正态随机变量。

还有一些常见的分布函数如下：

```python
# uniform(low=0.0, high=1.0, size=None)
# 均匀分布
# binomial(n, p, size=None)
# 二项分布
# negative_binomial(n, p, size=None)
# 负二项分布
# multinomial(n, pvals, size=None)
# 多项分布
# normal(loc=0.0, scale=1.0, size=None)
# 正态分布
# standard_normal(size=None)
# 标准正态分布
# lognormal(mean=0.0, sigma=1.0, size=None)
# 对数正态分布
# multivariate_normal(mean, cov[, size, check_valid, tol])
# 多元正态分布
# wald(mean, scale, size=None)
# 逆高斯分布
# poisson(lam=1.0, size=None)
# 泊松分布
# exponential(scale=1.0, size=None)
# 指数分布
# standard_exponential(size=None)
# 标准指数分布
# beta(a, b, size=None)
# β分布
# gamma(shape, scale=1.0, size=None)
# Γ分布
# standard_gamma(shape, size=None)
# 标准Γ分布
# chisquare(df, size=None)
# 卡方分布
# standard_t(df, size=None)
# 标准t分布
# f(dfnum, dfden, size=None)
# F分布
# noncentral_chisquare(df, nonc, size=None)
# 非中心卡方分布
# noncentral_f(dfnum, dfden, nonc, size=None)
# 非中心F分布
# geometric(p, size=None)
# 几何分布
# hypergeometric(ngood, nbad, nsample, size=None)
# 超几何分布
# pareto(a, size=None)
# 帕累托分布
# dirichlet(alpha, size=None)
# 狄利克雷分布
# gumbel(loc=0.0, scale=1.0, size=None)
# Gumbel分布(极值分布)
# laplace(loc=0.0, scale=1.0, size=None)
# 拉普拉斯分布
# logistic(loc=0.0, scale=1.0, size=None)
# Logistic分布
# rayleigh(scale=1.0, size=None)
# 瑞利分布
# standard_cauchy(size=None)
# 标准柯西分布
# triangular(left, mode, right, size=None)
# 三角分布
# weibull(a, size=None)
# 韦布尔分布
# zipf(a, size=None)
# ζ分布
```

```python
# ----- Day 13 -----
```



### 样例：随机游动



## Pandas库