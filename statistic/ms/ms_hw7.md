### 34)

令$T_1=\sum X_i,T_2=\sum Y_i$

$a=\displaystyle\frac{T_1+T_2}{m+n}$是无偏估计

$\sigma^2=\displaystyle\frac{\sum(X_i-a)^2+\sum (Y_i-a)^2/2 }{m+n-1}$是无偏估计

$f(X,Y,\theta)=\displaystyle(\frac{1}{2\pi\sigma^2})^{\frac{n}{2}}(\frac{1}{4\pi\sigma^2})^{\frac{m}{2}}exp\{-\frac{m}{2\sigma^2}(\frac{1}{m}\sum X_i^2 +a^2-2a\overline{X})-\frac{n}{4\sigma^2}(\frac{1}{n}\sum Y_i^2 +a^2-2a\overline{Y}) \}$

存在一一对应，是充分完全统计量

所以是UMVUE



### 35.1)

显然根据定义，服从负二项分布

$T$服从负二项分布

$\therefore P(X=x|T=t)=P(X=x,T=t)/P(T=t)=\displaystyle\frac{\prod\limits_{i=1}^{n-1}\theta (1-\theta)^{x_i} *\theta (1-\theta)^{t-\sum x_i}}{C_{t+n-1}^{n-1}\theta^n(1-\theta)^t}=\frac{1}{C_{t+n-1}^{n-1}} $

是充分统计量

用因子分解定理

$f(x,\theta)= \theta^n(1-\theta)^t$

是充分统计量

其自然参数空间有内点，是完全统计量



### 35.2)

$E_\theta T=\sum kP(X=k)=n(1-\theta)/\theta $

$\therefore \hat\theta^{-1}=(t+n)/n $

$\therefore \hat\theta^{-1} $是UMVUE



### 35.3)

$\because E(\phi )=\theta$

是无偏估计

$E_\theta (\phi(X_1)|T=t)=n/t $

$\therefore \hat\theta =n/t $

是UMVUE