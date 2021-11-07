# Cross-validation

## Model Selection Methods

| Title | Description, Information |
| :---:         |          :--- |
|**K-Folds cross-validator**|<ul><p>KFold divides all the samples in _k_ groups of samples, called folds (if _k = n_, this is equivalent to the Leave One Out strategy), of equal sizes (if possible). The prediction function is learned using _k−1_ folds, and the fold left out is used for test.</p><li>[K-fold](https://scikit-learn.org/stable/modules/cross_validation.html#k-fold)</li><li>[sklearn.model_selection.KFold](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.KFold.html#sklearn.model_selection.KFold)</li></ul>|

### Cross validation of Time Series data

Time series data is characterised by the correlation between observations that are near in time (autocorrelation). However, classical cross-validation techniques such as KFold and ShuffleSplit assume the samples are independent and identically distributed, and would result in unreasonable correlation between training and testing instances (yielding poor estimates of generalisation error) on time series data. Therefore, it is very important to evaluate our model for time series data on the “future” observations least like those that are used to train the model. To achieve this, one solution is provided by TimeSeriesSplit.

| Title | Description, Information |
| :---:         |          :--- |
|**Time Series Split**|<ul><p>TimeSeriesSplit is a variation of k-fold which returns first _k_ folds as train set and the _(k + 1)_- th fold as test set. Note that unlike standard cross-validation methods, successive training sets are supersets of those that come before them. Also, it adds all surplus data to the first training partition, which is always used to train the model.</p><p>This class can be used to cross-validate time series data samples that are observed at fixed time intervals.</p><li>[Time Series Split](https://scikit-learn.org/stable/modules/cross_validation.html#time-series-split)</li><li>[sklearn.model_selection.TimeSeriesSplit](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.TimeSeriesSplit.html)</li></ul>|


## Splitter Functions

| Title | Description, Information |
| :---:         |          :--- |
|**train_test_split**|<ul><p>Split arrays or matrices into random train and test subsets</p><li>[sklearn.model_selection.train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)</li></ul>|
