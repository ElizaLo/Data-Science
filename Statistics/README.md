<img src="https://github.com/ElizaLo/Data-Science/blob/master/img/Statistics.png" width="900" height="150">

## Courses

- **Udacity**:
  - [Intro to Descriptive Statistics](https://www.udacity.com/course/ud827) (Mathematics for Understanding Data) by Kaggle
  - [Intro to Inferential Statistics](https://www.udacity.com/course/ud201) (Making Predictions from Data) by Facebook Blueprint

## YouTube

- [Statistics Playlist 1](https://www.youtube.com/playlist?list=PL5901C68C96DFCAD1) by Professor Leonard
- [Statistics](https://www.youtube.com/playlist?list=PL0o_zxa4K1BVsziIRdfv4Hl4UIqDZhXWV) by The Organic Chemistry

## Web Sites

- [Statology](https://www.statology.org)
- [Statistics By Jim](https://statisticsbyjim.com)
- [Statistics How To](https://www.statisticshowto.com)

## Terminology and Methods

### Sampling

- [Stratified sampling](https://en.wikipedia.org/wiki/Stratified_sampling)

### Errors

| Title | Description, Information |
| :---:         |          :--- |
|[Coefficient of determination, R squared](https://en.wikipedia.org/wiki/Coefficient_of_determination) -> **R<sup>2</sup>**|<ul><li>[R-squared Is Not Valid for Nonlinear Regression](https://statisticsbyjim.com/regression/r-squared-invalid-nonlinear-regression/)</li><li>R-squared provides the relative measure of the percentage of the dependent variable variance that the model explains. R-squared can range from 0 to 100%. Higher R-squared values indicate that the data points are closer to the fitted values. While higher R-squared values are good, they don’t tell you how far the data points are from the regression line.</li></ul>|
|[Standard Error](https://en.wikipedia.org/wiki/Standard_error)|<ul><li>The standard error of the regression provides the absolute measure of the typical distance that the data points fall from the regression line. S is in the units of the dependent variable.</li><li>It tells you straight up how precise the model’s predictions are using the units of the dependent variable. You want lower values of S because it signifies that the distances between the data points and the fitted values are smaller.</li><li>[How to Calculate the Standard Error of the Mean in Python](https://www.statology.org/standard-error-of-mean-python/)</li></ul>|
|[Mean Absolute Error](https://en.wikipedia.org/wiki/Mean_absolute_error), MAE|<ul><li>Measure of errors between paired observations expressing the same phenomenon. Examples of Y versus X include comparisons of predicted versus observed, subsequent time versus initial time, and one technique of measurement versus an alternative technique of measurement</li><li>[How to Calculate Mean Absolute Error in Python](https://www.statology.org/mean-absolute-error-python/)</li></ul>|
|[Mean Squared Error](https://en.wikipedia.org/wiki/Mean_squared_error) (MSE) or Mean Squared Deviation (MSD)|<ul><li>An **estimator** (of a procedure for estimating an unobserved quantity) measures the average of the squares of the errors—that is, the average squared difference between the estimated values and the actual value. MSE is a risk function, corresponding to the expected value of the squared error loss. The fact that MSE is almost always strictly positive (and not zero) is because of randomness or because the estimator does not account for information that could produce a more accurate estimate.</li><li>[How to Calculate Mean Squared Error (MSE) in Python](https://www.statology.org/mean-squared-error-python/)</li></ul>|
|[Mean Squared Prediction Error](https://en.wikipedia.org/wiki/Mean_squared_prediction_error) (MSPE) or Mean Squared Error of the Predictions (MSEP)|<ul><li>In statistics the **mean squared prediction error** or **mean squared error of the predictions** of a smoothing or _**curve fitting**_ procedure is the expected value of the squared difference between the fitted values implied by the predictive function and the values of the (unobservable) function g. It is an inverse measure of the explanatory power of and can be used in the process of cross-validation of an estimated model.</li></ul>|
|[Mean Absolute Scaled Error](https://en.wikipedia.org/wiki/Mean_absolute_scaled_error) (MASE)|<ul><li>In statistics, the **mean absolute scaled error (MASE)** is a measure of the accuracy of forecasts. It is the mean absolute error of the forecast values, divided by the mean absolute error of the in-sample one-step naive forecast.</li></ul>|
|[Root-Mean-Square Deviation](https://en.wikipedia.org/wiki/Root-mean-square_deviation) (RMSD) or root-mean-square error (RMSE)|<ul><li>The **root-mean-square deviation (RMSD)** or **root-mean-square error (RMSE)** is a frequently used measure of the differences between values (sample or population values) predicted by a model or an estimator and the values observed.</li><li>The RMSD represents the square root of the _second sample moment_ of the differences between predicted values and observed values or the quadratic mean of these differences. These deviations are called **residuals** when the calculations are performed over the data sample that was used for estimation and are called errors (or prediction errors) when computed out-of-sample.</li><li>The RMSD serves to aggregate the magnitudes of the errors in predictions for various data points into a single measure of predictive power.</li><li>RMSD is a measure of accuracy, to compare forecasting errors of different models for a particular dataset and not between datasets, as it is scale-dependent.</li></ul> |

#### Other Errors

| Title | Description, Information |
| :---:         |          :--- |
|[Forecast Error (or Residual Forecast Error)](https://en.wikipedia.org/wiki/Forecast_error)|The forecast error is calculated as the expected value minus the predicted value. This is called the **residual error of the prediction**.|
|Mean Forecast Error (or Forecast Bias) |Mean forecast error is calculated as the average of the forecast error values.|

### T-test

- [Two Sample t Test: unequal variances](https://www.real-statistics.com/students-t-distribution/two-sample-t-test-uequal-variances/)
- [Paired Sample T-Test](https://www.statisticssolutions.com/manova-analysis-paired-sample-t-test/?__cf_chl_jschl_tk__=7ce798a5221b0a7eb6119acd7006f1e2f0ea6e92-1614442595-0-Ace7FKLX7nRAMdKS3WD_p10PXYZDFsjL3E6A8v04mSXz_4kAm3WVSWTIzxDkNB_doIOT3tyjZtGm5xzCcO-3f_nOjrFHo-9tO_iOJdrmElBH3iIvume-oCCjIuCCzTs-NXNK1MWtdQll1vZh_GndYerOskzJFCl2uhb5qXFqLzFjPDJTZZ_HzAiEXWamrM2vf5vKYKryqJf7IMcFs9MJ1viq8NRpBQrsaLlKFRiawn8USDgFAMZ5pKdjPgPzIacGVMScGiVh8BlpYMt-2RqAPxTxI9YsQkIp-vsKfdaCuI99X_-gMb4BF98TS7kmqwNrnWsYKg1kqZYe1XNxTsZ67h_xds22jvzx9OOtTdE--gnT)

### Estimation

| Title | Description |
| :---: | :--- |
|[Least squares (Метод найменших квадратів, МНК)](https://en.wikipedia.org/wiki/Least_squares)|<ul><p>The method of **least squares** is a standard approach in regression analysis to approximate the solution of overdetermined systems (sets of equations in which there are more equations than unknowns) by minimizing the sum of the squares of the residuals made in the results of every single equation.</p><p></p>The most important application is in **data fitting (curve fitting)**. The best fit in the least-squares sense minimizes the sum of squared residuals (a residual being: the difference between an observed value, and the fitted value provided by a model). When the problem has substantial uncertainties in the independent variable (the x variable), then simple regression and least-squares methods have problems; in such cases, the methodology required for fitting errors-in-variables models may be considered instead of that for least squares.</p><p> Least-squares problems fall into two categories: **linear or ordinary least squares** and **nonlinear least squares**, depending on whether or not the residuals are linear in all unknowns. The **linear least-squares** problem occurs in statistical regression analysis; it has a closed-form solution. The **nonlinear** problem is usually solved by iterative refinement; at each iteration the system is approximated by a linear one, and thus the core calculation is similar in both cases.</p></ul>|
|[Least Absolute Deviations (LAD)](https://en.wikipedia.org/wiki/Least_absolute_deviations)|<ul><p>**Least absolute deviations (LAD)**, also known as **least absolute errors (LAE), least absolute value (LAV), least absolute residual (LAR), sum of absolute deviations,** or the **L1 norm** condition, is a statistical optimality criterion and the statistical optimization technique that relies on it. Similar to the least squares technique, it attempts to find a function which closely approximates a set of data.</p></ul>|
