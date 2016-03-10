# Linear algebra

## Scientific Computing with Python

Various open-source add-on modules to Python make the programming language very suitable for scientific computing purposes. This will be illustrated by examples from linear algebra, statistics, and data plotting.

**NumPy** (Numeric Python) is an open-source add-on module to Python that provides common mathematical and numerical routines in pre-compiled, fast functions. It provides basic routines for manipulating large arrays and matrices of numeric data. For example, it contains the well-known LAPACK library for doing linear algebra.

*Note: we expect you to try all examples below in your own Python shell.*

Like any Python module, one must import NumPy before it can be used. This can be done in several ways, but a recommended way is to import it under a brief name, say `np`:

	>>> import numpy as np

## Arrays

Hereafter one can introduce the basic NumPy datatype `array` as follows:

	>>> a = np.array([1, 3, 5], float) # change a list into an array
	>>> type(a)
	<type 'numpy.ndarray'>
	>>> a
	array([ 1., 3., 5.])

An 1-dimensional array is similar to a list in Python, except that (i) every element of an array must be of the same type, typically a numeric type like float or int; and (ii) the length of a given array remains fixed during a computation.

These constraints on arrays offers the opportunity to make operations with large amounts of numeric data very fast: arrays are generally much more time-efficient than lists. The main reason is that most functions are automatically applied to every element of an array; in contrast with the use of lists, one does not need to implement a loop or use the map function. This usually leads to efficient, readable, 'vectorized' computations. For example, continuing with the above example:

	>>> b = np.arange(3)
	>>> b
	array([0, 1, 2])
	>>> a*b
	array([  0.,   3.,  10.])

Access to a 1-dimensional array is similar to access of lists:

	>>> a[1]
	3.0
	>>> a[1:]
	array([ 3.,  5.])

Element-wise vector-computation makes it easy to generate data graphs of functions via arrays. First introduce via the `linspace` function from the NumPy package an array of equally spaced points within a interval and then create function values (note that NumPy as supports various mathematical functions). In the example below the quadratic and logarithmic functions are considered:

	>>> x = np.linspace(1, 3, 10)
	>>> x
	array([ 1.        , 1.22222222, 1.44444444, 1.66666667, 1.88888889,
	        2.11111111, 2.33333333, 2.55555556, 2.77777778, 3.        ])
	>>> y = x**2 # quadratic function values
	>>> y
	array([ 1.        , 1.49382716, 2.08641975, 2.77777778, 3.56790123,
	        4.45679012, 5.44444444, 6.5308642 , 7.71694938, 9.        ])
	
	>>> z = np.log(x) # logarithmic function values
	>>> z
	array([ 0.        , 0.2006707 , 0.36772478, 0.51082562, 0.63598877,
                0.7472144 , 0.84729786, 0.93826964, 1.02165125,  1.09861229])

## Matrices

Multidimensional arrays are also well-supported by Python. The focus in this tutorial is on 2-dimensional arrays because they can be interpreted as matrices. Two examples of created 2-dimensional arrays are:

    >>> A = np.array([[1,2,3], [4,5,6]])
    >>> A
    array([[1, 2, 3],
           [4, 5, 6]])
    >>> B = np.diag([1,2,3])
    >>> B
    array([[1, 0, 0],
           [0, 2, 0],
           [0, 0, 3]])
    >>> A.shape
    (2, 3)
    >>> B.shape
    (3, 3)

The display of the 2-dimensional arrays suggest that they can be interpreted as matrices. Indeed with the dot function or method one can compute the matrix product of $$A$$ and $$B$$.

    >>> np.dot(A, B)
    array([[ 1,  4,  9],
           [ 4, 10, 18]])
    >>> A.dot(B)
    array([[ 1,  4,  9],
           [ 4, 10, 18]])

One cannot use `*` for matrix arithmetic as this will only multiply arrays element-wise:

    >>> A*A
    array([[ 1,  4,  9],
           [16, 25, 36]])

Of course, matrix-vector multiplication must be done with the dot function as well:

	>>> v = np.ones(3)
	>>> v
	array([ 1., 1., 1.])
	>>> np.dot(A, v)
	array([  6.,  15.])

A 1-dimensional array can be treated as either column or row vector. It is the responsibility of the Python programmer to ensure that dimensions match for array arithmetic:

	>>> np.dot(v, A)
	Traceback (most recent call last):
	  File "<pyshell#157>", line 1, in <module>
	    np.dot(v,A)
	ValueError: matrices are not aligned
	>>> np.dot(v[:2], A)
	    array([ 5.,  7.,  9.])
	>>> np.cumsum(v)  
	>>> w
	array([ 1.,  2.,  3.])
	>>> v+w
	array([ 2.,  3.,  4.])
	>>> 2*v*w
	array([ 2.,  4.,  6.])
	>>> np.dot(v,w)
	6.0

