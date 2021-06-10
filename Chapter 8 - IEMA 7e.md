# Chapter 8 Heteroskedasticity

Consider a multple linear regression model:

 $y=\beta_0 + \beta_1x_1+\beta_2x_2+\cdots+\beta_kx_k+u$

Under the first four Gauss-Markov assumptions, the OLS estimators are proved to be **unbiased**. The homoskedasticity assumption(MLR.5) states in terms of the error variance as $\space Var(u|\mathbf{x})=\sigma^2$.

Heteroskedasticity does not cause **bias** or **inconsistency** of $\beta_j$, and also do not affect $R^2$ or $\overline {R^2}$.
Though, $Var(\hat \beta_j)$ are biased when heteroskekasticity occurs.

## **Consequences of heteroskedasticity:**

Thus, $se(\hat \beta_j)$ are also biased and they are not valid for constructing confidence intervals and t statistics.

OLS is no longer BLUE or symptotically efficient.

***
### _Review:_

- **Assumption MLR.5 Homoskedasticity**     (page.88)

    The error $u$ has the same variance given any value of the explanatory variables. $Var(u|x_1,\cdots,x_k)=\sigma^2$
- calculation of $Var (\hat\beta_j)$

    $Var(\hat\beta_j)=\frac{Var{(y|\mathbf{x}})}{SST_j(1-R_j^2)}=\frac{\sigma^2}{SST_j(1-R_j^2)}$ ,  where  $SST_j=\sum_{i=1}^n(x_{ij}-\overline x_j)^2$

***
