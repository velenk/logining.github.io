### 14)

令$\phi=1/\theta^2 $

$f(x,\phi)=x\phi exp\{-x^2\phi/2\} $

是指数族

$\because \displaystyle \frac{n}{C(\theta)}\frac{\partial C(\theta)}{\partial \theta}=-\sum T_i(X_j) $

$\therefore \displaystyle \frac{n}{\phi}=\sum x_i^2/2 $

$\therefore \phi=2n/\sum x_I^2 $

$\therefore \theta =\sqrt{\displaystyle\frac{\sum x_i^2}{2n}} $



### 19)

先估计均值

$L(\theta,x)=\displaystyle(\frac{1}{\sqrt{2n}\sigma})^n exp\{\sum -\frac{(x_i-\mu)^2}{2\sigma^2} \} $

$lnL=nln \displaystyle(\frac{1}{\sqrt{2n}\sigma}) -\sum \frac{(x_i-\mu)^2}{2\sigma^2}$

$\because \displaystyle\frac{\partial lnL}{\partial \mu}=0 $

$\therefore \hat\mu=\sum x_i/n $

$\therefore \hat\mu_1=\overline{X},\hat\mu_2=\overline{Y} $

再考虑方差

$L(\sigma^2,x)=\displaystyle(\frac{1}{\sqrt{2n}\sigma})^{2n} exp\{\sum -\frac{(x_i-\mu_1)^2+(y_i-\mu_2)^2}{2\sigma^2} \} $

$lnL=2nln \displaystyle(\frac{1}{\sqrt{2n}\sigma}) -\sum \frac{(x_i-\mu_1)^2+(y_i-\mu_2)^2}{2\sigma^2}$

$\because \displaystyle\frac{\partial lnL}{\partial \sigma^2}=0   $

$\therefore \hat\sigma^2=\frac{1}{2n}\sum ( (x_i-\overline{X})^2+(y_i-\overline{Y})^2 ) $



### 20)

近似成有放回抽样，设抽中标记概率为k

$P(x=10)=\displaystyle\frac{C_{1000}^{10}C_{N-1000}^{140}}{C_N^{150}}\approx C_{150}^{10}k^{10}(1-k)^{140} $

求导得

$C_{150}^{10} k^9(1-k)^{139}(10-150k)=0 $

$\therefore k=1/15$

$\therefore$一共有15000条时概率最大

