# Numerical Differentiation

## Scientific Computing with Python

Various open-source add-on modules to Python make the programming language very suitable for scientific computing purposes. This will be illustrated by examples from linear algebra, statistics, and data plotting.

**NumPy** (Numeric Python) is an open-source add-on module to Python that provides common mathematical and numerical routines in pre-compiled, fast functions. It provides basic routines for manipulating large arrays and matrices of numeric data. For example, it contains the well-known LAPACK library for doing linear algebra.

**Matplotlib** is an open-source add-on module to Python for 2D plotting that generates production quality graphs in Matlab style.

## Importing Modules

#### NOTE: We expect you to try all examples below in your own Python shell.

Like any Python module, one must import NumPy before it can be used. This can be done in several ways, but a recommended way is to import it under a brief name, say `np`:

	>>> import numpy as np

Similarly, the Matplotlib module must be imported first. For example, one can import the basic plotting facilities, stored in the subpackage pyplot, under an abbreviated name, say `plt`:

	>>> import matplotlib.pyplot as plt

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
	array([ 0.        , 0.22222222, 0.44444444, 0.66666667, 0.88888889,
	        1.11111111, 1.33333333, 1.55555556, 1.77777778, 2.        ])
	>>> y = x**2 # quadratic function values
	>>> y
	array([ 0.        , 0.04938272, 0.19753086, 0.44444444, 0.79012346,
	        1.2345679 , 1.77777778, 2.41975309, 3.16049383, 4.        ])
	>>> z = np.log(x) # logarithmic function values
	>>> z
	array([ 0.        , 0.2006707 , 0.36772478, 0.51082562, 0.63598877,
                0.7472144 , 0.84729786, 0.93826964, 1.02165125,  1.09861229])

A plot of y vs. x can now be created as follows:

	>>> plt.plot(x, y)
	[<matplotlib.lines.Line2D object at 0x03D3F770>]

Only a plot object is created; it is not immediately displayed in a figure. The reason is that one can add more plots to a figure and change styles. For example, one can add a plot of the cubic values as red open circles and make gridlines visible.

	>>> plt.plot(x, z, 'ro') # plot points are red open circles 
	[<matplotlib.lines.Line2D object at 0x03D3FB70>]
	>>> plt.grid(True) # display grid

To display the figure in a separate window, enter the following command

    >>> plt.show()

![plot1](plot1.svg)

The window contains interactive controls: for example, one can pan and zoom in or out, and save the figure. After closing the window, the figure object cannot be accessed anymore (unless it was assigned to a name). One can also immediately save the figure in a file, in various formats, by the savefig command:

	>>> plt.plot(x, y, 'r-') # points connected by red line segments
	>>> plt.savefig('C:/temp/fig1.jpg') # save figure in JPEG format

## Numerical Differentiation

In experimental work, one is often faced with the problem of finding the derivative of a function $$f(x)$$ whose form is only known as a tabulation of data. Suppose that one has a sequence of equally spaced points $$x_0, x_1, x_2, ..., x_n$$ with distance $$dx = x_1 - x_0$$, and function values $$y_0, y_1, y_2, ..., y_n$$. The numerical derivative $$f'(x)$$ of the function $$f(x)$$ can be approximated by a sequence $$y'_0, y'_1, y'_2, ..., y'_n$$ computed via the following central divided difference formula:

$$y_k' = (y_(k+1) - y_(k-1))/(2dx)$$, for $$k=1,2,...,n-1$$.

It is based on averaging the following approximations of $$f(x)$$ for small values of $$h$$:

$$f'(x) ~~ (f(x+h)+f(x))/h$$ and $$f'(x) ~~ (f(x) + f(x-h))/h$$.

At the endpoints of the interval one can apply the following formulas:

$$y_0' = (-3y_0+4y_1-y_2)/(2dx)$$ and $$y_n' = (3y_n-4y_(n-1)+y_(n-2))/(2dx)$$.

#### Assignment

Use the `NumPy` and `Matplotlib` modules to implement the above numerical differentiation in Python and to apply the algorithm for the sine function approximated by function values calculated for 25 equally spaced points in the interval $$[0,2pi]$$ (Hint: use the NumPy function roll to rotate arrays). Draw data plots of $$y$$ and $$y'$$ in one figure. What do you think of the result? Does it improve when more data points are available, say 101 equally spaced points? Does your code still works fine when you use 1000001 equally spaced points in the interval $$[0,2pi]$$?
