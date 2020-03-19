### 39)

负二项分布

$P(X=x)=\binom{x+r-1}{r-1}p^r(1-p)^x=\binom{x+r-1}{r-1}exp\{xln(1-p)\}p^r $

$\phi=ln(1-p) $

$\therefore p=1-e^{\phi} $

自然参数空间为$\Theta^*=\{-\infty<\phi<0\} $

指数分布

$f(x)=\lambda exp\{-\lambda x \} $

$\phi=-\lambda $

自然参数空间为$\Theta^*=\{-\infty<\phi<0\} $



### 41)

设$\theta ,\phi \in \Theta $

对于$0<a<1$

$\int h(x)exp\{(a\theta + (1-a)\phi)x\}dx=\int h(x)(exp\{x\theta\})^a(exp\{x\theta\})^{1-a}dx $

由Holder不等式得

$\int h(x)exp\{(a\theta + (1-a)\phi)x\}dx\leq (\int h(x)(exp\{x\theta\})dx)^a (\int h(x)(exp\{x\phi \})dx)^{1-a} $

所以是凸集



### 42)

$P(X=x|T=t)=P(X=x,T=t)/P(T=t)=\displaystyle\frac{\lambda^t e^{-n\lambda}\prod x_i! }{(n\lambda)^te^{-n\lambda}/t!}=\frac{\prod x_i! }{n^t/t!} $

是充分统计量

$f(x,\lambda)=\lambda^te^{-n\lambda}/\prod x_i!=g(t(x),\lambda)h(x) $

是充分统计量



