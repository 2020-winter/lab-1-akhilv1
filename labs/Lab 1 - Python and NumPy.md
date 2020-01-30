---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**PUT YOUR FULL NAME(S) HERE**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.


## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1
Make an array a of size 6 × 4 where every element is a 2.

```python
import numpy as np
a = np.ones((6,4))*2
print(a)
```

## Exercise 2
Make an array b of size 6 × 4 that has 3 on the leading diagonal and 1
everywhere else. (You can do this without loops.)

```python
b = np.ones((6,4))
b[range(4), range(4)] = 3
print(b)
```

## Exercise 3
Can you multiply these two matrices together? Why does a * b work, but
not dot(a,b)?

```python
print(a * b)
np.dot(a, b)
#dot function uses dot multiplication of matricies, so the dimentions of the two matricies must be inverse of each other
```

## Exercise 4
Compute dot(a.transpose(),b) and dot(a,b.transpose()). Why are
the results different shapes?

```python
print("np.dot(a.transpose(),b)\n", np.dot(a.transpose(),b), "\n")
print("np.dot(a,b.transpose())\n", np.dot(a,b.transpose()))
#they're different dimensons because of dot multiplication again. 
#in dot(a.transpose(),b), a.transpose is 4x6 and multiplied with b which is 6x4 which results in a 4x4 output
#in dot(a,b.transpose()), b.transpose is 6x4 and multiplied with a which is 4x6 which results in a 6x6 output
```

## Exercise 5
Write a function that prints some output on the screen and make sure you can run it in the programming environment that you are using.

```python
def printSomething():
    print("something")
    
printSomething();
```

## Exercise 6
Now write one that makes some random arrays and prints out their sums, the mean value, etc.

```python
def makeRandArr():
    arr = np.random.rand(6, 4)
    print(arr)
    print("arr.sum()",arr.sum())
    print("arr.mean()",arr.mean())
    
makeRandArr()
```

## Exercise 7
Write a function that consists of a set of loops that run through an array and count the number of ones in it. Do the same thing using the where() function (use info(where) to find out how to use it).

```python
def countOnes(arr):
    c = 0;
    for i in range(arr.shape[0]):
        for j in range(arr.shape[1]):
            if arr[i][j] == 1:
                c += 1
    return c,len(np.where(arr==1)[0])
countOnes(a), countOnes(b)
```

## Excercises 8-11
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
import numpy as np
a = pd.DataFrame(np.ones((6,4))*2)
print(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = np.ones((6,4))
b = pd.DataFrame(b)
b.iloc[range(4),range(4)] = 3
print(b)
```

```python
b.values
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
print(a*b)
# np.dot(a, b)
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def countOnes(arr):
    c = 0
    for i in range(arr.shape[0]):
        for j in range(arr.shape[1]):
            if arr.iloc[i, j] == 1:
                c += 1
    
    return c, len(np.where(arr == 1)[0])
countOnes(a), countOnes(b)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

```python
titanic_df.index
```

```python
df = titanic_df.set_index('sex').loc['female']
df
```

```python
inxs = np.where(titanic_df.survived==1)
inxs
titanic_df.iloc[inxs]
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df["name"]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace=True)
titanic_df
```

```python
## YOUR SOLUTION HERE
```

```python

```
