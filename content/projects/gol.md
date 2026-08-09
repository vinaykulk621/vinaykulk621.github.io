+++
date = '2026-08-09T11:15:15+05:30'
title = 'Game of Life'
+++

![gol](/images/gol.gif "Game of Life demo")

This following project is built using [GO](https://go.dev) and [bubblete](https://github.com/charmbracelet/bubbletea). and no **AI** was used to create this project.

following are the rules:

- Live cell with < 2 neighbors → dies
- Live cell with 2 or 3 neighbors → lives
- Live cell with > 3 neighbors → dies (overpopulation)
- Dead cell with exactly 3 neighbors → becomes alive

To add chaos and continuity of the game i've added the below rules

- Every 7 seconds: 20% of live cells die
- Every 10 seconds: 30% of dead cells resurrect

---

Build this project on your machine:

```bash
git clone github.com/vinaykulk621/gol.git && cd gol
go mod tidy
go build -o gol
```