## Linear Algebra with NumPy

There is a special matrix type for doing linear algebra, which is just a subclass of the array class. Operations on matrix-class arrays are linear algebra operations. Thus, in this case `*` is interpreted as matrix multiplication. In this case, the multiply function must be used for element-wise multiplication. In this tutorial we stick to the use of array. 

The interested reader is referred to the [SciPi website](http://www.scipy.org/NumPy_for_Matlab_Users) for a description of Matlab-lookalike features through the `matlib` subpackage of NumPy.

NumPy contains a `linalg` subpackage for doing numeric linear algebra computations.

### Creating Vectors and Matrices

There are some utility functions to create matrices and vectors. A few examples will illustrate constructions of matrices and vectors. The $$3 \times 4$$-matrix $$M$$ with $$M_{ij} = i^j$$ can be created as follows:

	>>> import numpy as np
	>>> import numpy.linalg as la
	>>> M = np.array([[i**j for j in range(1,5)] \
	              for i in range(1,4)])
	>>> M
	array([[ 1,  1,  1,  1],
	       [ 2,  4,  8, 16],
	       [ 3,  9, 27, 81]])

One can also define an user-defined indexing function to generate a matrix:

	>>> def band(i,j): return (0 if abs(i-j)>1 else 1)
    >>> N = np.array([band(i,j) for i in range(1,5) \
                  for j in range(1,5)]).reshape(4,4)
    >>> N
    array([[1, 1, 0, 0],
           [1, 1, 1, 0],
           [0, 1, 1, 1],
           [0, 0, 1, 1]])

Here we have used that one can reshape an existing matrix or vector:

	>>> np.arange(12).reshape(3,4)
	array([[ 0,  1,  2,  3],
	       [ 4,  5,  6,  7],
	       [ 8,  9, 10, 11]])

Some utility functions to create matrices with 0's and 1's.

	>>> Z = np.zeros((2, 4)); Z
	array([[ 0.,  0.,  0.,  0.],
	       [ 0.,  0.,  0.,  0.]])
	>>> I = np.eye(3); I
	array([[ 1.,  0.,  0.],
	       [ 0.,  1.,  0.],
	       [ 0.,  0.,  1.]])
	>>> J = np.ones((3,3)); J
	array([[ 1.,  1.,  1.],
	       [ 1.,  1.,  1.],
	       [ 1.,  1.,  1.]])
	>>> D = np.diag(np.array([1,2,3])); D
	array([[1, 0, 0],
	       [0, 2, 0],
	       [0, 0, 3]])

Some utility functions to stack matrices horizontally or vertically:

	>>> np.hstack((M, I))
	array([[  1.,   1.,   1.,   1.,   1.,   0.,   0.],
	       [  2.,   4.,   8.,  16.,   0.,   1.,   0.],
	       [  3.,   9.,  27.,  81.,   0.,   0.,   1.]])
	>>> np.vstack((Z, M, Z))
	array([[  0.,   0.,   0.,   0.],
	       [  0.,   0.,   0.,   0.],
	       [  1.,   1.,   1.,   1.],
	       [  2.,   4.,   8.,  16.],
	       [  3.,   9.,  27.,  81.],
	       [  0.,   0.,   0.,   0.],
	       [  0.,   0.,   0.,   0.]])

## Basic Operations on Matrices

### The Transpose of a Matrix

	>>> M
	array([[ 1,  1,  1,  1],
	       [ 2,  4,  8, 16],
	       [ 3,  9, 27, 81]])
	>>> np.transpose(M)
	array([[ 1,  2,  3],
	       [ 1,  4,  9],
	       [ 1,  8, 27],
	       [ 1, 16, 81]])

### Power of a Square Matrix

    >>> la.matrix_power(N, 3)

### Trace and Determinant of a Square Matrix

	>>> N
	array([[1, 1, 0, 0],
	       [1, 1, 1, 0],
	       [0, 1, 1, 1],
	       [0, 0, 1, 1]])
	>>> np.trace(N)
	4
	>>> la.det(N)
	-1.0

### Eigenvalues and Eigenvectors

	>>> la.eigvals(N)
	array(...)
	>>> mu, v = la.eig(N)
	>>> mu; v
	array(...)
	array(...)

### Inverse of a Matrix

    >>> la.inv(N)

Also the Moore-Penrose inverse $$A^{+}$$ of a matrix $$A$$ can be computed. Recall that the Moore-Penrose inverse is defined as:

$$\displaystyle A^{+} = \lim_{x\rightarrow 0}(A^T \cdot  A + x^2 I)^{-1}\cdot  A^T$$

	>>> la.pinv(M)
	>>> np.dot(M, la.pinv(M))
	>>> np.round(_)

### Solving linear Equations

The linear system of equations $$\{x+y+z = 6, 2x-y = 7, 2y-z = 8\}$$ can be solved as follows:

    >>> A = np.array([[1,1,1], [2,-1,0], [0,2,-1]]); A
    array([[ 1,  1,  1],
           [ 2, -1,  0],
           [ 0,  2, -1]])
    >>> b = np.array([6,7,8]); b
    array([6, 7, 8])
    >>> x = la.solve(A, b); x
    array([ 5.,  3., -2.])
    >>> np.dot(A, x) - b
    array([ 0.,  0.,  0.])

### Standard Forms of Matrices

The singular value decomposition (SVD) of a matrix $$A$$ is a factorization of $$A$$ as $$A=U\cdot D\cdot V^T$$, where $$U$$ and $$V$$ are orthogonal matrices and $$D$$ is a diagonal matrix with non-negative entries. The singular value decomposition of the matrix

$$\left(\matrix{0&1&-3\cr 4&5&1\cr 1&4&-1\cr}\right)$$

can be computed as follows:

    >>> A = np.array([[0,1,-3], [4,5,1], [1,4,-1]]); A
    array([[ 0,  1, -3],
           [ 4,  5,  1],
           [ 1,  4, -1]])
    >>> U, D, V = la.svd(A, full_matrices=True);
    >>> U
    array([[-0.11505136, -0.85300248,  0.50906773],
           [-0.84379953,  0.35434365,  0.4030421 ],
           [-0.52418083, -0.38318057, -0.76053081]])
    >>> V
    array([[-0.51848749, -0.85507847,  0.00339535],
           [ 0.29471894, -0.17497622,  0.93942752],
           [ 0.80269015, -0.48808209, -0.3427308 ]])
    >>> np.diag(D)
    array([[ 7.52068087,  0.        ,  0.        ],
           [ 0.        ,  3.50908567,  0.        ],
           [ 0.        ,  0.        ,  1.06097927]])
    >>> np.dot(U, np.dot(np.diag(D),V)) - A
    array([[  1.11022302e-16,  8.88178420e-16,  -1.77635684e-15],
           [ -4.44089210e-16,  0.00000000e+00,   6.66133815e-16],
           [  2.22044605e-16,  8.88178420e-16,  -8.88178420e-16]])
    >>> np.rint(_)
    array([[ 0.,  0., -0.],
           [-0.,  0.,  0.],
           [ 0.,  0., -0.]])

The final check of the answer illustrates that the singular value decomposition implemented in the `numpy.linalg` package strangely enough does not follow the convention to write $$V^T$$ instead of $$V$$ in this decomposition. This means that one still has to transpose the computed $$V$$ to arrive at the result according to the conventional definition of the SVD.

### Problem a

Consider the following three matrices:

$$ A=\left(\begin{array}{rrr} -3 & -1 & 0 \\ 4 & 7 & -10 \\ 4 & 3 & -3 \end{array}\right), \quad B=\left(\begin{array}{rrr} -2 & 2 & -5 \\ 12 & -7 & 20 \\ 6 & -4 & 11 \end{array}\right), \quad C=\left(\begin{array}{rrr} -2 & 14 & 8 \\ -1 & 10 & 6 \\ 1 & -13 & -8 \end{array}\right)$$

These matrices have the following properties:

$$ A^{4n+1} = A, B^n = B, C^{n+2} = 0$$, for all $$n = 1,2,3,4$$

Verify these properties by computing $$M^2, M^3, M^4$$ and $$M^5$$ for
$$M = A$$, $$M = B$$ and $$M = C$$.

### Problem b

The Cholesky decomposition of a positive-definite symmetric matrix $$A$$ is a factorization of $$A$$ as $$A=L\cdot L^T$$, where $$L$$ is a lower triangular matrix. The QR decomposition of a matrix $$A$$ is a factorization of $$A$$ as $$A=Q\cdot R$$, where $$Q$$ is an orthogonal matrix and $$R$$ is an upper-triangular matrix.

Compute with Python the Cholesky and QR decomposition of the following matrix:

$$ A=\left(\begin{array}{ccc} 5 & -2 & 2 \\ -2 & 5 & 1 \\ 2 & 1 & 2 \end{array}\right)$$
