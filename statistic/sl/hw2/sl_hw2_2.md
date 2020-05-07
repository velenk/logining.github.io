转换为txt格式后直接进行回归，回归结果如下

```R
> userdata <- read.csv(file="sample1.txt",encoding="UTF-8")
> lm.sol=lm(y~x1+x2,data=userdata)
> summary(lm.sol)

Call:
lm(formula = y ~ x1 + x2, data = userdata)

Residuals:
    Min      1Q  Median      3Q     Max 
-7.4451 -0.8037  0.7530  0.8509  4.7338 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) -59.6014    22.2298  -2.681  0.02305 *  
x1            1.0493     0.1127   9.313 3.04e-06 ***
x2            0.3870     0.1142   3.388  0.00691 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3.544 on 10 degrees of freedom
Multiple R-squared:  0.9169,    Adjusted R-squared:  0.9003 
F-statistic: 55.19 on 2 and 10 DF,  p-value: 3.957e-06

```

结果满足t检验和F检验。

所以得到结论，在人的身高相等的条件下，其血压的收缩压y确实与体重x1、年龄x2都成正相关。