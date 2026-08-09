+++
date = '2026-08-09T09:59:21+05:30'
title = 'Game of Life'
+++

[conway's Game of Life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) has an infinite grid where the each cell is either a live cell or dead cell.

On each iteration each cell is evaluated to certain set of rules.

following are the rules:

- Live cell with < 2 neighbors → dies
- Live cell with 2 or 3 neighbors → lives
- Live cell with > 3 neighbors → dies (overpopulation)
- Dead cell with exactly 3 neighbors → becomes alive

To add chaos and continuity of the game i've added the below rules

- Every 7 seconds: 20% of live cells die
- Every 10 seconds: 30% of dead cells resurrect

Following is the result you see:

![gol](/images/gol.gif "Game of Life executable demo")

Checkout Code: [github.com/vinaykulk621/gol.git](https://github.com/vinaykulk621/gol.git)
