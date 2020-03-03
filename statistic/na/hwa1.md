### 1.1)

绝对误差界$5*10^{-5}$

相对误差界$1.176*10^{-3}$

有效数字$3$位



### 1.2)

绝对误差界$5*10^{-5}$

相对误差界$1.245*10^{-4}$

有效数字$4$位



### 1.3)

绝对误差界$5*10^{-3}$

相对误差界$1.538*10^{-4}$

有效数字$4$位



### 1.4)

绝对误差界$5*10^{-1}$

相对误差界$1.25*10^{-4}$

有效数字$4$位



### 2.1)

由

$arctan(A)-arctan(B)=arctan(A-B)/(1+AB)$

可知

$arctan(x+1)-arctan(x)=\displaystyle\frac{\pi}{4}\frac{1}{(x^2+x+1)}$



### 2.2)

$ln(x-\sqrt{x^2-1})=ln(\displaystyle\frac{1}{x+\sqrt{x^2-1}})=-ln(x+\sqrt{x^2-1})$



### 2.3)

$\displaystyle\frac{sinx}{x-\sqrt{x^2-1}}=(x+\sqrt{x^2-1})sin(x-2k\pi)$

再对$sinx$进行Taylor展开计算最终结果



### 3)

$dcos(\phi)=-sin(\phi)d\phi =-sin(\phi)\delta $

所以

$e_r^*=\displaystyle\frac{dcos(\phi)}{cos(\phi)}=-\frac{sin(\phi)}{cos(\phi)}\delta $



### 4)

先进行变形

$a+\sqrt{a^2+b^2}=b^2/(2a^2+b^2)$

再利用python进行编程计算

```python
a = -12345678987654321
b = 123
(b**2)/((a**2 + b**2)**0.5 - a)
# Out: 6.12724501225449e-13
```

或者使用MATLAB

```matlab
a = -12345678987654321
b = 123
(b*b)/(sqrt(a*a + b*b) - a)
%{
Out:

...

ans =

   6.1272e-13

%}
```

所以结果为$6.127*10^{-13}$



### 5)

对于方程$x^2+9^{12}x-3=0$，易知两根为实根，且求根公式为

$x_1=\displaystyle\frac{-b+\sqrt{b^2-4ac}}{2a},\qquad x_2=\displaystyle\frac{-b-\sqrt{b^2-4ac}}{2a}$

但由于$b>0$且$b^2>>4ac$，导致$-b+\sqrt{b^2-4ac}\to 0$，从而产生误差

因而改用下列公式计算

$x_1=\displaystyle\frac{2c}{-b-\sqrt{b^2-4ac}},\qquad x_2=\displaystyle\frac{-b-\sqrt{b^2-4ac}}{2a}$

python程序如下

```python
a = 1
b = 9**12
c = -3
ans = -b - (b**2 - 4*a*c)**0.5
x1 = 2*c/ans
x2 = ans/2/a
print(x1)
print(x2)
'''
Out:
1.062211848441645e-11
-282429536481.0
'''
```

或者使用MATLAB

```matlab
a = 1
b = power(9,12)
c = -3
ans = -b - sqrt(b*b - 4*a*c)
x1 = 2*c/ans
x2 = ans/2/a
%{
Out:

...

x1 =

   1.0622e-11


x2 =

  -2.8243e+11

%}
```

保留四位有效数字后得到

$x_1=1.062*10^{-11},\quad x_2=-2.824*10^{11}$



### 6)

编写python程序，利用秦九韶算法计算得

```python
sig = 1
x = 1.00001
ans = -1
for i in range(99):
    ans = x * ans + sig
    sig *= -1
ans
# Out: -0.0005002450796476321
```

或者使用MATLAB

```matlab
sig = 1
x = 1.00001
ans = -1
for i = 0:98
    ans = x * ans + sig
    sig = -sig
end
ans
%{
Out:

...

ans =

  -5.0025e-04

%}
```

因为

$P(x)=1-x+x^2-\ldots +x^{98}-x^{99}=(1-x)(1+x^2+\ldots +x^{98})=(1-x)\displaystyle\frac{1-x^{100}}{1-x^2}$

所以可进行编程计算

```python
(1-x)*(1-x**100)/(1-x**2) - ans
# Out: 3.782781379801925e-16
```

得到结果误差约为$3.783*10^{-16}$

