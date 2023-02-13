# EDA_Bank_Case_Study
In this case study ,the company wants to understand the driving factors (or driver variables) behind loan default, i.e. the variables which are strong indicators of default.

Business Understanding : 
The loan providing companies find it hard to give loans to the people due to their insufficient or non-existent credit history. Because of that, some consumers use it as their advantage by becoming a defaulter. Suppose you work for a consumer finance company which specialises in lending various types of loans to urban customers. You have to use EDA to analyse the patterns present in the data. This will ensure that the applicants capable of repaying the loan are not rejected.
When the company receives a loan application, the company has to decide for loan approval based on the applicant’s profile.

Business Objectives :
The company wants to understand the driving factors (or driver variables) behind loan default, i.e. the variables which are strong indicators of default. The company can utilise this knowledge for its portfolio and risk assessment.

Download the dataset from the link given as below. 
https://drive.google.com/open?id=16RQztUqCfJOlbooHqYlJrp6Q7iL65uZB

_________






_-------------------------------6

import pandas as pd
from openpyxl import load_workbook

# list of dataframes
df_list = [df1, df2, df3]

# list of sheet names
sheet_names = ['Sheet1', 'Sheet2', 'Sheet3']

# check if the file exists in DBFS
dbutils.fs.ls("/dbfs/path/to/existing_file.xlsx")

# if the file exists, load it
if len(dbutils.fs.ls("/dbfs/path/to/existing_file.xlsx")) > 0:
    with open("/dbfs/path/to/existing_file.xlsx", "rb") as f:
        content = f.read()
        book = load_workbook(content)

# if the file doesn't exist, create a new one
else:
    book = Workbook()

# create the writer object
writer = pd.ExcelWriter('/dbfs/path/to/existing_file.xlsx', engine='openpyxl')
writer.book = book

# write each dataframe to a different sheet
for i, df in enumerate(df_list):
    df.to_excel(writer, sheet_name=sheet_names[i], index=False)

# save the changes
writer.save()




----------------6666666

Sure. Here is some sample code in Python that can be used to apply Association Rule Mining in order to identify relationships between independent continuous variables and dependent continuous variables:

```Python
#import the necessary packages
import numpy as np
import pandas as pd
from mlxtend.frequent_patterns import apriori

#load the data
data = pd.read_csv('data.csv')

#convert the data into a form suitable for the apriori algorithm
transaction_data = []
for i in range(0, data.shape[0]):
    temp = []
    for j in range(0, data.shape[1]):
        temp.append(str(data.values[i,j]))
    transaction_data.append(temp)

#apply the apriori algorithm to the data
rules = apriori(transaction_data, min_support = 0.3, min_confidence = 0.8, min_lift = 3, min_length = 2)

#output the rules
print(rules)

```
