<img src="https://raw.githubusercontent.com/ElizaLo/Data-Science/master/img/Data_Pre_Processing.png" width="1050" height="150"/>


- Cleaning Data
- Check Missing Values
- Numerical Imputation
- Categorical Imputation
- Handling Outliers
  - Outlier Detection with Standard Deviation
  - Outlier Detection with Percentiles
- Binning
- Data Manipulations
  - Add String to Each Value in Column
  - Drop Rows that Contain a Specific Value

# 🔹 Cleaning Data

  - [Guide to Data Preprocessing for Data Science](https://medium.com/@vinitasilaparasetty/guide-to-data-preprocessing-for-data-science-d2447a09ba4c)
  - [Data Preprocessing: 6 Necessary Steps for Data Scientists](https://hackernoon.com/what-steps-should-one-take-while-doing-data-preprocessing-502c993e1caa)
  - [What Is Data Preprocessing in ML?](https://serokell.io/blog/data-preprocessing)
  - [Guide to Data Cleaning for Data Science](https://medium.com/@vinitasilaparasetty/guide-to-data-cleaning-for-data-science-53e056c8eb98)
  - [Data Cleaning and Preprocessing for Beginners](https://medium.com/sciforce/data-cleaning-and-preprocessing-for-beginners-25748ee00743)

# 🔹 Check Missing Values

- The most simple solution to the missing values is to drop the rows or the entire column. There is not an optimum threshold for dropping but you can use 70% as an example value and try to drop the rows and columns which have missing values with higher than this threshold.
  
  ```@python
  threshold = 0.7
  #Dropping columns with missing value rate higher than threshold
  data = data[data.columns[data.isnull().mean() < threshold]]

  #Dropping rows with missing value rate higher than threshold
  data = data.loc[data.isnull().mean(axis=1) < threshold]
  ```
  
# 🔹 Numerical Imputation

Considering a possible **default value of missing values** in the column. For example, if you have a column that only has 1 and NA, then it is likely that the **NA** rows correspond to **0**.

Except for the case of having a default value for missing values, I think the best imputation way is to use the **medians of the columns**. As the averages of the columns are sensitive to the outlier values, while medians are more solid in this respect.

  ```@python
  #Filling all missing values with 0
  data = data.fillna(0)

  #Filling missing values with medians of the columns
  data = data.fillna(data.median())
  ```
  
# 🔹 Categorical Imputation

Replacing the missing values with the maximum occurred value in a column is a good option for handling categorical columns. But if you think the values in the column are distributed uniformly and there is not a dominant value, imputing a category like “Other” might be more sensible, because in such a case, your imputation is likely to converge a random selection.

  ```@python
  #Max fill function for categorical columns
  data['column_name'].fillna(data['column_name'].value_counts()
  .idxmax(), inplace=True)
  ```

# 🔹 Handling Outliers

## 🔸 Outlier Detection with Standard Deviation 

If a value has a distance to the average higher than x * standard deviation, it can be assumed as an outlier. Then what x should be?

There is no trivial solution for x, but usually, a value between 2 and 4 seems practical.

    ```@python
    #Dropping the outlier rows with standard deviation
    factor = 3
    upper_lim = data['column'].mean () + data['column'].std () * factor
    lower_lim = data['column'].mean () - data['column'].std () * factor

    data = data[(data['column'] < upper_lim) & (data['column'] > lower_lim)]
    ```
    
In addition, **z-score** can be used instead of the formula above. **Z-score** (or standard score) standardizes the distance between a value and the mean using the standard deviation.

## 🔸 Outlier Detection with Percentiles

Another mathematical method to detect outliers is to use percentiles. You can assume a certain percent of the value from the top or the bottom as an outlier. The key point is here to set the percentage value once again, and this depends on the distribution of your data as mentioned earlier.

Additionally, a common mistake is using the percentiles according to the range of the data. In other words, if your data ranges from 0 to 100, your top 5% is not the values between 96 and 100. Top 5% means here the values that are out of the 95th percentile of data.

    ```@python
    #Dropping the outlier rows with Percentiles
    upper_lim = data['column'].quantile(.95)
    lower_lim = data['column'].quantile(.05)

    data = data[(data['column'] < upper_lim) & (data['column'] > lower_lim)]
    ```
## :question: An Outlier Dilemma: Drop or Cap

 Another option for handling outliers is to **cap** them instead of dropping. So you can keep your data size and at the end of the day, it might be better for the final model performance.
    
On the other hand, capping can affect the distribution of the data, thus it better not to exaggerate it.

    ```@python
    # Capping the outlier rows with Percentiles
    upper_lim = data['column'].quantile(.95)
    lower_lim = data['column'].quantile(.05)
    
    data.loc[(df[column] > upper_lim),column] = upper_lim
    data.loc[(df[column] < lower_lim),column] = lower_lim
    ```
# 🔹 Binning

  Binning can be applied on both categorical and numerical data:
  
  ```@python
  # Numerical Binning Example
  
  Value      Bin       
  0-30   ->  Low       
  31-70  ->  Mid       
  71-100 ->  High
  
  # Categorical Binning Example
  
  Value      Bin       
  Spain  ->  Europe      
  Italy  ->  Europe       
  Chile  ->  South America
  Brazil ->  South America
  ```

The main motivation of binning is to make the model more **robust** and **prevent overfitting**, however, it has a cost to the performance. Every time you bin something, you sacrifice information and make your data more regularized.

The trade-off between **performance** and **overfitting** is the key point of the binning process. In my opinion, for numerical columns, except for some obvious overfitting cases, binning might be redundant for some kind of algorithms, due to its effect on model performance.
  
However, for categorical columns, the labels with low frequencies probably affect the robustness of statistical models negatively. Thus, assigning a general category to these less frequent values helps to keep the robustness of the model. _For example,_ if your data size is **100,000** rows, it might be a good option to unite the labels with a count less than **100** to a new category like **“Other”**.

  ```@python
  # Numerical Binning Example
  
  data['bin'] = pd.cut(data['value'], bins=[0,30,70,100], labels=["Low", "Mid", "High"])
     value   bin
  0      2   Low
  1     45   Mid
  2      7   Low
  3     85  High
  4     28   Low
  
  
  # Categorical Binning Example
       Country
  0      Spain
  1      Chile
  2  Australia
  3      Italy
  4     Brazil
  conditions = [
      data['Country'].str.contains('Spain'),
      data['Country'].str.contains('Italy'),
      data['Country'].str.contains('Chile'),
      data['Country'].str.contains('Brazil')]

  choices = ['Europe', 'Europe', 'South America', 'South America']

  data['Continent'] = np.select(conditions, choices, default='Other')
  
       Country      Continent
  0      Spain         Europe
  1      Chile  South America
  2  Australia          Other
  3      Italy         Europe
  4     Brazil  South America
  ```

# 🔹 Drop Duplicates

- [pandas.DataFrame.duplicated](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.duplicated.html)
  - [Pandas : Find duplicate rows in a Dataframe based on all or selected columns using DataFrame.duplicated() in Python](https://thispointer.com/pandas-find-duplicate-rows-in-a-dataframe-based-on-all-or-selected-columns-using-dataframe-duplicated-in-python/)
    
    **Show all duplicated rows**
    ```@python
    df[df.duplicated(keep = False)]
    ```
  - [pandas.DataFrame.drop_duplicates](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop_duplicates.html)
- [Dropping Rows And Columns In pandas Dataframe](https://chrisalbon.com/python/data_wrangling/pandas_dropping_column_and_rows/)
- 

# 🔹 Data Manipulations

## 🔸 Add String to Each Value in Column

```python
df['my_column'] = 'some_string' + df['my_column'].astype(str)
```

📰 **Articles:**

- [Pandas: How to Add String to Each Value in Column](https://www.statology.org/pandas-add-string-to-column/)

## 🔸 Drop Rows that Contain a Specific Value

```python
#drop rows that contain specific 'value' in 'column_name'
df = df[df.column_name != value]
```

📰 **Articles:**

- [Pandas: How to Drop Rows that Contain a Specific Value](https://www.statology.org/pandas-drop-rows-with-value/)

------------------------------------

# 📰 Articles

- [Fundamental Techniques of Feature Engineering for Machine Learning](https://towardsdatascience.com/feature-engineering-for-machine-learning-3a5e293a5114)
