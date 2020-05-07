### 6.1)

$l(x,\lambda)=-n\lambda +ln\lambda^{\sum x_i}-ln\prod x_i! $

$I(\lambda)=\displaystyle E(\frac{\sum x_i}{\lambda^2})=n/\lambda $

$\therefore \pi(\lambda)=\displaystyle\sqrt{\frac{n}{\lambda}} $



### 6.2)

$f(x,\theta)=\theta^x(1-\theta)^{n-x} $

$l(\theta)=xln\theta+(n-x)ln(1-\theta) $

$I(\theta)=\displaystyle E(x/\theta^2-(n-x)/(1-\theta)^2)=\frac{n}{2}(\frac{1}{\theta^2}-\frac{1}{(1-\theta)^2}) $

$\therefore \pi(\theta)=\displaystyle\sqrt{\frac{n}{2}(\frac{1}{\theta^2}-\frac{1}{(1-\theta)^2})} $



### 6.3)

$l(\alpha,\lambda)=-nln\Gamma(\alpha)-n\alpha ln\lambda +(\alpha-1)\sum x_i -\sum x_i /\lambda $

$I(\lambda)=E(2\sum x_i/\lambda^3-n\alpha/\lambda^2)=2\alpha/\lambda^4-n\alpha/\lambda^2 $

$\therefore \pi(\lambda)=\sqrt{2\alpha-n\alpha\lambda^2}/\lambda^2 $



### 21)

平方损失下，Bayes估计即为后验期望

$\pi(\theta|x)=\displaystyle\frac{(n+1)^{\sum x_i+1}}{\Gamma(\sum x_i +1)}\theta^{\sum x_i}e^{-(n+1)\lambda} $

$\hat\theta_B(x)=(\sum x_i +1)/(n+1) $



### 24)

$\because \hat\tau_B=\displaystyle\frac{E(\tau w(\tau)|x)}{E(w(\tau)|x)} $

$w(\tau)=1/\tau^2 $

$\therefore \hat\tau_B= \displaystyle\frac{E(1/\tau|x)}{E(1/\tau^2|x)}$

$\because E(1/\tau|x)=\beta /\alpha,E(1/\tau^2|x)=(\beta^2+\beta)/\alpha^2 $

$\therefore \hat\tau_B=\alpha/(\beta+1) $

