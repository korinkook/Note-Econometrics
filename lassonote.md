<font face="garamond">

## LASSO regression Study Note

Let
$$ 
\begin{aligned}
\quad y&=b_0+b_1x_1+b_2x_2+...+b_nx_n\\
&=\mathbf{b x}
\end{aligned}
$$
Estimated value:
$$ 
\begin{aligned}
\quad \hat y&=\hat b_0+\hat b_1x_1+\hat b_2x_2+...+\hat b_nx_n\\
&=\mathbf{\hat b x}
\end{aligned}
$$

MSE(based on OLS):

$$ 
\begin{aligned}
\quad \frac{1}{n}\sum_{i=1}^n(y-\hat y)^2
\end{aligned}
$$

Loss function（損失関数）:
$$\frac{1}{n}\sum_{i=1}^n(y_n-\hat y_n)^2+\lambda \left \| \mathbf{x} \right \|_1$$


/*

$\lambda$ は$L_2$ normをコントロールするハイパーパラメーター
(自分で設定できるが、L-curveとかで計算した方が主流)

***
### Digression:
$L_1$ norm:
$|v|_1=\sum |v_i|$

$L_2$ norm:
$|v|_2=\sqrt{\sum v_i^2}$

