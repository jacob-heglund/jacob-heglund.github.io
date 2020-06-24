---
title: 'Running Remote Jobs'
date: 2020-06-24
permalink: /posts/2020/06/running-remote-jobs/
tags:
  - research
---

## Running Remote Jobs

While working remotely, I haven't yet had the opportunity to really take advantage of the computational resources in our lab. That changed this week when I started running different experiments for an upcoming paper. Before, if my internet connection went down, my laptop went to sleep, or anything else happened to interrupt my ssh connection to the lab computer, the job on the lab computer would stop because the terminal controlling the job had stopped. That changes today!

Using a program called "screen", the process being run (i.e. python automation.py) can be detached from its controlling terminal, meaning it can run in the background without worrying about the connection between my home laptop and the lab computer. Note that there there are other programs out there like tmux that also give similar functionality. Screen works just fine for me, so I'm sharing how I use the program.

1. After opening an ssh connection to the remote computer, start the screen program in the terminal

        $ screen

1. From here, you can start a process

        $ python automation.py

1. The process is now running, and now you can detach it from the controlling terminal (and make it safe from a dropped ssh connection) by typing "ctrl+a, d"

1. To view the process and reattach it to the current terminal, type the following to see the available running processes that have been detached using screen

    $ screen -r

1. Then use the same command with the corresponding process ID to reattach the process

    $ screen -r PID

1. If you have multiple choices in the -r menu and want to delete some, you can kill a window by reattaching it, and typing "ctrl+a, k"

And those are the basics of using screen to run remote jobs without worrying about the ssh connection dropping! I haven't found need for any other features of the program yet, but if I do I will be sure to either update this post or make a new one.
