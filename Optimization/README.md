<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/Optimization.png" width="900" height="150">

### Methods of optimization:

- Curve Fitting

## Curve Fitting

**Curve fitting** is a type of optimization that finds an optimal set of parameters for a defined function that best fits a given set of observations.

Unlike supervised learning, curve fitting requires that you define the function that maps examples of inputs to outputs.

The mapping function, also called the basis function can have any form you like, including a straight line (linear regression), a curved line (polynomial regression), and much more. This provides the flexibility and control to define the form of the curve, where an optimization process is used to find the specific optimal parameters of the function.

### Articles 

- [Curve Fitting With Python](https://machinelearningmastery.com/curve-fitting-with-python/)
- [How to do exponential and logarithmic curve fitting in Python? I found only polynomial fitting](https://stackoverflow.com/questions/3433486/how-to-do-exponential-and-logarithmic-curve-fitting-in-python-i-found-only-poly)
- [Gaussian fit for Python](https://stackoverflow.com/questions/19206332/gaussian-fit-for-python/19207683)

### How to estimate error in curve fitting?

- [Mean Squared Error](https://en.wikipedia.org/wiki/Mean_squared_error) (MSE) or Mean Squared Deviation (MSD)
- [Mean Squared Prediction Error](https://en.wikipedia.org/wiki/Mean_squared_prediction_error) (MSPE) or Mean Squared Error of the Predictions (MSEP)
- [Root-Mean-Square Deviation](https://en.wikipedia.org/wiki/Root-mean-square_deviation) (RMSD) or root-mean-square error (RMSE)
- [Coefficient of determination, R squared](https://en.wikipedia.org/wiki/Coefficient_of_determination) -> **R<sup>2</sup>** ( ‼️ **only for linear functions**)

## Estimation

| Title | Description |
| :---: | :--- |
|[Least squares (Метод найменших квадратів, МНК)](https://en.wikipedia.org/wiki/Least_squares)|<ul><p>The method of **least squares** is a standard approach in regression analysis to approximate the solution of overdetermined systems (sets of equations in which there are more equations than unknowns) by minimizing the sum of the squares of the residuals made in the results of every single equation.</p><p></p>The most important application is in **data fitting (curve fitting)**. The best fit in the least-squares sense minimizes the sum of squared residuals (a residual being: the difference between an observed value, and the fitted value provided by a model). When the problem has substantial uncertainties in the independent variable (the x variable), then simple regression and least-squares methods have problems; in such cases, the methodology required for fitting errors-in-variables models may be considered instead of that for least squares.</p><p> Least-squares problems fall into two categories: **linear or ordinary least squares** and **nonlinear least squares**, depending on whether or not the residuals are linear in all unknowns. The **linear least-squares** problem occurs in statistical regression analysis; it has a closed-form solution. The **nonlinear** problem is usually solved by iterative refinement; at each iteration the system is approximated by a linear one, and thus the core calculation is similar in both cases.</p></ul>|
