### 12)

$\because \alpha\overline{X}+\beta\overline{Y}\sim N(\alpha \mu_1+\beta \mu_2,\alpha^2\sigma^2/m^2+\beta^2\sigma^2/m^2) $

$\therefore \displaystyle\frac{\alpha\overline{X}+\beta\overline{Y}-\alpha\mu_1-\beta\mu_2 }{\sigma\sqrt{\alpha^2/m^2+\beta^2/m^2}}\sim N(0,1) $

$\because mS_{1m}^2/\sigma^2\sim\chi^2_{m-1},nS_{1n}^2/\sigma^2\sim\chi^2_{n-1} $

$\therefore T\sim t(m+n-2) $



### 26)

令$Z_i=X_{(i)}-X_{(i-1)},Z_1=X_{(1)}$

$f(X_{(1)},\ldots,X_{(n)})=\lambda^{-n}n!exp\{-\frac{1}{\lambda}\sum{X_{(i)}} \} $

$\because X_{(i)}=\sum Z_i $

$\therefore J=I $

$\therefore g(Z_1,\ldots, Z_n)=\lambda^{-n}n!exp\{-\frac{1}{\lambda}\sum \sum Z_i \}=\lambda^{-n}n!exp\{-\frac{1}{\lambda}\sum(n-i+1)Z_i \} $

$\therefore Z_i\sim exp((n-i+1)/\lambda) $

$\therefore 2(n-i+1)Z_i/\lambda\sim\chi^2_2 $

$\because T=\sum(n-i+1)Z_i $

$\therefore 2T/\lambda \sim \chi^2_{2r} $



### 27)

令$Z_i=X_{(i)}-X_{(i-1)},Z_1=X_{(1)}-\mu$

$f(X_{(1)},\ldots,X_{(n)})=\prod (1-exp\{-(X_{(i)}-\mu)/\sigma\}) $

$\because X_{(i)}=\sum Z_i $

$\therefore J=I $

$\therefore g(Z_1,\ldots, Z_n)=\prod (1-exp\{-\sum Z_i/\sigma\}) $

$\therefore 2(n-i+1)Z_i/\lambda\sim\chi^2_2 $



### 28)

$F_1(y)=P(X_1+X_2\leq y)=\displaystyle\frac{\lambda^{\alpha_1+\alpha_2}}{\Gamma(\alpha_1)\Gamma(\alpha_2)}e^{-\lambda y}\int_0^y (1-e)^{\alpha_1-1}e^{\alpha_2-1}dt=\int_0^yy^{\alpha_1+\alpha_2-1}(1-t)^{\alpha_1-1}t^{\alpha_2-1}dt $

$\therefore p(y)=\displaystyle\lambda^{\alpha_1+\alpha_2}e^{-\lambda y}y^{\alpha_1+\alpha_2-1}\frac{1}{\Gamma(\alpha_1+\alpha_2)} $

$\therefore Y_1\sim\Gamma(\alpha_1+\alpha_2,\lambda) $