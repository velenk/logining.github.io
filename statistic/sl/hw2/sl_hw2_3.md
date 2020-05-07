利用R进行logistic回归，结果如下。

```R
> userdata <- read.csv(file="sample2.txt",encoding="UTF-8")
> glm.sol<-glm(y~x1+x2+x3,family = binomial(link = logit), data = userdata)
> summary(glm.sol)

Call:
glm(formula = y ~ x1 + x2 + x3, family = binomial(link = logit), 
    data = userdata)

Deviance Residuals: 
    Min       1Q   Median       3Q      Max  
-1.5636  -0.9131  -0.7892   0.9637   1.6000  

Coefficients:
             Estimate Std. Error z value Pr(>|z|)  
(Intercept)  0.597610   0.894831   0.668   0.5042  
x1          -1.496084   0.704861  -2.123   0.0338 *
x2          -0.001595   0.016758  -0.095   0.9242  
x3           0.315865   0.701093   0.451   0.6523  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)

    Null deviance: 62.183  on 44  degrees of freedom
Residual deviance: 57.026  on 41  degrees of freedom
AIC: 65.026

Number of Fisher Scoring iterations: 4

```

通过t检验知，只有x1对于结果有显著的负相关。即只有视力状况和去年是否发生事故显著负相关。