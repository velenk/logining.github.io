先加载数据集：

```R
> iris.train<-iris[c(1:25,51:75,101:125),]
> iris.test<-iris[c(26:50,76:100,126:150),]
```

利用knn算法进行处理，结果如下：

```R
> iris.kknn <- kknn(Species~., iris.train, iris.test, distance = 1, kernel = "triangular")
> table(iris.test$Species, fitted(iris.kknn))> table(iris.test$Species, fitted(iris.kknn))
            
             setosa versicolor virginica
  setosa         25          0         0
  versicolor      0         23         2
  virginica       0          4        21

```

需要的表格如上所示。