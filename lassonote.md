# LASSO regression Study Note

## About LASSO
Consider a multiple linear regression model:
$$ 
\begin{aligned}
\quad y&=b_0+b_1x_1+b_2x_2+...+b_nx_n\\
&=\mathbf{b x}
\end{aligned}
$$
Estimated value（予測値）:
$$ 
\begin{aligned}
\quad \hat y&=\hat b_0+\hat b_1x_1+\hat b_2x_2+...+\hat b_nx_n\\
&=\mathbf{\hat b x}
\end{aligned}
$$

MSE(mean squared error):
$$ 
\quad \frac{1}{n}\sum_{i=1}^n(y-\hat y)^2
$$
> MSE measures the average of the squares of the errors—that is, the average squared difference between the estimated values and the actual value, corresponding to the expected value of the squared error loss.

最小二乗法の考え方は、MSEを最小にするような推定量を見つけ出すことである。だが、変数の個数が多かったらoverfitting（過剰適合）という現象が起きる恐れがある。
>![avatar](https://miro.medium.com/max/2250/1*_7OPgojau8hkiPUiHoGK_w.png)
>Ken Hoffman, Machine Learning: How to Prevent Overfitting, https://medium.com/swlh/machine-learning-how-to-prevent-overfitting-fdf759cc00a9

そのため、MSEに推定量への制御（ここで$\alpha\cdot L_1$ノルム）を加えることで、推定量(coefficient vector)のmagnitudeをコントロールする
- $L_1$ノルム：$|v|_1=\sum |v_i|$
    >ノルム:
    >https://ja.wikipedia.org/wiki/%E3%83%8E%E3%83%AB%E3%83%A0
- $\alpha$：ハイパーパラメーター(regularization parameter)
  - モデルの複雑さをコントロールするパラメーター
  - 簡単なモデルが欲しかったら、$\alpha$を大きく設定する
  - 自分で設定できるが、L-curveとかで計算した方が主流(パッケージで自動的に算出してくれるので計算方法はここで省略.

Loss function（損失関数）:
$$\frac{1}{n}\sum_{i=1}^n(y_n-\hat y_n)^2+\lambda \left \| \mathbf{b} \right \|_1$$

e.g.
-  MSEを最小化にするための　$\hat y_i=\hat b_0+\hat b_1x_{1i}+\hat b_2x_{2i}+\hat b_3{x_3i}^3+b_4{x_4i}^3+u$という推定式があり、$x_3$と$x_4$はoverfittingを起こしたと仮定する
- $\alpha\cdot L_1$ノルムを加えることで、$b=\mathrm{argmin(MSE)}$から$b=\mathrm{argmin(MSE}+\alpha \cdot |b|)$になる
- 新しい損失関数を最小化にするようにしたら、推定量のmagnitudeを抑えることができ、$x_3$と$x_4$の$y$への影響も小さくなる（過学習を抑えることができる）


***
## Realization in R
``` r
#必要なパッケージをダウンロードし、使用する
install.packages("glmnet")
library(glmnet)

#データを読み込む
data1<-read.table("C:\Users\koko\Desktop\data.csv", header=true)
df1.outcome<-dat1$Y
df1.x<-as.matrix(dat1[,1:20]])

fit1<-cv.glmnet(df1.x,df1.outcome,family="gaussian",type.measure="deviance")

#lambdaの値を表示する
fit1$lambda.min #損失関数を最小化にするlambda
fit1$lambda.1se #lambda.minより1seの範囲内で一番簡単なモデルを導くlambda（これを使う）

#計算結果を表示
result.1se<-predict(fit1, s=fit1$lambda.1se,
                    newx=model.matrix(.,dat1[,-ncol(dat1)]),
                    type="coefficients")
```

***
## Realization in Python

***
### Digression:

#### Differences between LASSO and Ridge regression:
$L_1$ norm:
$|v|_1=\sum |v_i|$

$L_2$ norm:
$|v|_2=\sqrt{\sum v_i^2}$　（ridge regで用いられている）
>![avatar](https://i.loli.net/2018/11/19/5bf2b1deeb51e.jpg)