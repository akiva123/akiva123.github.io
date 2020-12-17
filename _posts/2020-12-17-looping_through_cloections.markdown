---
layout: post
title:      "Looping Through Colections"
date:       2020-12-17 13:17:53 -0500
permalink:  looping_through_cloections
---


If you have unusable values in a data-frame, use a for loop to iterate through the columns and a nested for loop to iterate the the column rows, and then conditionally check the rows for the unusable values to determine which columns have the unusable values.

list1=[]
for column in data.columns:
    for i in data[(f'{column}')]:
        if i == '?':
            list1.append(column)

            mode = data[(f'{column}')].mode()


print(f'Columns:{set(list1)}')
print(f'Value:{mode}')

Then iterate conditionally through the column with the unusable values and replace them.

for i in X[('sqft_basement')]:
    if i != '?':
        #print(i)
        sqft_basement1.append(i)
    elif i == '?':
            #print(i)
            i=i.replace('?', '0')
            #print(i)
            sqft_basement1.append(i)
sqft_basement1=pd.DataFrame(sqft_basement1)
sqft_basement1

Test outliers for statistical significance by using a for loop to iterate through the continuous independent variable columns and  a nested for loop to iterate conditionally through the column rows and separate the data according to quantiles. Mask the data-frame to  account for NaN values.

for i in ContinuousX[column]:
        if i < X2[f'{column}'].quantile(.25):
            list1.append(i)
            
    
        elif i > X2[f'{column}'].quantile(.75):
            list2.append(i)
            
        
        else:
            list3.append(i)

            
            
    X2[f'{column}_lower_outliers']=pd.DataFrame(list1)
    X2[f'{column}_upper_outliers']=pd.DataFrame(list2)
    X2[f'{column}1']=pd.DataFrame(list3)
    X2=X2.drop([f'{column}'],axis=1)
X2=X2.mask(X2=='NaN').fillna(X2.mean())
X2

In regression, finding interactions that are statistically significant will enhance the model. To get every interaction, use a nested for loop. The first loop iterates through every independent variable and the nested loop iterates the first loop independent variable with every independent variable to make a sample for every combination of the interactions that the first loop independent variable has.

for column in Independent_Variables:
    for columns in Independent_Variables:
        model_interaction = smf.ols(formula=f'price ~ {column} +    {columns} + {column}:{columns}', data=data).fit()
        summary = model_interaction.summary()
        print(summary)
