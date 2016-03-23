#Geographically Weighted Regression



In this essay I will provide some information about Geographically Weighted Regression which is excellent tool for testing model specification. To understand (GWR) and its methodology we should know regression and spatial analysis. At the beginning *the aim of data analysis* is to provide relationship between two variables.
Actually, ***regression*** is the most common type to obtain this aim. *If* we want to define regression, we will say is the statistical measure that attempts to determine relationship between one dependent variable and many others changing variables.
A linear regression model can take the form:
y_i=B_0+B_1 x_i+ε_i     For i= 1, 2…n
The equation y_i here represent variable measured in location i, x_iis the independent variable, and ε_i is the error term. B_0and B_1 are parameters which are to be estimated.

*In general*, a multiple linear regression model may be written as: 
y_i=B_0+B_1 x_1i+B_2 x_2i+⋯+B_m x_mi+ε_i     for i= 1…n

* In spatial analysis* the data pulled from geographical units and a single regression equation is estimated we assume a stationary process. What is happening has an impact in producing average or global parameter estimates. 
The regression equation is then:
y_i=B_io+∑_(k=1'm)▒B_ik  x_ik+ε_i 
Where B_ikis the value of the kth parameter at location i, the ε_i are independent normally distributed error terms with zero means N (0,σ^2 I). Usually the least squares method is used to estimate B_ks as what we done here. As the maximum likelihood estimate of B .

B ̀=〖(x^t x)〗^(-1) x^t y
This method is applied to geographical data is that each case corresponds to geographical location. 
The assumption of stationarity in regression is:  y_i=∝+Bx
When applied to spatial data, it assumes a stationary spatial process. The measured relationships vary spatially because several points.
<ol>
<li>Sampling variation. </li>
<li>, Relationships intrinsically different across space.</li>
<li>Model misspecification.</li>
</ol>
*Actually*, Local models good indicator of how model is misspecified. 
<em>Note</em>: if there is spatial nonstationary, we only see it through the residuals not directly because (GWR).
######Geographically weighted regression
is an exploratory technique mainly intended to indicate where non-stationarity is taking place on the map, that is where locally weighted regression coefficients move away from their global values.
y_i=B_0+B_1 x_1i+B_2 x_2i+⋯+B_m x_mi+ε_i * * * (B(u)) ̀=(x^t W(u)x)^(-1) x^t W(u)y
Where W(u) is a square matrix of weights specific to location u in the study area, X^T W(u)X is the geographically weighted variance-covariance matrix, and y is the vector of the values of the dependent variable.
The weight matrix W(u) contains the geographically weights in its leading diagonal and 0 in its off diagonal elements which is helpful for investigating the precision of spatially varying estimates .
■(W_1 (u)&0&0@0&W_2 (u)&0@0&0&W_(n ) (u))
Where W_(n )is the weight given to data point n for the estimate of the local parameters at location u. In fact this matrix is the key output of GWR. By selecting individual rows, it is possible to see how a coefficient corresponding to a given predictor variable changes geographically. More than that, this is possible to find the stander error of coefficient estimate.  
Numerous weighting schemes can be used although they tend to be **Gaussian**:

,img src="http://www.mdpi.com/remotesensing/remotesensing-07-06454/article_deploy/html/images/remotesensing-07-06454-g003.png" alt="Gaussian" />

W_i (u)=e^(-.5(d_1 (u)/h)〖^2〗) 
where d_1 (u)is the distance between locations u h is the bandwidth – as h increases, the gradient of the kernel becomes less steep and more data points are included in the local calibration. We need to find the optimal value of h in the GWR routine. A Spatially Adaptive Weighting Function:
W_i (u)=〖(1-((d_1 (u))/h)^2)〗^2    and     0 when 𝑑1𝑢ℎ>h.
Where W_i (u)  is zero when (d_1 (u))/h>h this is a nearest neighbor with the useful property that the weight is zero at a finite distance. These functions will be referred as *Kernel functions* and denoted by letter K as in  W_i (u)=K.
*Generally*, the Kernel functions K are:
<ul>
	<li>K(0)=1</li>
<li>	lim┬(d→∞)⁡〖K(d)=0  /<li>
<li>	K is a monotone decreasing function for positive real numbers.</li> 
</ul>
	K is a monotone decreasing function for positive real numbers. 
The results of GWR appear to be relatively insensitive to the choice of weighting function as long as it is a continuous distance-based function. Whichever weighting function is used. However, be sensitive to the degree of distance-decay. Therefor an optimal value of either h or N has to be obtained. This can be found by minimizing a cross validation score (CV) or the Akaike Information Criterion (Hurvich et al, 1998) this takes the following form: 
AIC_C=2nlog(σ ̂ )+n〖log〗_e (2π)+n((n+tr(s))/(n-2-tr(s)))
Where n is the number of observations in the dataset, σ ̂ is the estimate of standard deviation of residuals, and tr(s) is the trace of the hot matrix.  The AIC_C can be used to compare models of the same y variable which have very different right hand sides and it contains a penalty for the complexity of the model. Also, the AIC_C can not only be used to compare models with different independent variable, but can also be used to compare the global ordinary least squares (OLS)model with local (GWR)model. It is important to mention the use of The AIC_C in software. 
The Output from GWR is a set of location-specific parameter estimates which can be mapped and analyzed to provide information on spatial nonstationary in relationships and their associated standard error at the regression points. If the regression points are the same as the sample points then the GWR will produce predictions for the independent variable, residuals and standardized residuals. If the regression points are not the same as the sample points, and there are no the independent variable available for regression points then parameter estimates and standard errors will be available. 
In GWR, we can also estimate:
•	local standard errors.
•	 derive local t statistics.
•	 calculate local goodness-of-fit measures.
•	 perform tests to assess the significance of the spatial variation in the local parameter estimates.
•	 perform tests to determine if the local model performs better than the global one, accounting for differences in degrees of freedom.
*In conclusion*, the basic idea behind GWR is to explore how the relationship between a dependent variable (Y) and one or more independent variables (the Xs) might vary geographically. This essay provide the reason of using (GWR).

###References
<ul>
<li> <a href="http://onlinelibrary.wiley.com/doi/10.1111/1467-9884.00145/epdf/">Geographically weighted regressionÐmodellingspatial non-stationarity</a> </li>
<li> <a href="http://http://eprints.maynoothuniversity.ie/5895/1/CB_Weighted%20Regression.pdf/"> Geographically Weighted Regression: A Method
for Exploring Spatial Nonstationarity</a> </li>
</ul>

