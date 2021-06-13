# Chapter 13 
### Pooling Cross Sections across Time: Simple Panel Data Methods

## 13.1 Pooling Independent Cross Sections across Time

Advantages:
1. increase the sample size
2. get more precise estimators and test statistics with more power

Requirement:
depent variable and some of the independent variables remain constant over time
***

example 1:

$$
\begin{aligned}
\mathrm{log}(wage)=&\beta_0+\delta_0y85+\beta_1educ+\delta_1y85\cdot educ+\beta_2exper+\\
&\beta_3exper^2+\beta_4union+\beta_5female+\delta_5y85\cdot female+u
\end{aligned}$$
A log(wage) equation pooled across the years 1978(the base year) and 1985. The variable y85 is a dummy variable equal to one if the observation comes from 1985 and zero if it comes from 1978.

The return to **education in 1978** is  $\frac{\partial \mathrm{log}(wage)}{\partial educ}=\beta_1$, **in 1985** is $\frac{\partial \mathrm{log}(wage)}{\partial educ}=\beta_1+\delta_1$. Therefore, $\delta_1$ measures how the return to another year of education has changed over the seven-year period.
***

## 13.2 Policy Analysis with Pooled Cross Sections
### Difference-indifferences(DID)
example 2:

$\hat \delta_1=\underbrace{(\overline{rprice}_{81,nr}-\overline{rprice}_{81,fr})}_{1981}-\underbrace{(\overline{rprice}_{78,nr}-\overline{rprice}_{78,fr})}_{1978}$

First, calculate the difference between in housing prices of "near the incinerator site" and "farther away from the site" in 1981 and 1978, then calculate the difference between 1978 and 1981. 

$\delta_1$ is the difference over time in the average difference of housing prices in the two locations.

Then, we use:

 $$rprice=\beta_0+\delta_0y81+\beta_1nearinc+\delta_1y81\cdot nearind+u$$ 
 
 to test whether $\hat \delta_1$ is statistically from zero.
***
**Digression:**

1. adding an additional control group, creating a DDD estimator(p.437)

2. $\lambda_t$(intercept) must be added, they are the aggregate time effects that capture external factors.(p.437)

3. $\alpha_g$ account for systematic differences in groups that are constant across time.
***
## 13.3 Two-Period Panel Data Analysis
### **Fixed affects model**
$$y_{it}=\beta_0+\delta_0d2_t+\beta_1x_{it}+a_i+u_{it}, t=1,2$$
- $d2_t$ is a dummy variable that equals zero when t=1 and one when t=2.
- $u_{it}$ is called the idiosyncratic error(ime-varying error), it presents unobserved factors that change over time and affect $y_{it}$
- assume that the unobserved effect $a_{i}$ is uncorrelated with $x_{it}$, so $a_i+u_{it}$ can be written as $v_{it}$
- because $a_{it}$ is correlated with $x_{it}$, pooled OLS is biased and inconsistent(the resulting bias is often called heterogeneity bias)

### **First-differenced equation**
$$\begin{aligned}
&y_{i1}=\beta_0+\beta_1x_{i1}+a_i+u_{i1} \qquad (t=1) \\
&y_{i2}=(\beta_0+\delta_0)\beta_1x_{i2}+a_i+u_{i2} \qquad (t=2)\\
\Rightarrow \quad
&(y_{i2}-y_{i1})=\delta_0+\beta_1(x_{i2}-x_{i1})+({u_{i2}-u_{i1}})\\
\end{aligned}
$$
$$
\Rightarrow \quad \Delta y_i=\delta_0+\beta_1\Delta x_i+\Delta u_i
$$
Assumptions:
- $\Delta u_i$ is uncorrelated with $\Delta x_i$ in both time periods
- $x_{it}$ can be correlated with unobservables that are constant over time

## 13.5 Differencing with More Than Two Time Periods
$$
y_{it}=\delta_1+\delta_2d2_t+\delta_3d3_t+\beta_1x_{it1}+\cdots \beta_k x_{itk}+a_i+u_{it}
$$
Intepretion:
- intercept for the $t_{th}$ time period is $\delta_1+\delta_t$

Key assumption:
- Cov(x_{itj},u_is)=0$, for all $t, s,$ and $j$ ($\Delta u_it$ is uncorrelated over time for the usual standard erors and test statistics to be valid)

tbd.