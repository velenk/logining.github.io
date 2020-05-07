### 1)

令$X_i=Y_i/\sigma\sim N(0,1) $

$T_1=\displaystyle\frac{Y_1^2/\sigma^2}{\sum_{j=2}^n Y_j^2/\sigma^2}=\frac{X_1^2}{\sum X_j^2}=(\frac{X_1}{\sqrt{\chi^2_{n-1}}})^2\sim \frac{1}{n-1}(t_{n-1})^2\sim \frac{1}{n-1}F_{1,n-1} $

$T_2=\displaystyle\frac{1}{1+\displaystyle\frac{\sum_{j=2}^{n-1} Y_j^2}{Y_n^2}}=\frac{1}{1+\displaystyle\frac{n-2}{F_{1,n-2}} }=\frac{1}{1+(n-2)F_{n-2,1}} $



### 2.1)

由因子分解定理

$f(x,\lambda)=\lambda^nexp\{-\lambda t\}=g(t(x),\lambda)h(x) $

是充分统计量

$f(x)=\lambda exp\{-\lambda x \} $

$\phi=-\lambda $

自然参数空间为$\Theta^*=\{-\infty<\phi<0\} $

有内点，是完全统计量



### 2.2)

​	$P(x_1\leq x|T=t)=\lim_{\Delta t\to 0}\displaystyle\frac{P(x_1\leq x,t\leq\sum x_i\leq t+\Delta t)}{P(t\leq\sum x_i\leq t+\Delta t)} $

$=\lim_{\Delta t\to 0}\displaystyle\frac{\displaystyle\int_0^x\int_{t-x_1}^{t+\Delta t-x_1}\lambda e^{-\lambda x_1}\frac{\lambda^{n-1}}{(n-2)!}s^{n-2}e^{-\lambda s}dsdx_1 }{\displaystyle\int_{t}^{t+\Delta t}\frac{\lambda^n}{(n-1)!}s^{n-1}e^{-\lambda s}ds } $

$=\displaystyle\frac{n-1}{t^{n-1}}\int_0^x (t-x_1)^{n-2}dx_1=1-\frac{(t-x)^{n-1}}{t^{n-1}},\quad t>x $

​	$P(x_1\leq x|T=t)=1,\qquad \qquad \qquad \qquad \qquad t\leq x $



### 2.3)

$g(y)=\displaystyle \frac{n!}{(n-r)!}(1-F(x_r))^{n-r}\prod f(x_i)=\frac{n!}{(n-r)!}(e^{-\lambda x_r})^{n-r}\lambda^r e^{-\lambda \sum x_i } $

令$Z_i=X_{(i)}-X_{(i-1)},Z_1=X_{(1)}$

$\because X_{(i)}=\sum Z_i $

$\therefore J=I $

$\therefore g(Z_1,\ldots, Z_n)=\lambda^{n}n!exp\{-\lambda\sum \sum Z_i \}=\lambda^{n}n!exp\{-\lambda\sum(n-i+1)Z_i \} $

$\therefore Z_i\sim exp((n-i+1)\lambda) $

$\therefore 2(n-i+1)Z_i\lambda\sim\chi^2_2 $

$\because S=\sum(n-i+1)Z_i $

$\therefore  S \sim \chi^2_{2r}/2\lambda $

$\therefore f_S(s)=f_{\chi^2}(2\lambda s)=\displaystyle\frac{1}{2^r\Gamma(r)}(2\lambda t)^{r-1}e^{-\lambda s}=\frac{1}{2\Gamma(r)}exp\{-\lambda s\}\lambda^{r-1}s^{r-1} $

$\phi=-\lambda$

自然参数空间为$\Theta^*=\{-\infty<\phi<0\} $

有内点，是完全统计量

$\because f(x,\lambda)=\displaystyle\frac{n!}{(n-r)!}\lambda^r exp\{-\lambda s \} $

由因子分解定理知，是充分统计量

