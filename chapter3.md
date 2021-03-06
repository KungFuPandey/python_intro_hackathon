---
title       : Exploratory analysis in Python using Pandas
description : We start with the first step of data analysis - the exploratory data analysis.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:python xp:100 skills:1 key:af2f6f90f3
## Who is eligible for loan?

Dream Housing Finance company deals in all home loans. They have presence across all urban, semi urban and rural areas. Customer first apply for home loan after that company validates the customer eligibility for loan. Company wants to automate the loan eligibility process (real time) based on customer detail provided while filling online application form.  

Let's start with loading in the training and testing set into your python environment. You will use the training set to build your model, and the test set to validate it. The data is stored on the web as CSV files; their URLs are already available as character strings in the sample code. You can load this data with the pandas.read_csv() function, it converts the data set to python dataframe. Python dataframe likes a spreadsheet or SQL table.


*** =instructions
- After importing the library "Pandas" (import pandas as pd), you read the dataset using function pd.read_csv()
- You can use train_url to load training dataset in train (dataframe)
- You can use test_url to load training dataset in test (dataframe)
- train.head(n) helps to look at top n observation
- train.tail(n) helps to look at bottom n observation


*** =hint
- Use len(dataframe) to return the total observations in the dataframe 
- Use len(dataframe.columns) to return the total available columns in the dataframe


*** =pre_exercise_code

```{python}

# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# Import library pandas
import pandas as pd

# Import training file
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing file
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

```

*** =sample_code

```{python}

# import library pandas
import pandas as pd

# Import training data as train
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing data as test
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

# Print top 5 observation of training dataset


# Store total number of observation in training dataset
train_length =

# Store total number of columns in testing data set
test_col = 

```

*** =solution

```{python}

import pandas as pd

# Import training data as train
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing data as test
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

# Print top 5 observation of test dataset
print (train.head(5))

# Store total number of observation in training dataset
train_length = len(train)

# Store total number of columns in testing data set
test_col = len(test.columns)

```

*** =sct

```{python}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# pythonwhat Python package. Documentation can also be found at github.com/datacamp/pythonwhat/wiki

# Test for evaluating top 5 heading of dataframe


# Test for total observation in training dataset
test_object("train_length")

# Test for total columns in testing dataset
test_object("test_col")

success_msg("Great work!")
```

--- type:NormalExercise lang:python xp:100 skills:1 key:36c3190b26
## Understanding Data?

You can look at summary of numerical fields by using describe() function. Describe() function would provide count, mean, standard deviation (std), min, quartiles and max in its output.

```{python}

describe(dataframe)

```
For the non-numeric values (e.g. Property_Area, Credit_History etc.), we can look at frequency distribution to understand whether they make sense or not. The frequency table can be printed by following command:

```{python}

df[column_name].value_counts()

```

*** =instructions

- Pass dataframe to describe() function 
- We can also look at unique values of non-numeric values using df[column_name].value_counts()


*** =hint
- Store the output of describe(train) in a dataframe df 
- Use df['ApplicantIncome'][2] to access standard deviation of Applicant Income
- Use df['PropertyArea']['Semiurban'] to access number of residents in semiurban area


*** =pre_exercise_code

```{python}

# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# Import library pandas
import pandas as pd

# Import training file
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing file
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

```

*** =sample_code

```{python}

# import library pandas
import pandas as pd

# Import training data as train
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing data as test
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

# Look at the summary of numerical variables for train data set
df= train.describe()
print (df)

# Store and print the standard deviation of ApplicantIncome in variable std_income
std_income = 
print("Standard Deviation of Applicant Income is %d" %std_income)

# Print the unique values and their frequency of variable Property_Area
df1=train['Property_Area'].value_counts()
print (df1)

# Store the number of residents of semi urban area in semiurban_count
semiurban_count=
print("%d residents are from semi urban area" %semiurban_count)


```

*** =solution

```{python}

import pandas as pd

# Import training data as train
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing data as test
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

# Look at the summary of numerical variables for train data set
df = train.describe()
print (df)

# Store and print the standard deviation of ApplicantIncome in variable std_income
std_income = df['ApplicantIncome'][2]
print("Standard Deviation of Applicant Income is %d" %std_income)

# Print the unique values and their frequency of variable Property_Area
df1=train['Property_Area'].value_counts()
print (df1)

# Store the number of residents of semi urban area in semiurban_count
semiurban_count = df1['Semiurban']
print("%d residents are from semi urban area" %semiurban_count)

```

*** =sct

```{python}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# pythonwhat Python package. Documentation can also be found at github.com/datacamp/pythonwhat/wiki

# Test for evaluating top 5 heading of dataframe


# Test for total observation in training dataset
test_object("std_income")

# Test for total columns in testing dataset
test_object("semiurban_count")

success_msg("Great work!")
```


--- type:NormalExercise lang:python xp:100 skills:1 key:85c5d3a079
## Understanding distribution of nmerical variables?

Now that we are familiar with basic data characteristics, let us study distribution of various variables. Let us start with numeric variables – namely ApplicantIncome.

Lets start by plotting the histogram of ApplicantIncome using the following commands:

```{python}

train['ApplicantIncome'].hist(bins=50)

```
Next, we can also look at box plots to understand the distributions. Box plot for ApplicantIncome can be plotted by


```{python}

train.boxplot(column='ApplicantIncome')

```

*** =instructions

- Import %matplotlib inline to have the charts in ipython notebook
- You can also create box plot for ApplicantIncome by categorical variable using following command

```{python}

train.boxplot(column='ApplicantIncome', by='Gender')

```



*** =hint
- Store the output of describe(train) in a dataframe df 
- Use df['ApplicantIncome'][2] to access standard deviation of Applicant Income
- Use df['PropertyArea']['Semiurban'] to access number of residents in semiurban area


*** =pre_exercise_code

```{python}

# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# Import library pandas
import pandas as pd

# Import training file
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing file
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

```

*** =sample_code

```{python}

# import library pandas
import pandas as pd

# Import training data as train
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing data as test
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

# Look at the summary of numerical variables for train data set
df= train.describe()
print (df)

# Store and print the standard deviation of ApplicantIncome in variable std_income
std_income = 
print("Standard Deviation of Applicant Income is %d" %std_income)

# Print the unique values and their frequency of variable Property_Area
df1=train['Property_Area'].value_counts()
print (df1)

# Store the number of residents of semi urban area in semiurban_count
semiurban_count=
print("%d residents are from semi urban area" %semiurban_count)


```

*** =solution

```{python}

import pandas as pd

# Import training data as train
train = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/train.csv")

# Import testing data as test
test = pd.read_csv("https://s3-ap-southeast-1.amazonaws.com/av-datahack-datacamp/test.csv")

# Look at the summary of numerical variables for train data set
df = train.describe()
print (df)

# Store and print the standard deviation of ApplicantIncome in variable std_income
std_income = df['ApplicantIncome'][2]
print("Standard Deviation of Applicant Income is %d" %std_income)

# Print the unique values and their frequency of variable Property_Area
df1=train['Property_Area'].value_counts()
print (df1)

# Store the number of residents of semi urban area in semiurban_count
semiurban_count = df1['Semiurban']
print("%d residents are from semi urban area" %semiurban_count)

```

*** =sct

```{python}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# pythonwhat Python package. Documentation can also be found at github.com/datacamp/pythonwhat/wiki

# Test for evaluating top 5 heading of dataframe


# Test for total observation in training dataset
test_object("std_income")

# Test for total columns in testing dataset
test_object("semiurban_count")

success_msg("Great work!")
```


