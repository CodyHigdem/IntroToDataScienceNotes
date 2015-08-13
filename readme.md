#Introduction to Data Science Notes

##Lesson 1

To get brushed up on python https://www.udacity.com/course/programming-foundations-with-python--ud036

####Python Pandas
Handle data in a way suited for analysis
Similiar to R So nice pick up

Data frames: string, int, float, bolean. Similiar to excel spreadsheets

Create a data frame. create a python dictionary called d where each key is the name of the column. Then the name of the data frames and the index of where you want them to go.
In fare, there was a NaN and so it is 'skipped' in the data frame and indexes are given to everything else

d = {'name': Series(['Braund', 'Cummings', 'Heikkinen', 'Allen'], index=['a', 'b', 'c', 'd']),
	'age': Series([22,38,26,35], index=['a','b','c','d']),
	'fare': Series([7.25,71.83,.8.05], index=['a','b','d'])
	'survived': Series([False, True, True, False], index=['a', 'b', 'c', 'd'])}

Now that this is created, we can actually pass this on to the data frame function to create the actual dataframe.

df = DataFrame(d)

print (df)

returns a 'excel' like info

import pandas as pd

'''
The following code is to help you play with the concept of Series in Pandas.

You can think of Series as an one-dimensional object that is similar to
an array, list, or column in a database. By default, it will assign an
index label to each item in the Series ranging from 0 to N, where N is
the number of items in the Series minus one.

Please feel free to play around with the concept of Series and see what it does

*This playground is inspired by Greg Reda's post on Intro to Pandas Data Structures:
http://www.gregreda.com/2013/10/26/intro-to-pandas-data-structures/
'''
# Change False to True to create a Series object
if False:
    series = pd.Series(['Dave', 'Cheng-Han', 'Udacity', 42, -1789710578])
    print series

'''
You can also manually assign indices to the items in the Series when
creating the series
'''

# Change False to True to see custom index in action
if False:
    series = pd.Series(['Dave', 'Cheng-Han', 359, 9001],
                       index=['Instructor', 'Curriculum Manager',
                              'Course Number', 'Power Level'])
    print series

'''
You can use index to select specific items from the Series
'''
# Change False to True to see Series indexing in action
if False:
    series = pd.Series(['Dave', 'Cheng-Han', 359, 9001],
                       index=['Instructor', 'Curriculum Manager',
                              'Course Number', 'Power Level'])
    print series['Instructor']
    print ""
    print series[['Instructor', 'Curriculum Manager', 'Course Number']]

'''
You can also use boolean operators to select specific items from the Series
'''
# Change False to True to see boolean indexing in action
if False:
    cuteness = pd.Series([1, 2, 3, 4, 5], index=['Cockroach', 'Fish', 'Mini Pig',
                                                 'Puppy', 'Kitten'])
    print cuteness > 3
    print ""
    print cuteness[cuteness > 3]


####Python Numpy
Multidimentional arrays + Matrices
Mathematical functions
Like Statistical analysis
numbers = [1,2,3,4,5]

Mean
numpy.mean(numbers)
return 3.0

Median
numpy.median(numbers)
return 3.0

Standard Deviation
numpy.std(numbers)
returns 1.4142...

#####Numpy Examples
import numpy as np

'''
The following code is to help you play with Numpy, which is a library
that provides functions that are especially useful when you have to
work with large arrays and matrices of numeric data, like doing
matrix matrix multiplications. Also, Numpy is battle tested and
optimized so that it runs fast, much faster than if you were working
with Python lists directly.
'''

'''
The array object class is the foundation of Numpy, and Numpy arrays are like
lists in Python, except that every thing inside an array must be of the
same type, like int or float.
'''
# Change False to True to see Numpy arrays in action
if False:
    array = np.array([1, 4, 5, 8], float)
    print array
    print ""
    array = np.array([[1, 2, 3], [4, 5, 6]], float)  # a 2D array/Matrix
    print array

'''
You can index, slice, and manipulate a Numpy array much like you would with a
a Python list.
'''
# Change False to True to see array indexing and slicing in action
if False:
    array = np.array([1, 4, 5, 8], float)
    print array
    print ""
    print array[1]
    print ""
    print array[:2]
    print ""
    array[1] = 5.0
    print array[1]

# Change False to True to see Matrix indexing and slicing in action
if False:
    two_D_array = np.array([[1, 2, 3], [4, 5, 6]], float)
    print two_D_array
    print ""
    print two_D_array[1][1]
    print ""
    print two_D_array[1, :]
    print ""
    print two_D_array[:, 2]

'''
Here are some arithmetic operations that you can do with Numpy arrays
'''
# Change False to True to see Array arithmetics in action
if False:
    array_1 = np.array([1, 2, 3], float)
    array_2 = np.array([5, 2, 6], float)
    print array_1 + array_2
    print ""
    print array_1 - array_2
    print ""
    print array_1 * array_2

# Change False to True to see Matrix arithmetics in action
if False:
    array_1 = np.array([[1, 2], [3, 4]], float)
    array_2 = np.array([[5, 6], [7, 8]], float)
    print array_1 + array_2
    print ""
    print array_1 - array_2
    print ""
    print array_1 * array_2

'''
In addition to the standard arthimetic operations, Numpy also has a range of
other mathematical operations that you can apply to Numpy arrays, such as
mean and dot product.

Both of these functions will be useful in later programming quizzes.
'''
if False:
    array_1 = np.array([1, 2, 3], float)
    array_2 = np.array([[6], [7], [8]], float)
    print np.mean(array_1)
    print np.mean(array_2)
    print ""
    print np.dot(array_1, array_2)


import numpy as np
import pandas as pd

'''
The following code is to help you play with the concept of Dataframe in Pandas.

You can think of a Dataframe as something with rows and columns. It is
similar to a spreadsheet, a database table, or R's data.frame object.

*This playground is inspired by Greg Reda's post on Intro to Pandas Data Structures:
http://www.gregreda.com/2013/10/26/intro-to-pandas-data-structures/
'''

'''
To create a dataframe, you can pass a dictionary of lists to the Dataframe
constructor:
1) The key of the dictionary will be the column name
2) The associating list will be the values within that column.
'''
# Change False to True to see Dataframes in action
if False:
    data = {'year': [2010, 2011, 2012, 2011, 2012, 2010, 2011, 2012],
            'team': ['Bears', 'Bears', 'Bears', 'Packers', 'Packers', 'Lions',
                     'Lions', 'Lions'],
            'wins': [11, 8, 10, 15, 11, 6, 10, 4],
            'losses': [5, 8, 6, 1, 5, 10, 6, 12]}
    football = pd.DataFrame(data)
    print football

'''
Pandas also has various functions that will help you understand some basic
information about your data frame. Some of these functions are:
1) dtypes: to get the datatype for each column
2) describe: useful for seeing basic statistics of the dataframe's numerical
   columns
3) head: displays the first five rows of the dataset
4) tail: displays the last five rows of the dataset
'''
# Change False to True to see these functions in action
if False:
    data = {'year': [2010, 2011, 2012, 2011, 2012, 2010, 2011, 2012],
            'team': ['Bears', 'Bears', 'Bears', 'Packers', 'Packers', 'Lions',
                     'Lions', 'Lions'],
            'wins': [11, 8, 10, 15, 11, 6, 10, 4],
            'losses': [5, 8, 6, 1, 5, 10, 6, 12]}
    football = pd.DataFrame(data)
    print football.dtypes
    print ""
    print football.describe()
    print ""
    print football.head()
    print ""
    print football.tail()
