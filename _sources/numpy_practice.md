# Numpy

In this section we will learn how to use Numpy, a library for Python that allows us to work with multidimensional arrays and matrices. Numpy is the basis of other libraries such as Scikit-Learn, Pandas, Matplotlib, etc. In this section we will learn how to create arrays, how to access their elements, how to perform operations with them, etc.

## Creating arrays

You may be familiar with the concept of arrays from other programming languages. An array is a data structure that stores a collection of elements of the same type. In Python, arrays are called lists. However, in this course we will use the term array to refer to the data structure that Numpy provides. Numpy arrays are more efficient than lists, since they are stored in a contiguous block of memory. This allows us to perform operations on the entire array without the need for loops. 

To create an array, we can use the function `np.array()`. This function takes as input a list and returns an array. For example, to create an array with the numbers from 0 to 9, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array con los números del 0 al 9
a = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
print(a)
```

```
[0 1 2 3 4 5 6 7 8 9]
```

We can also create an array from a list of lists. For instance, let's create a 2-dimensional array with the numbers from 0 to 9:

$$
A = \begin{bmatrix}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{bmatrix}
$$


```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a)
```

```
[[0 1 2]
 [3 4 5]
 [6 7 8]]
```

We can also create an array with random numbers. For this, we can use the function `np.random.rand()`. This function takes as input the dimensions of the array and returns an array with random numbers between 0 and 1. For example, to create an array with 3 rows and 4 columns, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 3 x 4 con números aleatorios
a = np.random.rand(3, 4)
print(a)
```

```
[[0.37454012 0.95071431 0.73199394 0.59865848]
 [0.15601864 0.15599452 0.05808361 0.86617615]
 [0.60111501 0.70807258 0.02058449 0.96990985]]
```
By now you may be wondering how to know the dimensions of an array. To do this, we can use the attribute `shape`. For example, to know the dimensions of the array `a` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 3 x 4 con números aleatorios
a = np.random.rand(3, 4)
print(a.shape)
```

```
(3, 4)
```
During your career you will work with arrays of different dimensions. For example, in machine learning we usually work with 2-dimensional arrays, where each row represents a sample and each column represents a feature. In deep learning, we usually work with 4-dimensional arrays, where the first dimension represents the number of samples, the second dimension represents the number of channels, the third dimension represents the height of the image and the fourth dimension represents the width of the image. For instance we can create an image with 3 channels (RGB) of size 32 x 32 as follows:

```{code-block} python
---
linenos: true
---
import numpy as np

np.random.seed(42) # Fijar semilla para reproducibilidad

# Crear un array de 4 dimensiones
a = np.random.rand(1, 3, 32, 32)
print(a.shape)
# Pasamos a ver como queda la imagen usando matplotlib
import matplotlib.pyplot as plt
plt.imshow(a[0, 0, :, :], cmap='viridis')
plt.colorbar()
plt.savefig('./images/practices/imagen_ejemplo.png') # Guardar gráfico
plt.show()
```

```
(1, 3, 32, 32)
```

```{figure} ./images/practices/imagen_ejemplo.png
---
name: resulting_image
width: 700px
align: center
height: 500px
---
Resulting image
```

## Accessing elements

To access the elements of an array, we can use the same syntax as for lists. For example, to access the first element of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[0, 0])
```

```
0
```
If we use negative indices, we can access the elements of the array from the end. For example, to access the last element of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[-1, -1])
```

```
8
```

## Slicing

Let's step further and learn how to access a subset of an array. For this, we can use the slicing notation. For example, to access the first row of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[0, :])
```

```
[0 1 2]
```
To access the first column of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[:, 0])
```

```
[0 3 6]
```
To access the first two rows of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[:2, :])
```

```
[[0 1 2]
 [3 4 5]]
```
To access the first two columns of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[:, :2])
```

```
[[0 1]
 [3 4]
 [6 7]]
```
To access the first two rows and the first two columns of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[:2, :2])
```

```
[[0 1]
 [3 4]]
```
Last example, to access the diagonal of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true   
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(a[range(3), range(3)])
```

```
[0 4 8]
```
What range(3) does is to create a list with the numbers from 0 to 2. This is equivalent to the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(a[[0, 1, 2], [0, 1, 2]])
```

```
[0 4 8]
```
### Sorting
In numpy we can also sort the elements of an array. For example, to sort the elements of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array de 2 dimensiones
a = np.array([[3, 2, 1], [6, 5, 4], [9, 8, 7]])
print(np.sort(a))
```

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```
We can also sort the elements of an array in descending order. For example, to sort the elements of the array `A` that we created in the previous example in descending order, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array de 2 dimensiones
a = np.array([[3, 2, 1], [6, 5, 4], [9, 8, 7]])
print(-np.sort(-a))
```

```
[[9 8 7]
 [6 5 4]
 [3 2 1]]
