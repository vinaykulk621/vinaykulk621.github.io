+++
date = '2026-04-05T11:30:32+05:30'
title = 'Viper And Cobra for GO CLI application'
+++

After a long time of procastination, i finally learnt how to make CLI applications in go using [cobra](https://cobra.dev) and [viper](https://github.com/spf13/viper).

### What is cobra and viper

| cobra                                                                                                    | viper                                                                      |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| cobra is a library to define how the user interacts with your CLI, Think of it as a skeleton for the CLI | viper is library which handles the data that is needed for the CLI to work |
| Things like `--help`, godoc and LLM friendly docs generation is handled by cobra                         | Providing and handling data such as config files is handled by viper       |

### What i made with it

At work, i often need to figure out what subnet does a VM/server belongs to based on the hostname/IpAddress. Manually it requires me to navigate through multiple browser tabs and auth pages, and is really slow and boring, so i built a tool to get the subnet information for a given hostname/IpAddress

---

And...... it works like it should, there were few bugs and errors that i had to go through and fix them by debugging and stuff, but overall productive tool.
