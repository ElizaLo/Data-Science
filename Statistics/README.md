<img src="https://github.com/ElizaLo/Data-Science/blob/master/img/Statistics.png" width="900" height="150">

## 🎓 Courses

- **Udacity**:
  - [Intro to Descriptive Statistics](https://www.udacity.com/course/ud827) (Mathematics for Understanding Data) by Kaggle
  - [Intro to Inferential Statistics](https://www.udacity.com/course/ud201) (Making Predictions from Data) by Facebook Blueprint

## 🔴 YouTube

- [Statistics Playlist 1](https://www.youtube.com/playlist?list=PL5901C68C96DFCAD1) by Professor Leonard
- [Statistics](https://www.youtube.com/playlist?list=PL0o_zxa4K1BVsziIRdfv4Hl4UIqDZhXWV) by The Organic Chemistry

## 💻 Web Sites

- [Statology](https://www.statology.org)
- [Statistics By Jim](https://statisticsbyjim.com)
- [Statistics How To](https://www.statisticshowto.com)
- [Learn Math and Stats with Dr. G](https://www.mathandstatistics.com)

## :octocat: GitHub Repositories

| Title | Description, Information |
| :---:         |          :--- |
|[Statistics/ Mathematical Computing Notebooks](https://github.com/tirthajyoti/Stats-Maths-with-Python)|General statistics, mathematical programming, and numerical/scientific computing scripts and notebooks in Python|

## 🛠️ Frameworks

| Title | Description |
| :---:         |          :--- |
|[TensorFlow Probability](https://www.tensorflow.org/probability)|TensorFlow Probability (TFP) is a Python library built on TensorFlow that makes it easy to combine probabilistic models and deep learning on modern hardware (TPU, GPU). It's for data scientists, statisticians, ML researchers, and practitioners who want to encode domain knowledge to understand data and make predictions.|
|[Pyro](https://pyro.ai)|Deep Universal Probabilistic Programming|
|[ArviZ: Exploratory analysis of Bayesian models](https://arviz-devs.github.io/arviz/#)|ArviZ is a Python package for exploratory analysis of Bayesian models. Includes functions for posterior analysis, data storage, sample diagnostics, model checking, and comparison.|
|[PyStan](https://pystan.readthedocs.io/en/latest/)|PyStan is a Python interface to Stan, a package for Bayesian inference.|

-------

# 💠 Terminology and Methods

## 🔹 Sampling

- [Stratified sampling](https://en.wikipedia.org/wiki/Stratified_sampling)

----------------------------

## 🔹 Errors

Keep in mind that **there is no silver bullet, no single best error metric**. The fundamental challenge is, that every statistical measure condenses a large number of data into a single value, so it only provides one projection of the model errors emphasizing a certain aspect of the error characteristics of the model performance _(Chai and Draxler 2014)_.

Therefore it is better to have a more practical and pragmatic view and work with a selection of metrics that fit for your use case or project.

| Title | Description, Information |
| :---:         |          :--- |
|[Standard deviation](https://en.wikipedia.org/wiki/Standard_deviation)|<ul><li>The standard deviation (SD) is a measure of the amount of variation or dispersion of a set of values. A low standard deviation indicates that the values tend to be close to the mean (also called the expected value) of the set,. In contrast, a high standard deviation indicates that the values are spread out over a broader range. The SD of predicted values helps in understanding the dispersion of values in different models.</li></ul>|
|[Coefficient of determination, R squared](https://en.wikipedia.org/wiki/Coefficient_of_determination) -> **R<sup>2</sup>**|<ul><li>[R-squared Is Not Valid for Nonlinear Regression](https://statisticsbyjim.com/regression/r-squared-invalid-nonlinear-regression/)</li><li>R-squared provides the relative measure of the percentage of the dependent variable variance that the model explains. R-squared can range from 0 to 100%. Higher R-squared values indicate that the data points are closer to the fitted values. While higher R-squared values are good, they don’t tell you how far the data points are from the regression line.</li><li>[How To Interpret R-squared in Regression Analysis](https://statisticsbyjim.com/regression/interpret-r-squared-regression/)</li></ul>|
|[Standard Error](https://en.wikipedia.org/wiki/Standard_error)|<ul><li>The standard error of the regression provides the absolute measure of the typical distance that the data points fall from the regression line. S is in the units of the dependent variable.</li><li>It tells you straight up how precise the model’s predictions are using the units of the dependent variable. You want lower values of S because it signifies that the distances between the data points and the fitted values are smaller.</li><li>[How to Calculate the Standard Error of the Mean in Python](https://www.statology.org/standard-error-of-mean-python/)</li></ul>|
|[Relative Standard Deviation (RSD) / Coefficient of Variation (CV)](https://en.wikipedia.org/wiki/Coefficient_of_variation)|<ul><li>The coefficient of variation (CV), also known as relative standard deviation (RSD), is a standardized measure of the dispersion of a probability distribution or frequency distribution. It helps us in understanding how the spread is the data in two different tests</li></ul>|
|Relative Squared Error (RSE)|<ul><li>The relative squared error (RSE) is relative to what it would have been if a simple predictor had been used. More specifically, this simple predictor is just the average of the actual values. Thus, the relative squared error takes the total squared error and normalizes it by dividing by the total squared error of the simple predictor. It can be compared between models whose errors are measured in the different units.</li></ul>|
|[Approximation error](https://en.wikipedia.org/wiki/Approximation_error)|<ul><li>The approximation error in a data value is the discrepancy between an exact value and some approximation to it. This error can be expressed as an absolute error (the numerical amount of the discrepancy) or as a relative error (the absolute error divided by the data value).</li></ul>|

### 💠 **Scale Dependent Metrics:**

| Title | Description, Information |
| :---:         |          :--- |
|[Mean Absolute Error](https://en.wikipedia.org/wiki/Mean_absolute_error), MAE|<ul><li>Measure of errors between paired observations expressing the same phenomenon. Examples of Y versus X include comparisons of predicted versus observed, subsequent time versus initial time, and one technique of measurement versus an alternative technique of measurement</li><li>[How to Calculate Mean Absolute Error in Python](https://www.statology.org/mean-absolute-error-python/)</li></ul>|
|[Mean Squared Error](https://en.wikipedia.org/wiki/Mean_squared_error) (MSE) or Mean Squared Deviation (MSD)|<ul><li>An **estimator** (of a procedure for estimating an unobserved quantity) measures the average of the squares of the errors—that is, the average squared difference between the estimated values and the actual value. MSE is a risk function, corresponding to the expected value of the squared error loss. The fact that MSE is almost always strictly positive (and not zero) is because of randomness or because the estimator does not account for information that could produce a more accurate estimate.</li><li>[How to Calculate Mean Squared Error (MSE) in Python](https://www.statology.org/mean-squared-error-python/)</li></ul>|
|[Root-Mean-Square Deviation](https://en.wikipedia.org/wiki/Root-mean-square_deviation) (RMSD) or Root-Mean-Square error (RMSE)|<ul><li>The **root-mean-square deviation (RMSD)** or **root-mean-square error (RMSE)** is a frequently used measure of the differences between values (sample or population values) predicted by a model or an estimator and the values observed.</li><li>The RMSD represents the square root of the _second sample moment_ of the differences between predicted values and observed values or the quadratic mean of these differences. These deviations are called **residuals** when the calculations are performed over the data sample that was used for estimation and are called errors (or prediction errors) when computed out-of-sample.</li><li>The RMSD serves to aggregate the magnitudes of the errors in predictions for various data points into a single measure of predictive power.</li><li>RMSD is a measure of accuracy, to compare forecasting errors of different models for a particular dataset and not between datasets, as it is scale-dependent.</li><p> </p><p>_**Variations:**_</p><li>Normalized Root Mean Squared Error (Norm RMSEP)</li></ul>|
|[Mean Squared Prediction Error](https://en.wikipedia.org/wiki/Mean_squared_prediction_error) (MSPE) or Mean Squared Error of the Predictions (MSEP)|<ul><li>In statistics the **mean squared prediction error** or **mean squared error of the predictions** of a smoothing or _**curve fitting**_ procedure is the expected value of the squared difference between the fitted values implied by the predictive function and the values of the (unobservable) function g. It is an inverse measure of the explanatory power of and can be used in the process of cross-validation of an estimated model.</li><li>[Mean Squared Error (MSE) vs. Mean Squared Prediction Error (MSPE)](https://stats.stackexchange.com/questions/20741/mean-squared-error-vs-mean-squared-prediction-error)</li></ul>|

### 💠 **Percentage Error Metrics:**

| Title | Description, Information |
| :---:         |          :--- |
|[Mean Absolute Percentage Error (MAPE)](https://en.wikipedia.org/wiki/Mean_absolute_percentage_error)|<ul><li>The mean absolute percentage error (MAPE) is one of the most popular used error metrics in time series forecasting. It is calculated by taking the average (mean) of the absolute difference between actuals and predicted values divided by the actuals.</li><li>[Detailed explanation of MAPE](https://github.com/ElizaLo/Data-Science/tree/master/Statistics#-mean-absolute-percentage-error-mape)</li></ul>|
|[Symmetric Mean Absolute Percentage Error (sMAPE)](https://en.wikipedia.org/wiki/Symmetric_mean_absolute_percentage_error)|<ul><li>To avoid the asymmetry of the MAPE a new error metric was proposed. The Symmetric Mean Absolute Percentage Error (sMAPE). The sMAPE is probably one of the most controversial error metrics, since not only different definitions or formulas exist but also critics claim that this metric is not symmetric as the name suggests.</li><li>[]()</li><li>[Detailed explanation of sMAPE](https://github.com/ElizaLo/Time-Series/blob/main/Metrics/README.md#-symmetric-mean-absolute-percentage-error-smape)</li></ul>|
|Weighted Mean Absolute Percentage Error (wMAPE)|<ul><li>[Calculating demand forecast accuracy](https://en.wikipedia.org/wiki/Demand_forecasting#Calculating_demand_forecast_accuracy)</li></ul>|

### 💠 **Relative Error Metrics:**

| Title | Description, Information |
| :---:         |          :--- |
|Relative Absolute Error (RAE)|<ul><li>Relative Absolute Error (RAE) is a way to measure the performance of a predictive model. RAE is not to be confused with relative error, which is a general measure of precision or accuracy for instruments like clocks, rulers, or scales. It is expressed as a ratio, comparing a mean error (residual) to errors produced by a trivial or naive model. A good forecasting model will produce a ratio close to zero; A poor model (one that’s worse than the naive model) will produce a ratio greater than one.</li><li>It is very similar to the relative squared error in the sense that it is also relative to a simple predictor, which is just the average of the actual values. In this case, though, the error is just the total absolute error instead of the total squared error. Thus, the relative absolute error takes the total absolute error and normalizes it by dividing by the total absolute error of the simple predictor.</li></ul>|
|Median Relative Absolute Error (MdRAE)|<ul><li>The Median Relative Absolute Error (MdRAE) calculates the median of the difference between the absolute error of our forecast to the absolute error of a benchmark model.</li></ul>|
|Geometric Mean Relative Absolute Error (GMRAE)|<ul><li>Geometric Mean Relative Absolute Error (GMRAE) compares the errors of our forecast with the one of a defined baseline model. However, instead of calculating the median, the GMRAE, as the name implies, calculates the geometric mean of our relative errors.</li></ul>|

### 💠 **Scale-Free Error Metrics:**

| Title | Description, Information |
| :---:         |          :--- |
|[Mean Absolute Scaled Error](https://en.wikipedia.org/wiki/Mean_absolute_scaled_error) (MASE)|<ul><li>In statistics, the **mean absolute scaled error (MASE)** is a measure of the accuracy of forecasts. It is the mean absolute error of the forecast values, divided by the mean absolute error of the in-sample one-step naive forecast.</li></ul>|

### 💠 Other Errors

| Title | Description, Information |
| :---:         |          :--- |
|[Forecast Error (or Residual Forecast Error)](https://en.wikipedia.org/wiki/Forecast_error)|The forecast error is calculated as the expected value minus the predicted value. This is called the **residual error of the prediction**.|
|Mean Forecast Error (or Forecast Bias) |Mean forecast error is calculated as the average of the forecast error values.|
|[Tracking signal](https://en.wikipedia.org/wiki/Tracking_signal)|Monitors any forecasts that have been made in comparison with actuals, and warns when there are unexpected departures of the outcomes from the forecasts.|
|Compounding Error|<p>Compounding error is when deviation of one feature, or the process used to measure that feature, directly affects the measurement of another feature.</p><p>In the training process, there’s never a chance to see compounding errors. The model is trained to predict the next token based on a human-generated context. If it gets one token wrong by generating a bad distribution, the next token uses the “correct” human generated context independent of the last prediction. During generation it is forced to complete its own automatically-generated context, a setting it has not considered during training.</p><ul><li>[The Affects of Compounding Error](https://www.havenmetrology.com/the-power-of-compounding-error/#:~:text=Compounding%20error%20is%20when%20deviation,the%20measurement%20of%20another%20feature.)</li><li>[What are Compounding Errors and How are They Affecting Your Business?](https://www.quadient.com/en-int/blog/what-are-compounding-errors-and-how-are-they-affecting-your-business)</li></ul>|

----

## 🔹 Metrics

> Time Series Forecast Error Metrics
<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/Overview%20Time%20Series_Forecast_Error_Metrics.png" width="971" height="322"/>

| Title | Description, Information |
| :---:         |          :--- |
|[Mean Reciprocal Rank](https://en.wikipedia.org/wiki/Mean_reciprocal_rank)|<p>The mean reciprocal rank is a statistic measure for evaluating any process that produces a list of possible responses to a sample of queries, ordered by probability of correctness.</p><p>This metric can help distinguish between answers that were close to being right or far from being right (e.g., a score of 1 if the correct document is rank 1, a score of ½ if rank 2, a score of ⅓ if rank 3, etc.)</p>|

### 📰 Articles

- [Ways to Evaluate Regression Models](https://towardsdatascience.com/ways-to-evaluate-regression-models-77a3ff45ba70)
- [Choosing the correct error metric: MAPE vs. sMAPE](https://towardsdatascience.com/choosing-the-correct-error-metric-mape-vs-smape-5328dec53fac)
- [Time Series Forecast Error Metrics You Should Know](https://towardsdatascience.com/time-series-forecast-error-metrics-you-should-know-cc88b8c67f27)

### :octocat: GitHub

- [Regression Metrics Python](https://github.com/mtortora-ai/Regression-Metrics-Python)

### 📄 Papers

- [Another look at measures of forecast accuracy](https://robjhyndman.com/papers/mase.pdf) by Rob J Hyndman

## 🔹 Scale Dependent Metrics

Many popular metrics are referred to as **scale-dependent** _(Hyndman, 2006)_. Scale-dependent means the error metrics are **expressed in the units** _(i.e. Dollars, Inches, etc.)_ of the underlying data.

The main advantage of scale dependent metrics is that they are usually **easy to calculate** and **interpret**. However, they can **not be used to compare different series**, because of their **scale dependency** _(Hyndman, 2006)_.

> Please note here that _Hyndman (2006)_ includes Mean Squared Error into a scale-dependent group (claiming that the error is “on the same scale as the data”). However, Mean Squared Error has a dimension of the squared scale/unit. To bring MSE to the data’s unit we need to take the square root which leads to another metric, the RMSE. _(Shcherbakov et al., 2013)_

### 🔸 Mean Absolute Error (MAE)

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/MAE.png" width="304" height="105"/>

The **Mean Absolute Error (MAE)** is calculated by taking the mean of the **absolute differences between the actual values** (also called _y_) **and the predicted values** (_y_hat_).

It is **easy to understand** (even for business users) and **to compute**. It is recommended for **assessing accuracy on a single series** _(Hyndman, 2006)_. 

However if you want to compare different series (with different units) it is not suitable. Also you should **not use** it if you want to **penalize outliers**.

```python
import numpy as np

def mae(y, y_hat):
    return np.mean(np.abs(y - y_hat))
```

### 🔸 Mean Squared Error (MSE)

If you want to put **more attention on outliers (huge errors)** you can consider the **Mean Squared Error (MSE)**. Like it’s name implies it takes the mean of the squared errors (differences between _y_ and _y_hat_). 

Due to its squaring, it **heavily weights large errors more than small ones**, which can be in some situations a **disadvantage**. Therefore the MSE is suitable for situations where you **really want to focus on large errors**. 

Also keep in mind that due to its squaring the metric **loses its unit**.

```python
import numpy as np

def mse(y, y_hat):
    return np.mean(np.square(y - y_hat))
```

### 🔸 Root Mean Squared Error (RMSE)

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/RMSE.png" width="326" height="119"/>

To **avoid the MSE’s loss of its unit** we can take the square root of it. The outcome is then a new error metric called the Root Mean Squared Error (RMSE).

It comes with the same **advantages** as its siblings MAE and MSE. However, like MSE, it is also **sensitive to outliers**.

Some authors like _Willmott and Matsuura (2005)_ argue that the RMSE is an inappropriate and misinterpreted measure of an average error and recommend MAE over RMSE.

However, Chai and Drexler (2014) partially refuted their arguments and **recommend RMSE over MAE for your model optimization** as well as for **evaluating different models where the error distribution is expected to be Gaussian**.

## 🔹 Percentage Error Metrics

As we know from the previous chapter, **scale dependent metrics are not suitable for comparing different time series**.

Percentage Error Metrics solve this problem. They are **scale independent** and **used to compare forecast performance between different time series**. However, their **weak spots are zero values in a time series**. Then they become **infinite or undefined** which makes them not interpretable _(Hyndman 2006)_.

### 🔸 Mean Absolute Percentage Error (MAPE)

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/MAPE.png" width="355" height="119"/>

The mean absolute percentage error (MAPE) is one of the **most popular used error metrics** in time series forecasting. It is calculated by taking the average (mean) of the absolute difference between actuals and predicted values divided by the actuals.

> _Please note, some MAPE formulas do not multiply the result(s) with 100. However, the MAPE is presented as a percentage unit so I added the multiplication._

MAPE’s **advantages** are it’s **scale-independency** and **easy interpretability**. As said at the beginning, percentage error metrics can be used to compare the outcome of multiple time series models with different scales.

However, MAPE also comes with some **disadvantages**. First, **it generates infinite or undefined values for zero or close-to-zero actual values** _(Kim and Kim 2016)_.

Second, it also puts a **heavier penalty on negative than on positive errors** which leads to an **asymmetry** _(Hyndman 2014)_.

And last but not least, MAPE **can not be used when using percentages make no sense**. This is for example the case when measuring temperatures. The units Fahrenheit or Celsius scales have relatively arbitrary zero points, and it makes no sense to talk about percentages _(Hyndman and Koehler, 2006)_.

```python
import numpy as np

def mape(y, y_hat):
    return np.mean(np.abs((y - y_hat)/y)*100)
```

### 🔸 Symmetric Mean Absolute Percentage Error (sMAPE)

To **avoid the asymmetry** of the MAPE a new error metric was proposed. The **Symmetric Mean Absolute Percentage Error (sMAPE)**. The sMAPE is probably one of the **most controversial** error metrics, since not only different definitions or formulas exist but also critics claim that this metric **is not symmetric** as the name suggests _(Goodwin and Lawton, 1999)_.

The original idea of an **“adjusted MAPE”** was proposed by _Armstrong (1985)_. However by his definition the **error metric can be negative or infinite** since the values in the denominator **are not set absolute** (which is then correctly mentioned as a disadvantage in some articles that follow his definition).

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/MAPE_formula.png" width="458" height="71"/>

_Makridakis (1993)_ proposed a similar metric and called it SMAPE. His formula which can be seen below **avoids the problems Armstrong’s formula** had by setting the values in the denominator to absolute _(Hyndman, 2014)_.

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/sMAPE_%20Makridakis_formula.png" width="385" height="94"/>

> _**Note:** Makridakis (1993) proposed the formula above in his paper “Accuracy measures: theoretical and practical concerns’’. Later in his publication (Makridakis and Hibbon, 2000) “The M3-Competition: results, conclusions and implications’’ he used Armstrong’s formula (Hyndman, 2014). This fact has probably also contributed to the confusion about SMAPE’s different definitions._

The sAMPE is the average across all forecasts made for a given horizon. It’s **advantages** are that it **avoids MAPE’s problem of large errors** when y-values are close to zero and the large difference between the absolute percentage errors when y is greater than y-hat and vice versa. Unlike MAPE which has no limits, **it fluctuates between 0% and 200%** _(Makridakis and Hibon, 2000)_.

For the **sake of interpretation** there is also a **slightly modified version of SMAPE** that ensures that the metric’s results **will be always between 0% and 100%**:

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/sMAPE_%20modified.png" width="385" height="94"/>

The following code snippet contains the sMAPE metric proposed by _Makridakis (1993)_ and the modified version.

```python
import numpy as np

# SMAPE proposed by Makridakis (1993): 0%-200%
def smape_original(a, f):
    return 1/len(a) * np.sum(2 * np.abs(f-a) / (np.abs(a) + np.abs(f))*100)


# adjusted SMAPE version to scale metric from 0%-100%
def smape_adjusted(a, f):
    return (1/a.size * np.sum(np.abs(f-a) / (np.abs(a) + np.abs(f))*100))
```

As mentioned at the beginning, there are **controversies around the sMAPE**. And they are true. _Goodwin and Lawton (1999)_ pointed out that sMAPE **gives more penalties to under-estimates more than to over-estimates** _(Chen et al., 2017)_. _Cánovas (2009)_ proofs this fact with an easy example.

- **_Table 1:_** Example with a **symmetric sMAPE**:

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/symmetric_sMAPE.png" width="632" height="127"/>

- **_Table 2:_** Example with an **asymmetric sMAPE**:

<img src="https://github.com/ElizaLo/Data-Science/blob/master/Statistics/img/asymmetric_sMAPE.png" width="632" height="127"/>

Starting with **_Table 1_** we have two cases. In **case 1** our actual value **_y_** is **100** and the prediction **_y_hat_** **150**. This leads to a sMAPE value of 20 %. **Case 2** is the opposite. Here we have an actual value _**y**_ of **150** and a prediction **_y_hat_** of **100**. This also leads to a sMAPE of 20 %. 

Let us now have a look at **_Table 2_**. We also have here two cases and as you can already see the sMAPE values **are not the same anymore**. The second case **leads to a different SMAPE value** of 33 %.

**Modifying the forecast while holding fixed actual values and absolute deviation do not produce the same sMAPE’s value. Simply biasing the model without improving its accuracy should never produce different error values _(Cánovas, 2009)_.**

## 🔹 Metric/Error choice

- As you have seen there is **no silver bullet, no single best error metric**. Each category or metric has its **advantages** and **weaknesses**. So it **always depends on your individual use case** or **purpose and your underlying data**. It is important **not to just look at one single error metric** when evaluating your model’s performance. It is necessary to measure several of the main metrics described above in order to analyze several parameters such as deviation, symmetrical deviation and largest outliers.
- If all series **are on the same scale**, the **data preprocessing procedures** were performed (data cleaning, anomaly detection) and the task is **to evaluate the forecast performance** then the **MAE can be preferred** because it is simpler to explain _(Hyndman and Koehler, 2006; Shcherbakov et al., 2013)_.
- _Chai and Draxler (2014)_ recommend to **prefer RMSE over MAE** when the error distribution is **expected to be Gaussian**.
- In case the data **contain outliers** it is advisable to apply scaled measures like **MASE**. In this situation the **horizon should be large enough, no identical values should be**, the normalized factor **should be not equal to zero** _(Shcherbakov et al., 2013)_.

### 📰 Articles

- [Metric choice](https://stephenallwright.com/metric-choice/)
- [Understanding metric values](https://stephenallwright.com/metric-values/)
- [Time Series Forecast Error Metrics You Should Know](https://towardsdatascience.com/time-series-forecast-error-metrics-you-should-know-cc88b8c67f27)

## 🔹 Accuracy (Error) Rate

### 📰 Articles

- [What is Accuracy Rate?](https://kimola.com/support/cognitive/what-is-accuracy-rate)
- [Accuracy (error rate)](https://deepai.org/machine-learning-glossary-and-terms/accuracy-error-rate)

## 🔹 Margin of Error

A statistical value that determines, with a certain degree of probability, the maximum value by which the results of the sample differ from the results of the general population. It is half the length of the confidence interval.

> **Предельная ошибка выборки** (также _предельная погрешность выборки_) — статистическая величина, определяющая, с определенной степенью вероятности, максимальное значение, на которое результаты выборки отличаются от результатов генеральной совокупности. Составляет половину длины доверительного интервала.

### 📰 Articles

- [Margin of error](https://en.wikipedia.org/wiki/Margin_of_error), Wikipedia

## 🔹 Confidence interval

### 🔺 Confidence limits

- [Confidence Limits: Definition](https://www.statisticshowto.com/confidence-limits-definition/)
- [Confidence Limits for the Mean](https://www.itl.nist.gov/div898/handbook/eda/section3/eda352.htm)

### 🔺 Using the Empirical Rule (95-68-34 or (50-34-14)

#### 📰 Articles

- [Confidence interval](https://en.wikipedia.org/wiki/Confidence_interval)
- [Confidence interval](https://en.wikipedia.org/wiki/Confidence_interval)
- [Understanding Confidence Intervals](https://www.scribbr.com/statistics/confidence-interval/)
- [Using the Empirical Rule (95-68-34 or (50-34-14)](https://www.mathandstatistics.com/learn-stats/probability-and-percentage/using-the-empirical-rule-95-68-34-or-50-34-14)
- [The Empirical Rule](https://online.stat.psu.edu/stat200/lesson/2/2.2/2.2.7)

-----

## 🔹 Standard score

### 📰 Articles

- [Standard score](https://en.wikipedia.org/wiki/Standard_score)

-----


## 🔹 Confusion matrix

- [Confusion matrix](https://en.wikipedia.org/wiki/Confusion_matrix)

### 🛠️ Tools

| Title | Description, Information |
| :---:         |          :--- |
|[Confusion Matrix in Python](https://github.com/wcipriano/pretty-print-confusion-matrix)|Confusion Matrix in Python: plot a pretty confusion matrix (like Matlab) in python using seaborn and matplotlib|

----------------------------

## 🔹 T-test

- [Two Sample t Test: unequal variances](https://www.real-statistics.com/students-t-distribution/two-sample-t-test-uequal-variances/)
- [Paired Sample T-Test](https://www.statisticssolutions.com/manova-analysis-paired-sample-t-test/?__cf_chl_jschl_tk__=7ce798a5221b0a7eb6119acd7006f1e2f0ea6e92-1614442595-0-Ace7FKLX7nRAMdKS3WD_p10PXYZDFsjL3E6A8v04mSXz_4kAm3WVSWTIzxDkNB_doIOT3tyjZtGm5xzCcO-3f_nOjrFHo-9tO_iOJdrmElBH3iIvume-oCCjIuCCzTs-NXNK1MWtdQll1vZh_GndYerOskzJFCl2uhb5qXFqLzFjPDJTZZ_HzAiEXWamrM2vf5vKYKryqJf7IMcFs9MJ1viq8NRpBQrsaLlKFRiawn8USDgFAMZ5pKdjPgPzIacGVMScGiVh8BlpYMt-2RqAPxTxI9YsQkIp-vsKfdaCuI99X_-gMb4BF98TS7kmqwNrnWsYKg1kqZYe1XNxTsZ67h_xds22jvzx9OOtTdE--gnT)

----------------------------

## 🔹 Estimation

| Title | Description |
| :---: | :--- |
|[Least squares (Метод найменших квадратів, МНК)](https://en.wikipedia.org/wiki/Least_squares)|<ul><p>The method of **least squares** is a standard approach in regression analysis to approximate the solution of overdetermined systems (sets of equations in which there are more equations than unknowns) by minimizing the sum of the squares of the residuals made in the results of every single equation.</p><p></p>The most important application is in **data fitting (curve fitting)**. The best fit in the least-squares sense minimizes the sum of squared residuals (a residual being: the difference between an observed value, and the fitted value provided by a model). When the problem has substantial uncertainties in the independent variable (the x variable), then simple regression and least-squares methods have problems; in such cases, the methodology required for fitting errors-in-variables models may be considered instead of that for least squares.</p><p> Least-squares problems fall into two categories: **linear or ordinary least squares** and **nonlinear least squares**, depending on whether or not the residuals are linear in all unknowns. The **linear least-squares** problem occurs in statistical regression analysis; it has a closed-form solution. The **nonlinear** problem is usually solved by iterative refinement; at each iteration the system is approximated by a linear one, and thus the core calculation is similar in both cases.</p></ul>|
|[Least Absolute Deviations (LAD)](https://en.wikipedia.org/wiki/Least_absolute_deviations)|<ul><p>**Least absolute deviations (LAD)**, also known as **least absolute errors (LAE), least absolute value (LAV), least absolute residual (LAR), sum of absolute deviations,** or the **L1 norm** condition, is a statistical optimality criterion and the statistical optimization technique that relies on it. Similar to the least squares technique, it attempts to find a function which closely approximates a set of data.</p></ul>|

----------------------------

# 💠 Models

## 🔹 Generalized additive model

### 📰 Articles

- [Generalized additive model](https://en.wikipedia.org/wiki/Generalized_additive_model)

------

# 💠 Bayesian Statistics
  
## 📚 Bayesian modeling and related books:

- [The Elements of Statistical Learning: Data Mining, Inference, and Prediction.](https://web.stanford.edu/~hastie/ElemStatLearn/)
- C.P. Robert: The Bayesian choice (advanced)
- Gelman, Carlin, Stern, Rubin: Bayesian data analysis (nice easy older book)
- Congdon: Applied Bayesian modelling; Bayesian statistical modelling (relatively nice books for references)
- Casella, Robert: Introducing Monte Carlo methods with R (nice book about MCMC)
- Robert, Casella: Monte Carlo Statistical Methods
- some parts of Bishop: Pattern recognition and machine learning (very nice book for engineers)
- Puppy book from Kruschke
- [Mathematical Statistics](https://books.google.cz/books/about/Mathematical_Statistics.html?id=_bEPBwAAQBAJ&source=kp_cover&redir_esc=y)
- [Think Stats 2e](https://greenteapress.com/wp/think-stats-2e/)

### 📰 Articles

- [Variational Bayesian methods](https://en.wikipedia.org/wiki/Variational_Bayesian_methods)

----

# 💠 Causal Inference

> Correlation does not imply causation

## 🎓 More online lectures, courses, papers, books, etc. on Causality:

- **Coursera:**
  - [A Crash Course in Causality: Inferring Causal Effects from Observational Data](https://www.coursera.org/learn/crash-course-in-causality)
  
- [Powerful Concepts in Social Science](https://www.youtube.com/c/ModUPowerfulConceptsinSocialScience/playlists?view=50&sort=dd&shelf_id=6) playlists, Duke
- 4 lectures on causality by J.Peters (8 h), [MIT Statistics and Data Science Center, 2017](https://stat.mit.edu/news/four-lectures-causality/)
- Causality tutorial by D.Janzing and S.Weichwald (4 h), [Conference on Cognitive Computational Neuroscience 2019](https://sweichwald.de/slides.html#ccn2019)
- Course on causality by S.Bauer and B.Schölkopf (3 h), [Machine Learning Summer School 2020](https://www.youtube.com/watch?v=btmJtThWmhA)
- Course on causality by D.Janzing and B.Schölkopf (3 h), [Machine Learning Summer School 2013](http://mlss.tuebingen.mpg.de/2013/speakers.html)
- [Causal Inference 3: Counterfactuals](https://www.inference.vc/causal-inference-3-counterfactuals/)
- [Causality for Machine Learning, Bernhard Schölkopf, 2019](https://arxiv.org/abs/1911.10500)
- [Elements of Causal Inference](https://www.dropbox.com/s/dl/gkmsow492w3oolt/11283.pdf)
- [Causal Structure Learning,Christina Heinze-Deml, Marloes H. Maathuis, Nicolai Meinshausen, 2017](https://arxiv.org/abs/1706.09141)
- [Causal inference in statistics: An overview, 2009](https://ftp.cs.ucla.edu/pub/stat_ser/r350.pdf)
- [JUDEA PEARL, MADELYN GLYMOUR, NICHOLAS P. JEWELL CAUSAL INFERENCE IN STATISTICS: A PRIMER](http://bayes.cs.ucla.edu/PRIMER/)
- [JUDEA PEARL - CAUSALITY, 2nd Edition, 2009](http://bayes.cs.ucla.edu/BOOK-2K/)
- [Causation, Prediction, and Search, Second Edition](https://mitpress.mit.edu/books/causation-prediction-and-search-second-edition)
- [Learning DAGs with Continuous Optimization](https://blog.ml.cmu.edu/2020/04/10/learning-dags-with-continuous-optimization/)
- [Causality in cognitive neuroscience: concepts, challenges, and distributional robustness](https://arxiv.org/abs/2002.06060)
- [Active Invariant Causal Prediction: Experiment Selection through Stability, Juan L Gamella, Christina Heinze-Deml, 2020](https://arxiv.org/abs/2006.05690)
- [Investigating Causal Relations by Econometric Models and Cross-spectral Methods, 1969](https://www.jstor.org/stable/1912791?seq=1)
- [Fast Greedy Equivalence Search (FGES) Algorithm for Continuous Variables](https://www.ccd.pitt.edu/wiki/index.php/Fast_Greedy_Equivalence_Search_(FGES)_Algorithm_for_Continuous_Variables)
- [Greedy Fast Causal Inference (GFCI) Algorithm for Continuous Variables](https://www.ccd.pitt.edu/wiki/index.php/Greedy_Fast_Causal_Inference_(GFCI)_Algorithm_for_Continuous_Variables)
- [awesome-causality-algorithms](https://github.com/rguo12/awesome-causality-algorithms)

## 📄 Casual Machine Learning (Papers)

- [Causal Decision Trees](https://arxiv.org/pdf/1508.03812.pdf), Jiuyong Li, Saisai Ma, Thuc Duy Le, Lin Liu and Jixue Liu, 2015
- [Discovery of Causal Rules Using Partial Association](https://ieeexplore.ieee.org/document/6413892), 2012
- [Causal Inference in Data Science From Prediction to Causation](https://www.datacouncil.ai/talks/causal-inference-in-data-science-from-prediction-to-causation), 2016

## 🔹 Experimental designs for casual learning:

- Matching
- Incident user design
- Active comparator
- Instrumental variables estimation
- Difference-in-differences
- Regression discontinuity design
- Modeling
