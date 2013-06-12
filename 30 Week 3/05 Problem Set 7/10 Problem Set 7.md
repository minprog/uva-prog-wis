# The Collatz conjecture

As you may observe, your problem sets are getting shorter and shorter. A sign
that we regard you as somewhat experienced programmers, who can translate a
problem into an algorithm, and then into working code.

## The game

The conjecture of Collatz can easily be formulated. It is basically the
following game:

* choose some positive integer $$n$$; 
* if $$n$$ is even, divide it by two;
* if $$n$$ is odd, multiply by three and add one;
* treat the newly obtained number in the same manner.

In 1937, Collatz formulated his conjecture that no matter what number $$n$$ one
starts with, one will always eventually reach 1.

## Example

An example of a Collatz sequence is: $$7 -> 22 -> 11 -> 34 -> 17 -> 52 -> 26 -> 13 -> 40 -> 20 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1$$.

The challenge of proving this conjecture is well characterized by the title of
the following paper: Guy, R. (1983), *Don't try to solve these problems*,
American Mathematical Monthly, 90, 35-41.

Paul Erdös, allegedly, once said about the Collatz problem: "Mathematics is not
yet ripe enough for such problems". In other words, we recommend that you
graduate before trying it.

You should put your problems a--d in one file, for example `ps7.py`. Please make each problem into a function, e.g. `problem_a`, `problem_b`. Have each function print out the solution to the problem. Make sure each function clearly states its name when outputting solutions to the screen.

## Problem a: one sequence

Write a function that returns a Collatz sequence represented as a list for a
given positive integer `n`. Refactor your code to make it more efficient, and
apply the function to generate the Collatz sequence that starts at 27. Its
length should be 112.

## Problem b: a list of sequences

Write a function that returns a list of all Collatz sequences that start with
an positive integer less than a given positive integer `n`. As before, each
single sequence should be represented as a list. Use it to print out every
Collatz sequence that starts with a number from 1 up to 29. Also print the
lengths of these Collatz sequences.

## Problem c: the longest sequence

Determine the longest Collatz sequence that starts with a number less than 100000. What is its length and with which number does it start?

## Problem d: the smallest starting point

Determine the Collatz sequence of length 500 with the smallest starting point.
