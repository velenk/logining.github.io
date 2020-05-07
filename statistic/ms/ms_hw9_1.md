### 7)

$f(x|p)=\binom{x-1}{k-1}p^k(1-p)^{n-k} $

$p\sim Be(a,b) $

$\pi(p|x)=\displaystyle\frac{p^{k+a-1}(1-p)^{n-k+b-1}}{\int_0^1 p^{k+a-1}(1-p)^{n-k+b-1} dp}\sim Be(k+a,n-k+b) $

得证



### 9)

$f(x|\theta)=exp\{a(\theta)b(x)+c(\theta)+d(x) \} $

$h(\theta)=Ae^{k_1a(\theta)+k_2c(\theta)} $

$\pi(\theta|x)\displaystyle \propto exp\{a(\theta)(b(x)+k_1)+c(\theta)(1+k_2) \} $

添加正则化常数C即可得到先验分布，与h同分布族

得证



### 13.1)

后验分布$\pi(\theta|\overline{x})\sim N(\mu_n(\overline{x}),\eta_n^2) $

后验方差$\eta_n^2=\displaystyle\frac{4\tau^2}{100\tau^2+4}<1/25 $

所以后验标准差小于$1/5$



### 13.2)

$\eta_n^2=\displaystyle\frac{4}{n+4}<0.1 $

$\therefore n\geq 36 $



### 14.1)

后验分布$\pi(\theta|\overline{x})=(x^2+x)\theta(1-\theta)^{x-1} $

$\therefore \hat\theta_B=2/(x+2) $

$\therefore x=3,\hat\theta_B=2/5 $



### 14.2)

令$t=\sum x_i$

$f(x|\theta)=\theta^3(1-\theta)^{\sum x_i -3}=\theta^3(1-\theta)^{t-3} $

后验分布$\pi(\theta|\overline{x})=\displaystyle\frac{(t+1)!}{3!(t-3)!}\theta^3(1-\theta)^{t-3} $

$\therefore \hat\theta_B=4/(t+2) $

$\therefore t=10,\hat\theta_B=1/3 $