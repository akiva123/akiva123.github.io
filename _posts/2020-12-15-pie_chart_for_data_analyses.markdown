---
layout: post
title:      "Pie Chart for data analyses"
date:       2020-12-15 19:53:10 +0000
permalink:  pie_chart_for_data_analyses
---


Pie charts are useful for comparing percentages of a whole.



We're going to make a function called genre_percent with a parameter called genres through which we pass the list of genres as our argument.

def genre_percent(genres):

Use the set function on the list of genres to make a category for each unique genre.

set=set(genres)

Import pandas and then iterate through the set by - making a list, identifying each time a genre appeared as true and the rest as false using a str.contains function, collecting all the true appearances using a filter function, finding the percentage of each genre, and appending the percentage to the list.

import pandas as pd
for i in set:
        list=[]
        true= genres.str.contains(f"{i}")
        t = list(filter(lambda l: true[l], range(len(true))))
        variable=(len(t)/len(df1))*100
        list.append(variable)

Import OrderedDict from collections, make a dictionary and store the set as the keys and the list as the values using a zip function, use the OrderderedDict function to sort the values numerically so that the slices of the chart will be ordered, and store the ordered dictionary keys in a variable and the values in another variable.

from collections import OrderedDict
zip = dict(zip(set, list))
ordered = OrderedDict(sorted(zip.items(), key=lambda x: x[1]))
keys=ordered.keys()
values=ordered.values()

Now, let's make the pie chart. Import matplotlib, make the labels equal to the keys and the sizes equal to the values, assign the pie chart plotting function to fig1 and ax1, construct the pie chart with the pie function and its parameters, ensure the pie is drawn as a circle with an axis('equal') function, reference the current figure with a gcf function, set the size of the figure with a set_size_inches function, and display the pie chart with a show function.

import matplotlib.pyplot as plt
%matplotlib inline
labels = keys
sizes = values
fig1, ax1 = plt.subplots()
ax1.pie(sizes, labels=labels, autopct='%1.1f%%',
      shadow=True, startangle=90)
ax1.axis('equal')  
fig = plt.gcf()
fig.set_size_inches(10,10)
plt.show()

When comparing percentages of a whole, because they add up to 100, a pie chart is a reasonable method of visualization. However, generally it is best to use a bar graph when comparing quantities because identifying angle size is cumbersome. Bar graphs are useful for comparing discrete data, whereas pie charts are a way to display how parts make up a whole.