```
```{note}
If we want to get the arguments that would sort an array, we can use the function `np.argsort()`. For example, to get the arguments that would sort the elements of the array `A` that we created in the previous example.
```

## Operations
In this section we will learn how to perform operations on arrays, whether they are operations on the same or together with other arrays.

### Operations on the same array
Let's start with the simplest case, operations on the same array. For example, to add 1 to each element of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A + 1)
```

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
```
We can also perform other operations such as subtraction, multiplication, division, etc. For example, to subtract 1 to each element of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A - 1)
```

```
[[-1  0  1]
 [ 2  3  4]
 [ 5  6  7]]
```
To multiply each element of the array `A` that we created in the previous example by 2, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A * 2)
```

```
[[ 0  2  4]
 [ 6  8 10]
 [12 14 16]]
```
We can also perform power operations. For example, to raise each element of the array `A` that we created in the previous example to the power of 2, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A ** 2)
```

```
[[ 0  1  4]
 [ 9 16 25]
 [36 49 64]]
```
We can also perform operations on the entire array. For example, to calculate the sum of all the elements of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A.sum())
```

```
36
```
To calculate the mean of all the elements of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A.mean())
```

```
4.0
```
Notice that we can also calculate the sum and the mean of each row or column. For example, to calculate the sum of each row of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A.sum(axis=1))
```

```
[ 3 12 21]
```
To calculate the mean of each column of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A.mean(axis=0))
```

```
[3. 4. 5.]
```
### Operations on different arrays

Now let's learn how to perform operations on different arrays.

$$
A = \begin{bmatrix}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{bmatrix}
B = \begin{bmatrix}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{bmatrix}
$$

Numpy allows us to perform operations on arrays. For example, to add two arrays, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear dos arrays de 2 dimensiones

a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
b = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(a + b)
```

```
[[ 0  2  4]
 [ 6  8 10]
 [12 14 16]]
```
```{note}
To add/subtract two arrays, they must have the same dimensions.
To perform a matrix multiplication, the number of columns of the first matrix must be equal to the number of rows of the second matrix.
For example, if we have a matrix $A$ of size $m \times n$ and a matrix $B$ of size $n \times p$, we can multiply them to obtain a matrix $C$ of size $m \times p$.
```
To multiply two arrays, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear dos arrays de 2 dimensiones

a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
b = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(a @ b)
```

```
[[ 15  18  21]
 [ 42  54  66]
 [ 69  90 111]]
```
```{note}
The `@` symbol is used to perform matrix multiplication. If you want to perform element-wise multiplication, you can use the `*` symbol.
```
### Broadcasting

Broadcasting is a powerful mechanism that allows Numpy to work with arrays of different shapes when performing arithmetic operations. Frequently we have a smaller array and a larger array, and we want to use the smaller array multiple times to perform some operation on the larger array. For example, suppose we want to add a constant vector to each row of a matrix. We could do it like this:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones
a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

# Crear un vector de 1 dimensión
b = np.array([1, 2, 3])

print(a + b)
```

```
[[ 1  3  5]
 [ 4  6  8]
 [ 7  9 11]]
```
This works; however, what if we had a larger array? Adding the vector `b` to each row of the matrix `a` would be very inefficient, since we would have to create a large matrix where each row is the vector `b`, and then add it to the matrix `a`. Numpy broadcasting allows us to perform this computation without actually creating multiple copies of `b`.

```{note}
Broadcasting two arrays together follows these rules:
- If the arrays do not have the same rank, prepend the shape of the lower rank array with 1s until both shapes have the same length.
- The two arrays are said to be compatible in a dimension if they have the same size in the dimension, or if one of the arrays has size 1 in that dimension.
- The arrays can be broadcast together if they are compatible in all dimensions.
- After broadcasting, each array behaves as if it had shape equal to the elementwise maximum of shapes of the two input arrays.
- In any dimension where one array had size 1 and the other array had size greater than 1, the first array behaves as if it were copied along that dimension.
```
Another approach is to reshape the vector `b` to be a row vector of shape `(1, 3)`. We can then broadcast it directly against `a`:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array de 2 dimensiones

a = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

# Crear un vector de 1 dimensión
b = np.array([1, 2, 3])

print(a + b.reshape((1, 3)))
```

```
[[ 1  3  5]
 [ 4  6  8]
 [ 7  9 11]]
```
### Comparison operators

