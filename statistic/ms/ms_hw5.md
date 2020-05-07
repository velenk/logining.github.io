### 5.1)

$E(\overline{X})=\theta, E(X_{(n)})=\frac{n}{n+1}2\theta $

是无偏估计



### 5.2)

样本一阶原点矩是总体一阶原点矩的强相合估计

$\therefore \hat{\theta}_1$是强相合估计

$\because n\to \infty $

$\therefore P(|X_{(n)}-\frac{n}{n+1}2\theta|\geq \epsilon)=P(|X_{(n)}-2\theta|\geq \epsilon)=0 $

$\therefore P(|X_{(n)}/2-\theta|\geq \epsilon)=0 $

是弱相合估计



### 5.3)

$Var(\hat{\theta}_1)=S^2/n=\theta/6n $

$\because X_{(n)}\sim 2\theta \beta (n, 1) $

$\therefore Var(\hat{\theta}_2)= \displaystyle\frac{\theta^2}{n(n+2)}$

$\therefore $当$6\theta >n+2$时，$\hat{\theta}_1$更有效，反之$\hat{\theta}_2$更有效



### 9)

$P(X>1)=\displaystyle P(N(0,1)>\frac{1-a}{\sigma} )=1-\phi(\frac{1-a}{\sigma})=1-\phi(\frac{1-a_{n1}}{\sqrt{m_{n2}}}) $



### 10)

$\because E(X)=\frac{r}{\lambda} $

$\therefore \hat{\lambda}=r/a_{n1} $

$E(\hat{\lambda})=\frac{r}{E(a_{n1})}=r/E(X)=\lambda $

无偏