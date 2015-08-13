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
