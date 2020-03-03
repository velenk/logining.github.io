### 5.1)

$\because X\sim b(1,p)$

$\therefore $样本空间为$X=(x_1,x_2,x_3,x_4,x_5),\qquad x_i=0,1$

$\therefore P(X=(x_1,x_2,x_3,x_4,x_5))=p^{\sum x_i}(1-p)^{5-\sum x_i}$



### 5.2)

统计量不含未知参数

$\therefore X_1+X_2,~ min~X_i$是统计量，其他不是



### 5.3)

​	$F_n(x)$

$=0,\qquad \qquad x<0$

$=\displaystyle\frac{n-m}{n},\quad 0\leq x<1$

$=1,\qquad \qquad x\geq 1$



### 6)

$\because \displaystyle\overline{x}=\frac{\sum x_i}{n}$

$\therefore \displaystyle\overline{y}=\frac{\sum y_i}{n}=\frac{\sum (ax_i+b)}{n}=a\overline{x}+b$

$\because \displaystyle S_x^2=\frac{\sum (x_i-\overline{x})^2}{n-1}$

$\therefore \displaystyle S_y^2=\frac{\sum (y_i-\overline{y})^2}{n-1}=\frac{\sum (ax_i-a\overline{x})^2}{n-1}=a^2S_x^2$

计算得$\overline{y}=540,\quad S_y^2=2100$



### 1.1)

$\because \overline{X}\sim N(20,0.9),\quad \overline{Y}\sim N(20,0.6)$

由于相互独立

$\therefore \overline{X}-\overline{Y}\sim N(0,1.5)$

$\therefore P= 2(1-\phi (\frac{0.3}{\sqrt{1.5}}))$

查表即可



### 1.2)

$\because (n-1)S^2\sim \sigma^2 \chi^2_{n-1}$

$\therefore 9S_X^2+14S_Y^2\sim 9(\chi_9^2+\chi_{14}^2)\sim 9(\chi_{23}^2)$

$\therefore P=(\chi_{23}^2)^{-1}(\frac{164}{9})$

查表即可



### 14)

令$X_i'= X_i/\sigma_i$

则$X_i'\sim N(0,1)$

$\therefore \xi =\displaystyle\sum\limits_{i}(\frac{X_i}{\sigma_i}-\frac{Z}{\sigma_i})^2=\sum\limits_i (\frac{X_i}{\sigma_i})^2-Z^2\sum\limits_i \frac{1}{\sigma_i^2}$

令$A=\begin{pmatrix} \displaystyle\frac{1}{\sigma_1}\frac{1}{\sqrt{\sum\frac{1}{\sigma_i^2}}} & \ldots & \displaystyle\frac{1}{\sigma_n}\frac{1}{\sqrt{\sum\frac{1}{\sigma_i^2}}} \\ a_{21} & & a_{2n} \\  \ldots   &  & \ldots \\ a_{n1} & & a_{nn} \end{pmatrix}$

$Y=AX'$

$\displaystyle\therefore Y_1=\sqrt{\sum\frac{1}{\sigma_i^2}} Z,\quad Y_i \sim N(0,1),~i\neq 1$

$\because A$是正交矩阵

$\therefore \displaystyle\xi =\sum\limits_{i=1}^n X_i'^2-Y_1^2=\sum\limits_{i=2}^n Y_i^2 \sim \chi_{n-1}^2$