Numpy also allows us to perform comparison operations on arrays. For example, to compare each element of the array `A` that we created in the previous example with the number 5, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A > 5)
```

```
[[False False False]
 [False False False]
 [ True  True  True]]
```

This is very useful when we want to filter the elements of an array. In machine learning, we usually have a dataset with a set of features and a set of labels. For example, let's suppose we have a dataset with the following features:

$$
X = \begin{bmatrix}
0 & 1 & 2 \\
3 & 4 & 5 \\
6 & 7 & 8
\end{bmatrix}
$$

And the following labels:

$$
y = \begin{bmatrix}
0 \\
1 \\
2
\end{bmatrix}
$$

If we want to filter the elements of the array `X` that we created in the previous example that have a label greater than 1, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
X = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

# Crear un vector de 1 dimensión
y = np.array([0, 1, 2])

print(X[y > 1])
```

```
[[6 7 8]]
```
### Logical operators

Numpy also allows us to perform logical operations on arrays. For example, to perform a logical `and` operation on the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print((A > 1) & (A < 5))
```

```
[[False False  True]
 [ True  True False]
 [False False False]]
```
To perform a logical `or` operation on the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print((A > 1) | (A < 5))
```

```
[[ True  True  True]
 [ True  True  True]
 [False False False]]
```
To perform a logical `not` operation on the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(~(A > 1))
```

```
[[ True  True False]
 [False False False]
 [False False False]]
```
### Localizing elements

Numpy also allows us to localize the elements of an array that meet a certain condition. For example, to localize the elements of the array `A` that we created in the previous example that are greater than 5, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(np.where(A > 5))
```

```
(array([2, 2, 2]), array([0, 1, 2]))
```
The `where()` function returns a tuple of arrays, one for each dimension of the input array, containing the indices where the given condition is true. In this case, the first array contains the indices of the rows and the second array contains the indices of the columns. This is very useful when we want to filter the elements of an array.

Another way to localize the elements of an array that meet a certain condition is to use the `nonzero()` function. For example, to localize the elements of the array `A` that we created in the previous example that are greater than 5, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(A.nonzero())
```

```
(array([0, 0, 1, 1, 1, 2, 2, 2]), array([1, 2, 0, 1, 2, 0, 1, 2]))
```
The `nonzero()` function returns a tuple of arrays, one for each dimension of the input array, containing the indices where the given condition is true. In this case, the first array contains the indices of the rows and the second array contains the indices of the columns. This is very useful when we want to filter the elements of an array.

We can also combine the `where()` and `nonzero()` functions to localize the elements of an array that meet a certain condition. For example, to localize the elements of the array `A` that we created in the previous example that are greater than 5, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(np.nonzero(np.where(A > 5)))
```

```
(array([0, 0, 0, 1, 1]), array([0, 1, 2, 1, 2]))
```
Also we can sum the elements of an array that meet a certain condition. For example, to sum the elements of the array `A` that we created in the previous example that are greater than 5, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(np.sum(A[np.where(A > 5)]))
```

```
21
```
Indeed, we can also sum the elements of an array that meet a certain condition using the `nonzero()` function. For example, to sum the elements of the array `A` that we created in the previous example that are greater than 5, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])
print(np.sum(A[np.nonzero(np.where(A > 5))]))
```

```
21
```
### Triu and tril

Numpy also allows us to obtain the upper triangular part of a matrix. For example, to obtain the upper triangular part of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array de 2 dimensiones
a = np.array([[3, 2, 1], [6, 5, 4], [9, 8, 7]])
print(np.triu(a))
```

```
[[3 2 1]
 [0 5 4]
 [0 0 7]]
```
Numpy also allows us to obtain the lower triangular part of a matrix. For example, to obtain the lower triangular part of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array de 2 dimensiones
a = np.array([[3, 2, 1], [6, 5, 4], [9, 8, 7]])
print(np.tril(a))
```

```
[[3 0 0]
 [6 5 0]
 [9 8 7]]
```

### Shape manipulation

Numpy also allows us to perform operations to change the shape of an array. For example, to flatten the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---

import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A.flatten())
```

```
[0 1 2 3 4 5 6 7 8]
```

To transpose the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---

import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5], [6, 7, 8]])

print(A.T)
```

```
[[0 3 6]
 [1 4 7]
 [2 5 8]]
```

The `reshape()` function allows us to change the shape of an array. This function will be very useful in your future career, since you will have to change the shape of the data to feed it to the machine learning algorithms.

```{code-block} python
---
linenos: true
---

import numpy as np

# Crear un array
A = np.array([[0, 1, 2], [3, 4, 5]])

print(A.reshape((3, 2)))
```

```
[[0 1]
 [2 3]
 [4 5]]
```

### Eigenvalues and eigenvectors

