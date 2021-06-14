# Advanced Panel Data Methods
## 14.1 Fixed Effects Estimation
$$\begin{aligned}
&y_{it}=\beta_1x_{it}+a_i+u_{it} \quad t=1,2,\cdots,T\\
&\overline y_i=\beta_1\overline x_i +a_i+\overline u_i\\
\Rightarrow &\ddot{y_{it}}=\beta_1\ddot{x_{it}}+\ddot{u_{it}}\\
\mathrm{where} &\quad \ddot{y_{it}}=y_{it}-\overline y_i
\end{aligned}$$
- under a strict exogeneity assumption on the explanatory variable across all time periods

### Comparing Fixed Effects and First Differencing
- when T=2: FE and FD estimates, as well as all test statistics are identical
- when T $\geq$ 3: 
  - when the $u_{it}$ are serially uncorrelated, fixed effects is more efficient than first differencing(the standard error reported from fixed effects are valid)
  - tbd

## 14.2 Random Effects Models