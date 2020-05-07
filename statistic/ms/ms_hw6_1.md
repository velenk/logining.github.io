### 22.1)

$\because L(\mu,x)=e^{n\mu -\sum x_i} $

$\therefore \displaystyle\frac{\partial L}{\partial \mu}=ne^{n\mu -\sum x_i}(ln(n\mu -\sum x_i)) $

$\therefore \hat\mu^* =(\sum x_i +1)/n >X_{(1)} $

$\therefore \hat\mu^*=X_{(1)} $

不是无偏估计

$E(\hat\mu^*)=\mu+1 $

$\therefore \hat\mu^{**}=X_{(1)}-1 $



### 22.2)

$\because E(x)=\mu+1 $

$\therefore \hat\mu = \overline{X}-1 $

$\because E(\hat\mu)=\mu $

是无偏估计



### 22.3)

$\because Var(\hat\mu^{**})=1,Var(\hat\mu)=1/n $

后者更有效



### 24)

$L(\sigma^2,x)=\displaystyle(\frac{1}{\sqrt{2n}\sigma})^{n} exp\{\sum -\frac{(x_i-\mu_1)^2}{2\sigma^2} \} $

$lnL=nln \displaystyle(\frac{1}{\sqrt{2n}\sigma}) -\sum \frac{(x_i-\mu_1)^2}{2\sigma^2}$

$\because \displaystyle\frac{\partial lnL}{\partial \sigma^2}=0   $

$\therefore \hat\sigma^2=\frac{1}{n}\sum (x_i-\overline{X})^2 $

$\because E(\hat\sigma^2)=\frac{n}{n-1}\sigma^2 \to \sigma^2 $

$\therefore $是弱相合估计



### 25)

设k为$X_i$中有理数的个数

$L(\theta,x)=\theta^k(1-\theta)^{n-k} $

$l(\theta,x)=kln\theta +(n-k)ln(1-\theta) $

$\therefore \hat\theta^*=k/n $

因为无理数基数大于有理数，所以不是相合估计