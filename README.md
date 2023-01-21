# Nelson-Siegel-Svensson
## This repo
The code in this repo contains a Python implementation of the Nelson-Siegel-Svensson (NSS) curve.
For any questions, comments, or complaints, feel free to reach out! 

<br>

## The Nelson-Siegel-Svensson model
The NSS model is used to construct yield curves using continuous YTMs. It is used by monetary institutions to estimate yield curves. With respect to the simpler Nelson-Siegel model, NSS allows the modelled yield curve to be more flexible, particularly in its short-term shape. 

### Mathematically
$$
r(t) = \beta_1 + \beta_2 \frac{1-e^{\frac{-T}{\lambda_1}}}{\frac{T}{\lambda_1}} + \beta_3 \left( \frac{1-e^{\frac{-T}{\lambda_1}}}{\frac{T}{\lambda_1}} - e^{\frac{-T}{\lambda_1}} \right) + \beta_4 \left( \frac{1-e^{\frac{-T}{\lambda_2}}}{\frac{T}{\lambda_2}} - e^{\frac{-T}{\lambda_2}} \right)
$$

### Parameters
**N.B.** the optimisation procedures of the NSs model is very sensitive to the initial estimates the model is fed.
- As $\beta_1$ determines the level of the yield curve, its estimate is set to the rate of the longest-term security available in a given yield curve.
- $\beta_2$ determines the slope of the curve. For $\beta_2$ to represent the yield curve's slope, it must be true that $(\beta_1 + \beta_2) = \text{rate of shortest-term bond available}$. 
- $\beta_3$ defines the curvature of the Yield Curve. In this implementation, the initial estimate set is $-5\%$.
- The “hump” in the yield curve of the NSS models is determined by $\lambda_1$. In this implementation, the initial estimate set is $1.5$.
- $\beta_4$ and $\lambda_2$ further improve the shape of the curve, and are manually set to initial values of $0.5\%$ and $1.0$ respectively.
