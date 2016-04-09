## Assignment 2

In this assignment, we're going to implement a Rubik's cube solver that follows along
with the instructions on a popular Rubik's cube solution site.

But we're going to change it a little. The human instructions ask you to turn the cube
upside down at one point. And we won't. Instead, we will *search* for an algorithm that
works the right way up.

Here's the instructions we will approximately follow
[How to solve a Rubik's cube'](http://how-to-solve-a-rubix-cube.com/)

I've done quite a bit of the coding for you. You'll need to explore my code a little.
And you'll need to reimplement the parts I've taken out of my code and replaced with ???

## The key to it...

There's 12 different "fundamental" operations we can do to the cube --
 there are six faces, and we can give any of them a quarter turn either clockwise or
 anticlockwise.

So, if we were to consider every possible set of moves, then even by the time we got to
 ten-move sequences, we'd have 61,917,364,224 possibilities.

So instead, we constrain the problem -- look to do it in stages, where we think each stage
can be made up of a small sequence of moves.

In the code, choosing a sequence of turns to apply is as simple as counting.
The numbers 0 to 11 are a single quarter-turn each (one of the twelve fundamental moves).
And above that, we're effectively counting in base 12 to work out what moves to apply.

After we've solved the top layer, we want to avoid mucking it up. So at this point we
sometimes change our set of moves we consider. Rather than considering every kind of
quarter turn, we consider turns that don't affect the top, plus little algorithms that
we've found that manipulate the bottom layers but preserve the current top position.

(Those are still done by counting, but the base is different depending on how many different
kinds of moves we're considering)


## Notes:

* Standard cube notation shows quarter-turns (90 degree turns) of faces:

  U = top clockwise
  D = bottom clockwise
  F = front clockwise
  B = back clockwise
  L = left clockwise
  R = right clockwise

  U' = top anticlockwise
  D' = bottom anticlockwise
  F' = front anticlockwise
  B' = back anticlockwise
  L' = left anticlockwise
  R' = right anticlockwise

* In the code, anticlockwise turns tend to look like `Turn.Ra` because `Turn.R'` would not compile.

* It's not all about the tests this time. There are some tests for "quick" things,
  like the CubeTests you've been asked to create. But there's also App which can be run.
  This will mix up a cube and run your solver on it.

  To run this, from sbt use the `run` command.

* Some marks are available for getting the tests to pass; some for how much of the cube it can solve; and some for the code.

