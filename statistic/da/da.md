# Data Analysis

### Velen Kong



## 摘要

基于Python的数据分析入门笔记，希望能自学掌握基本的数据分析能力，毕竟是统计学的基础之一。

内容安排主要参考

(美) Wes McKinney 著. Python for Data Analysis:2nd Edition [M] USA: O'Reilly Media 2017

该书作者同时也是pandas库的作者，同时借用其在GitHub上的数据资料。



## 第三方库与Python入门



### IPython \& Jupyter

用到的库：ipython，jupyter。

jupyter确实好用，主要扩展了$Tab,?,*$的功能。

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



### Python基础

#注释。

所有变量都是对象(object)。

基本的函数调用，利用函数批量处理。

变量赋值类似引用(reference)。

动态类型，利用type()和isinstance()进行类型检查。后者可以传入tuple代替逻辑或操作。

print配合format输出。

Python中的object拥有各自的属性(attributes)和方法(methods)，可通过getattr, hasattr, setattr操作。其中getattr可以直接使用返回对象，setattr不改变原class。



### Numpy库


