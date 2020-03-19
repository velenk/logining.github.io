### 5）

令$Y=X_1/X_2,Z=\sqrt{X_1^2+X_2^2}$

$f_Y(y)=\displaystyle\int_{0}^{\infty} |x|f_{X_1}(xy)f_{X_2}(x)dx=\frac{1}{\pi (1+y^2)}exp\{-\frac{x^2(1+y^2)}{2\sigma^2 }\}\Big{|}_{0}^{\infty}=\frac{1}{\pi (1+y^2)} $

$\displaystyle f_Z(z)=f_{\chi_2^2}((\displaystyle\frac{z}{\sigma})^2)=C\frac{1}{2\Gamma(1)}exp\{-z^2/2\sigma^2 \}= \frac{\sqrt{2}}{\sqrt{\pi}\sigma} exp\{-z^2/2\sigma^2 \}$

当$Y=y,Z=z$时

$|X_1|=z\displaystyle\sqrt{\frac{y^2}{1+y^2}},|X_2|=z\displaystyle\sqrt{\frac{1}{1+y^2}} $

代入正态分布密度函数知

$f(y,z)=\displaystyle\frac{1}{\pi \sigma^2}exp\{-z^2/2\sigma^2\}=f_Y(y)f_Z(z) $

$\therefore $相互独立



### 8.1）

$1-F^n(0.99)=1-0.99^n \geq 0.95 $

$\therefore n\geq \displaystyle\frac{ln 0.05}{ln 0.99}$



### 8.2)

$(X_{(1)},X_{(n)})$的联合密度为

$n(n-1)(F(y)-F(x))^{n-2} p(x)p(y)=n(n-1)(y-x)^{n-2} $

$\therefore R_n $的密度函数为

$\displaystyle\int_{0}^{1-r}n(n-1)r^{n-2}dz=n(n-1)r^{n-2}(1-r),\quad 0<r<1 $



### 8.3)

$\because Z=2n(1-R_n) $

$\therefore f_Z(z)=Cn(n-1)(1-(z/2n))^{n-2}(z/2n)=C(n-1)ze^{-z/2}=\displaystyle\frac{1}{4\Gamma(2)}ze^{-z/2 } $

$\therefore Z\sim \chi_4^2 $



### 16)

$\because \chi^2 $分布的特征函数为

$\phi(t)=(1-2it)^{-m/2} $

$\therefore \phi_{\overline{X}}(t)=(1-2it/n)^{-nm/2} $

满足$\Gamma(nm/2,2/n) $



### 17)

对于$X\sim N(0,1)$

$\because E(X^2)=1,D(X^2)=2 $

$\therefore E(\chi^2)=n,D(\chi^2)=2n $

$\therefore \nu =\sqrt{D(\chi^2)}/E(\chi^2)=\sqrt{\displaystyle\frac{2}{n}} $

$\therefore \beta_2 =\displaystyle\frac{12n^2+48n}{4n^3}-3=\frac{12}{n^2}+\frac{3}{n}-3 $



### 22)

$D(\xi_n)=n/(n-2),\quad n\geq 3 $





