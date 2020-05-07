### 53)

由于正态分布是指数族，自然参数空间有内点

所以$\overline{X}$是充分完全统计量

令$Y_i=X_i-a$，得极差分布与$a$无关

所以$\overline{X},X_{(n)}-X_{(1)}$相独立



### 1)

利用下面的引理

$f(y_1,\ldots,y_k)$在$(c_1,\ldots,c_k)$处连续，若$y_{n1}\stackrel{a.s.}{\longrightarrow}c_1,\ldots,y_{nk}\stackrel{a.s.}{\longrightarrow}c_k$，则$f(y_1,\ldots,y_k)\stackrel{a.s.}{\longrightarrow}f(c_1,\ldots,c_k)$

可以证明样本的k阶中心矩是总体k阶中心矩的强相合估计

所以$S^2$是$\sigma^2$的强相合估计

且由于$\lim_{n\to \infty}E|S^2-\sigma^2|^2=\lim_{n\to \infty}E(S^4+\sigma^4-2S^2\sigma^2)=0$

是均方相合估计



### 3)

​	$\lim_{n\to \infty}P(T(X)-\mu\geq\epsilon)=\lim_{n\to \infty}P(2\sum iX_i/n(n+1)-\mu\geq \epsilon)$

$=\lim_{n\to \infty}P(2\sum\limits_{k=1}^n \sum\limits_{i=1}^k X_i/n(n+1)-\mu\geq \epsilon)$

$=\lim_{n\to \infty}P(\mu+\delta-\mu\geq \epsilon)=0$