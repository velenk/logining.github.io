### 1)

由最小二乘解的几何意义知

$r=b-Ax$是与$span(A)$垂直的向量

所以$r$具有唯一性，即$Ax_1=Ax_2$



### 2)

$\sum ||Ax-b_i||^2_2=\sum (Ax-b_i)·(Ax-b_i)=\sum\limits_j\sum\limits_i ((Ax)_i-b_{ji})^2=\sum\limits_i\sum\limits_j ((Ax)_i-b_{ji})^2 $

由于$(Ax)_i$各自独立，要使其最小，则$\sum\limits_j ((Ax)_i-b_{ji})^2$最小

所以$(Ax)_i=\frac{1}{r}\sum\limits_j b_{ji}$

得$Ax=\frac{1}{r}\sum\limits_i b_i$



### 3)

$\because \alpha =(X^TX)^{-1}X^TY $

$\therefore $ 此时最小二乘解具有唯一性

而Lagrange插值在这种情况下的平方和为0，是最小二乘解

由唯一性，得证



### 4)

利用python进行编程计算

```python
import numpy as np
x = np.array([-3, -2, -1, 0, 1, 2, 3])
y = np.array([4, 2, 3, 0, -1, -2, -5])
Y = np.array([y]).T
x0 = np.zeros(7, int) + 1
x2 = x**2
A = np.array([x0, x, x2])
A = A.T
print(np.linalg.inv(A.T.dot(A)).dot(A.T).dot(Y))
'''
Out:
[[ 0.66666667]
 [-1.39285714]
 [-0.13095238]]
'''
```

所以$a_0=0.667,a_1=-1.393,a_2=-0.131 $



### 5)

利用python进行编程计算

```python
import numpy as np
x = np.array([1.02, 0.95, 0.87, 0.77, 0.67, 0.56, 0.44, 0.3, 0.16, 0.01])
y = np.array([0.39, 0.32, 0.27, 0.22, 0.18, 0.15, 0.13, 0.12, 0.13, 0.15])
Z = np.array([x**2]).T
x1 = y**2
x2 = x*y
x3 = x
x4 = y
x5 = np.zeros(10, int) + 1
A = np.array([x1, x2, x3, x4, x5]).T
print(np.linalg.inv(A.T.dot(A)).dot(A.T).dot(Z))
'''
Out:
[[-2.63562548]
 [ 0.14364618]
 [ 0.55144696]
 [ 3.22294034]
 [-0.43289427]]
'''
```

所以$a=-2.636, b=0.144, c=0.551, d=3.223, e=-0.433 $





