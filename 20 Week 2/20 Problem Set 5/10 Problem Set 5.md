# Gambler's ruin

In problem sets 5 and 6 you will simulate two kind of games of flipping coins
*Gamblers's ruin* and *Penney Ante*. These problems will illustrate how you can
group commands, possibly found in an interactive session, into functions so
that a Python program to simulate the game under consideration is gradually
developed. You practice the use of loops, conditionals and lists in Python.

## Description of the Coin Game

John and Sarah are flipping a coin. This coin is supposed to be fair, i.e., the
probability that it comes up heads equals one half. Each time it comes up head,
John pays Sarah one dollar; if it comes up tails, Sarah pays John one dollar.
The gambling is over when one player is broke. At the beginning of the game
John has four dollars to play with and Sarah has five dollars.

The questions that we want to answer via simulation of the gambling game are

* what is the probability that Sarah wins the game?
* what is the average length of the gambling game?

## Flipping the Coin

Sarah's profit when flipping the coin is one dollar if it comes up head and
minus one dollar if it comes up tail. So, from her point of view, it is
convenient to let a result head correspond to a value of $$1$$ (one dollar
gain) and to let a result tail correspond to a value of $$-1$$ (one dollar
loss). Then, flipping the coin is a random generation of $$1$$s and $$-1$$s
with equal probability and Sarah's amount of dollars at each step is adding the
random number to her current amount.

There are many ways to randomly generate numbers in Python, but the following
one seems appropriate: import the module `random` and then use
`random.randint(start,end)` to generate a random integer $$n$$ with $$a <= n <=
b$$.

### Problem a: getting started

Write a short program that does this:

* start a gambling game in which John and Sarah initially 
  have 5 and 10 coins respectively,
* flip the coin once, and 
* do some bookkeeping to store the amount of coins John 
  and Sarah have afterwards.

Save your program in `ps5a.py`.

## Problem b: repetition

Save your previous program as `ps5b.py` and add statements that
implement a loop that stops when one of the players is broke.

Repeat the previous step until the gambling game is over. The game goes on if none of the players is broke at the particular moment. Think of a Boolean expression implements this stopping condition. Because the length of the game is interesting, introduce the variable `number_of_tosses` that counts the number of times the coin is flipped. This variable is updated during the repetitive process of flipping the coin.

## Problem c: the game as a function

Now that you managed to simulate one game, you can collect all commands into a
function. Call this function game and assume that it is called with the initial
amounts of money of the players as actual arguments. It should return the
number of tosses needed for the game to finish because one of the players is
broke and the name of the winner.

Save your previous program as `ps5c.py`. Now incorporate your previous program
in a function called `game`. Call the function several times with the same
arguments to make sure that your function really implements a random game.

## Problem d: simulation of Gambler's Ruin

You can now play any number of games and analyze the results. Save your
previous program as `ps5d.py` and add the following functionality:
 
* Make a list of 10 games and extract from this a list of game lengths and the
  number of time Sarah wins.
 
* Next, do a large simulation of games, say 10,000 games, and analyze the
  results by statistical methods, i.e., compute the mean game length, its
  variance, the probability that Sarah wins this game, the average length of
  games won by Sarah, and the average length of games won by John.

Compare your results with the theoretical answers to the 
following questions. If John and Sarah start with $$m$$ and $$n$$ 
coins, respectively

* What is the average game length? Answer: $$m*n$$
* What is the variance of the game length? Answer: $$m*n*(m^2+n^2-2)/3$$
* What is the chance that Sarah wins?  Answer: $$n/(m+n)$$
* What is the average length of games won by Sarah when she 
  starts with 10 coins and John with 5 coins? 
  Answer: $$125 / 3 ~~ 41.666...$$
* What is the average length of games won by John when he 
  starts with 5 coins and Sarah with 10 coins? 
  Answer: $$200 / 3 ~~ 66.666...$$

Is your code sufficiently efficient to work well for as many as 100,000 games? Try it!
