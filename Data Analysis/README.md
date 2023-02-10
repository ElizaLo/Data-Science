<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/Data_Analysis.png" width="1050" height="150"/>

# ✅ To check:

- Is the data  **Independent and Identically Distributed** (i.i.d.)?

# :books: Books

- [Hands on Exploratory Data analysis with Python](https://github.com/PacktPublishing/Hands-on-Exploratory-Data-Analysis-with-Python), published by Packt

# 🛠️ Tools

| Title | Description |
| :---:         |          :--- |
|[Deepchecks](https://docs.deepchecks.com/en/stable/index.html)|Deepchecks is the leading tool for validating your machine learning models and data, and it enables doing so with minimal effort. Deepchecks accompanies you through various validation needs such as verifying your data’s integrity, inspecting its distributions, validating data splits, evaluating your model and comparing between different models|
|[pandas_profiling](https://pandas-profiling.github.io/pandas-profiling/docs/master/rtd/index.html)|Generates profile reports from a pandas `DataFrame`.|
|[Great Expectations](https://github.com/great-expectations/great_expectations)|Great Expectations helps data teams eliminate pipeline debt, through data testing, documentation, and profiling.|

## 📈 Visualization

| Title | Description |
| :---:         |          :--- |
|[Vega-Altair: Declarative Visualization in Python](https://altair-viz.github.io)|With Vega-Altair, you can spend more time understanding your data and its meaning. Altair’s API is simple, friendly and consistent and built on top of the powerful Vega-Lite visualization grammar. This elegant simplicity produces beautiful and effective visualizations with a minimal amount of code.|

# ❓ How To Select Columns Using Prefix/Suffix of Column Names in Pandas?

## 🔹 Select Columns with a Prefix using Pandas filter

For example, if we are interested in selecting columns starting with `“lifeExp”`, the regular expression for the pattern is `“^lifeExp”`. In the regular expression `“^”` represents we are interested in patterns that starts with. So our argument for `“regexp”` will be `regexp=’^lifeExp’`.

```python
df.filter(regex='^lifeExp',axis=1).head()
```

## 🔹 Select Columns with a suffix using Pandas filter

Let us select columns with names ending with a suffix in Pandas dataframe using filter function. As before, we need to come up with regular expression for the pattern we are interested in. Here our pattern is column names ending with a suffix.

Let us select columns ending with `“1957”` and the regular expression pattern is `‘1957$’`, where the dollar symbol at the end represents the pattern ending with `“1957”`.

We use `regex=’1957$’` as argument to the Pandas’ filter function and addition to `axis=1`. We get a data frame with three columns that have names ending with 1957.

```python
df.filter(regex='1957$',axis=1).head()
```

### 📰 Articles

- [How To Select Columns Using Prefix/Suffix of Column Names in Pandas?](https://cmdlinetips.com/2019/04/how-to-select-columns-using-prefix-suffix-of-column-names-in-pandas/)

# 💠 Missing Values

## 📰 Atricles

- []()
