#The Collatz Conjecture

As you may observe, your problem sets are getting shorter and shorter. A sign that we regard you as somewhat experienced programmers, who can translate a problem into an algorithm, and then real code.

##The Conjecture

The conjecture of Collatz which made him world famous can easily be formulated. It is basically the following game: 

* choose some positive integer *n*; 
* if *n* is even, divide it by two;
* if *n* is odd, multiply by three and add one;
* treat the newly obtained number in the same manner.

In 1937, Collatz formulated a conjecture that no matter what number *n* one starts with, one will always eventually reach 1.

### Example

An example of a  Collatz sequence is: 7 &rarr; 22 &rarr; 11 &rarr; 34 &rarr; 17 &rarr; 52 &rarr; 26 &rarr; 13 &rarr; 40 &rarr; 20 &rarr; 10 &rarr; 5 &rarr; 16 &rarr; 8 &rarr; 4 &rarr; 2 &rarr; 1.

The challenge of proving this conjecture is well characterized by the title of the following paper:  Guy, R. (1983), *Don't try to solve these problems*, American Mathematical Monthly, 90, 35-41.

Paul Erd&ouml;s, allegedly, once said about the Collatz problem: "Mathematics is not yet ripe enough for such problems". Thus, we recommend to graduate first.

### Problem a

Write a function that returns a Collatz sequence (represented as a list) for a given positive integer *n*. Build in your code some efficiency steps and apply the function to generate the Collatz sequence that starts at 27. Is length should be 112.

### Problem b

Write a function that  returns  a list of all Collatz sequence (represented as a list) that start with an positive integer less than a given positive integer *n*. Use it to print out every Collatz sequence that starts with a number from 1 up to 29. Also print the lengths of these Collatz sequences.

### Problem c

Determine the longest Collatz sequence that starts with a number less than 100000. What is its length and with which number does it start?

### Problem d

Determine the Collatz sequence of length 500 with the smallest starting point.

##Note

You can put your problems a-d in one file, for example `ps7.py`. If you do that, please make each problem into a function, e.g. `problem_a` - `problem_d`. Have each function print out the solution to the problem. Make sure each function clearly states its name when outputting solutions to the screen.

