### 28)

因为对于正态分布，矩估计都是连续可导的

而$g(\theta)$在$\theta=0$处不可导

所以没有无偏估计



### 30)

显然是无偏估计，下证UMVUE

$\because E\delta(T)=\displaystyle\int_{-\infty}^{\infty}\delta(t)\frac{1}{\sqrt{2\pi}\sigma}exp\{-\frac{(t-a)^2}{2\sigma^2}\}dt=0 $

$\therefore \displaystyle\int_{-\infty}^{\infty}\delta(t)exp\{-\frac{(t-a)^2}{2\sigma^2}\}dt=0 $

$\therefore \displaystyle\int_{-\infty}^{\infty}\delta(t)exp\{-\frac{(t-a)^2}{2\sigma^2}\}*ln\frac{-(t-a)^2}{2\sigma^2}*\frac{4(t-a)^2}{\sigma^3}dt=0 $

$\therefore E(h(T)\delta(T))=0 $



### 31.1)

$f(X,\sigma^2)=\displaystyle(\frac{1}{2\pi\sigma^2})^{\frac{n}{2}}exp\{-\frac{1}{2\sigma^2}\sum X_i^2\}$

$\therefore S^2=\displaystyle\frac{1}{n-1}\sum X_i^2 $存在一一对应，是充分完全统计量



### 31.2)

令$\hat\sigma^2=\displaystyle\frac{1}{n-1}\sum X_i^2$

由30题知是UMVUE

$\therefore \hat\sigma=\sqrt{\displaystyle\frac{1}{n-1}\sum X_i^2} $

$\therefore 3\hat\sigma^4=3(\displaystyle\frac{1}{n-1}\sum X_i^2)^2 $