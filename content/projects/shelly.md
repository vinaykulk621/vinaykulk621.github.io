+++
date = '2026-07-17T22:15:06+05:30'
title = 'Shelly'
+++

[shelly](https://github.com/vinaykulk621/shelly) (_noun_): A terminal based LLM client to help you in your terminal when you forget what that linux command was.

Shelly was inspired by [this](https://z3ugma.github.io/2026/05/25/a-comma-and-a-question-mark/) article and is built using [cobra](https://cobra.dev) and [viper](https://github.com/spf13/viper), source code: [github.com/vinaykulk621/shelly](https://github.com/vinaykulk621/shelly)

Following is some of the ways that i think shelly can prove it's usage

---

1. Error analysis:

```shell
tail piserver.log | shelly "explain why did the server crash??"
```

2. Linux commands:

```shell
docker ps -a | shelly "awk command to get first column here??"
```

3. Build/Test failures:

```shell
go test ./... -v 2>&1 | shelly "how to fix this??"
```

4. Commands:

```shell
shelly "command to delete all the txt files except requirement.txt, in cwd?"
```
