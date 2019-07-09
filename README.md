# Chapter 4.4: Cleaning data

## Lesson 1: data cleaning

### Exercise 1: Data cleaning

You have imported the dataset. But before you go ahead and analyse, you first have to check the quality of the data. Otherwise you are at risk of making the wrong assumptions from your results and that can lead to negative consequences in your decision making. One of the most common data cleaning processes is to check for missing values, and estimate whether or not those have to replaced. 

Instructions:
Use is.null() to check if there is any missing data across the dataset.
Use fillna() to fill the missing data with the correct value.
Use mean() to calculate the mean of an object.
Use groupby() to group two or more columns together based on their relationship. For example, if you have a column Age and a column Year of Graduation, you might want to group these two to see how many students have graduated in the same year.

Let’s practice: 
If the dataset is called df, type the code that will show you how many missing values are there:
```python
data.isnull()
```
If we found that column C  has missing values, we can fill those with the mean of that column.
```python
data[C].fillna(data[C].mean(), inplace = True)
```

Substitutions however, should not be taken lightly. If we fill in the missing values with the mean of that column without checking if the mean is representative, we run the risk of skewing our data. Let’s see if the mean of column C is different when we group it with column Y. 
```python
data.groupby(Y)[C])
```

In this case we see that if we choose to replace all the missing values in column C with the mean of the column, the average will be skewed. Let’s instead replace the missing values by the mean of it’s groups.
```python
data[C].fillna(df.groupby(Y)[C].transform(“mean”), inplace = True)
```