In numpy we can also calculate the eigenvalues and eigenvectors of a matrix. For example, to calculate the eigenvalues and eigenvectors of the array `A` that we created in the previous example, we can do the following:

```{code-block} python
---
linenos: true
---
import numpy as np
# Crear un array de 2 dimensiones
a = np.array([[3, 2, 1], [6, 5, 4], [9, 8, 7]])
eigenvalues, eigenvectors = np.linalg.eig(a)
print(eigenvalues)
print(eigenvectors)
```

```
[ 1.61168440e+01 -1.11684397e+00 -1.30367773e-15]
[[-0.23197069 -0.78583024  0.40824829]
 [-0.52532209 -0.08675134 -0.81649658]
 [-0.81867349  0.61232756  0.40824829]]
```

## Exercises
```{warning}
There is code with errors in the previous examples. You have to correct the code and run it to check if the output is correct. **Part of the mark will be based on the correct execution of the code.And please, report the places that you visited to solve the bug.**
```
```{note}
You have to submit your answers via UAcloud using the corresponding assignment. The file must be a surname_name.zip file containing three .ipynb file with your answers. The name of the file must be `numpy_exercises_1.ipynb`, `numpy_exercises_2.ipynb` and `numpy_exercises_3.ipynb`. Finally, in each notebook you have to include your name and surname.
```
### Exercise 1
After reading the previous section, you should be able to create your first Jupyter-Notebook and write a report about all the things you have learned in this section. In order to have a good structure, we recommend you to follow exactly the same structure as in this notebook. 
### Exercise 2: NumPy Array Calculator Implementation

Design a calculator system for handling NumPy array operations by implementing a set of functions. The calculator should support operations between bidimensional arrays, including:
- Addition
- Subtraction
- Multiplication (Matrix multiplication)
- Concatenation
- Transpose

Your task is to implement the following functions:

1. A main calculator function that receives two NumPy arrays and an operation string as parameters
2. Helper functions for each specific operation

#### Requirements:

1. The main calculator function should have the following signature:
```{code-block} python
def array_calculator(array1: np.ndarray, array2: np.ndarray, operation: str) -> np.ndarray:
    """
    Performs the specified operation between two NumPy arrays.
    
    Parameters:
    array1 (np.ndarray): First input array
    array2 (np.ndarray): Second input array
    operation (str): Operation to perform ('+', '-', '*', 'concat', 'transpose')
    
    Returns:
    np.ndarray: Result of the operation
    """
```
2. The function should handle the following cases:
    - Valid operations between compatible arrays
    - Error handling for incompatible array dimensions
    - Error handling for unsupported operations
    - Never use input(), since it was used last year
    Example:
    ```{code-block} python
    # Example arrays
    a = np.array([[0, 1, 2], 
                [3, 4, 5], 
                [6, 7, 8]])

    b = np.array([[0, 1, 2], 
                [3, 4, 5], 
                [6, 7, 8]])

    # Addition example
    result = array_calculator(a, b, '+')
    # Expected output:
    # array([[ 0,  2,  4],
    #        [ 6,  8, 10],
    #        [12, 14, 16]])

    # Invalid operation example
    result = array_calculator(a, b, '&')
    # Should raise ValueError with message: "Operation '&' not supported"
    ```
#### Hints:
1. Use NumPy's built-in functions for array operations
2. Implement error checking for:
    - Array dimension compatibility
    - Valid operation types
    - Array shape requirements for specific operations


### Exercise 3
You have to solve the following problems using numpy:


a) Create a 10x10 matrix with **your own seed**. Make sure that the values are 0 or 1. Also make sure that the diagonal is 0, so you don't have loops in your graph.


b) Calculate the degree matrix of the graph.
**Formula:** $D_{ii} = \sum_{j=1}^{n} A_{ij}$


c) Calculate the Laplacian matrix of the graph.
**Formula:** $L = D - A$


d) Calculate the normalized Laplacian matrix of the graph.


**Formula:** $L_{norm} = D^{-1/2} L D^{-1/2}$
``` {note}
Make sure that the values are **correct** and do not contain any infinity or NaN values due to the square root of a negative number.
```
e) Create a function that given an adjacency matrix and value, returns the number of nodes that have same or more degree than the value. The function must receive as input the adjacency matrix and the value. The function must return a numpy array with the number of nodes that have same or more degree than the value.
```{python}
def nodes_degree(adjacency_matrix, value):
    # Your code here
    return number_of_nodes
print(nodes_degree(adjacency_matrix, value))
# If the are nodes that have same or more degree than the value, the function must return a numpy array with the nodes that have same or more degree than the value
# else the function must return a numpy array with the value -1
``` 