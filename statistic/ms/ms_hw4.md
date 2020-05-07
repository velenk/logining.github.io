### 43)

$T$服从负二项分布

$\therefore P(X=x|T=t)=P(X=x,T=t)/P(T=t)=\displaystyle\frac{\prod\limits_{i=1}^{n-1}\theta (1-\theta)^{x_i} *\theta (1-\theta)^{t-\sum x_i}}{C_{t+n-1}^{n-1}\theta^n(1-\theta)^t}=\frac{1}{C_{t+n-1}^{n-1}} $

是充分统计量

用因子分解定理

$f(x,\theta)= \theta^n(1-\theta)^t$

是充分统计量



### 47)

$f(X,Y,\theta)=\displaystyle(\frac{1}{2\pi\sigma^2})^{\frac{n+m}{2}}exp\{-\frac{m}{2\sigma^2}(\frac{1}{m}\sum X_i^2 +a^2-2a\overline{X})-\frac{n}{2\sigma^2}(\frac{1}{n}\sum Y_i^2 +b^2-2b\overline{Y}) \}$

$\therefore S^2=\frac{1}{m+n-2}(\sum X_i^2 -m\overline{X}+\sum Y_i^2-n\overline{Y}) $

存在一一对应，是充分完全统计量



### 49)

$f(x,\theta)=e^{-\sum x}e^{n\theta}I(X_{(1)}>\theta)$

由因子分解定理，是充分统计量

其自然参数空间有内点，是完全统计量