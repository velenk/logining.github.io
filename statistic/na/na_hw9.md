### 1)

$\begin{pmatrix} 1 & 2 & -1 & -1 \\ -3 & 1 & 3 & 2 \\ 3 & -2 & 1 & 3 \end{pmatrix}\to  $

$\begin{pmatrix} 3 & -2 & 1 & 3  \\ -3 & 1 & 3 & 2 \\ 1 & 2 & -1 & -1 \end{pmatrix}\to  $

$\begin{pmatrix} 3 & -2 & 1 & 3  \\ 0 & -1 & 4 & 5 \\ 0 & 8/3 & -4/3 & -2 \end{pmatrix}\to  $

$\begin{pmatrix} 3 & -2 & 1 & 3  \\ 0 & 8/3 & -4/3 & -2 \\ 0 & -1 & 4 & 5 \end{pmatrix}\to  $

$\begin{pmatrix} 3 & -2 & 1 & 3  \\ 0 & 8/3 & -4/3 & -2 \\ 0 & 0 & 7/2 & 17/4 \end{pmatrix}  $

$ \therefore x_1 =1/2,x_2=-1/7,x_3=17/14 $



### 2)

首先L是三角矩阵

$a_{ij}=\sum\limits_k l_{ik}l_{kj}  $





### 3)

$||A||_F =\sqrt{\sum |a_{ij}|^2}\geq 0 $

$||A||_F =0 \Leftrightarrow a_{ij}=0 $

满足正定性

$||cA||_F =\sqrt{\sum |ca_{ij}|^2} =c\sqrt{\sum |a_{ij}|^2} $

满足齐次性

定义内积$<A,B>=\sum\limits_i\sum\limits_j |a_{ij}||b_{ij}| $

$\therefore ||A||_F =\sqrt{<A,A>} $

将n阶矩阵看作$n^2$维向量，利用Cauchy-Schwarz不等式得

$<A,B>\leq||A||_F ||B||_F $

$\therefore ||A+B||_F^2=<A+B,A+B>=<A,A>+<B,B>+2<A,B> $

$\leq ||A||_F^2+||B||_F^2+2||A||_F ||B||_F=(||A||_F +||B||_F)^2 $

三角不等式得证

令$C=AB$

$c_{ij}=\sum\limits_k a_{ik}b_{kj} $

$||AB||_F=\sqrt{\sum\limits_i \sum\limits_j |c_{ij}|^2 }\leq \sqrt{\sum\limits_i \sum\limits_j |\sum\limits_k a_{ik}^2 \sum\limits_k b_{kj}^2 | } $

$=\sqrt{\sum\limits_i \sum\limits_k a_{ik}^2 \sum\limits_j  \sum\limits_k b_{kj}^2 }=||A||_F||B||_F $

相容性得证



### 4.a)

$||A||_2= $



### 4.b)



### 4.c)



### 5)

利用python编程计算

```python
import numpy as np

def solve(n):

    H = np.zeros((n, n))
    x0 = np.zeros(n) + 1
    x = np.zeros(n)

    for i in range(n):
        for j in range(n):
            H[i][j] = 1/(i+j+1)

    H0 = np.copy(H)
    b = np.dot(H, x0.T)
    b0 = np.max(np.abs(b))

    for i in range(n-1):
        ans = i
        for j in range(i,n):
            if np.abs(H[j][i]) > np.abs(H[ans][i]):
                ans = j
        b[i], b[ans] = b[ans], b[i]
        H[[i, ans], :] = H[[ans, i], :]
        if H[i][i] == 0:
            continue
        for j in range(i+1, n):
            res = H[j][i] / H[i][i]
            H[j] = H[j] - H[i] * res
            b[j] = b[j] - b[i] * res


    for i0 in range(n):
        i = n-1-i0
        ans = b[i]
        for j0 in range(i0):
            j = n-1-j0
            ans -= x[j] * H[i][j]
        x[i] = ans / H[i][i]


    r0 = np.dot(H0, x0.T) - np.dot(H0, x.T)
    r1 = np.max(np.abs(r0))
    r2 = np.max(np.abs(x - x0))
    cond = r2 / r1 * b0
    
    return (x, r1, r2, cond)

# res0 = solve(100)
for i in range(10, 100):
    res0 = solve(i)
    if res0[2] > 1:
        print(i)
        break


print(res0[0])
# 解向量
print(res0[1])
# 后向误差
print(res0[2])
# 前向误差
print(res0[3])
# 条件数
'''
Out:
13
[ 1.00000006  0.99999038  1.00038941  0.99327396  1.06216203  0.65488996
  2.22734083 -1.89225271  5.56657209 -3.77676509  4.17553453 -0.21463552
  1.20350015]
2.220446049250313e-16
4.7767650891418025
6.841306459777838e+16
'''
```

所以n最小为13，此时的条件数为$6.841*10^{16} $

