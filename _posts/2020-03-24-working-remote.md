---
title: 'Working Remotely'
date: 2020-03-22
permalink: /posts/2020/03/working-remotely/
tags:
  - research
---

## Working Remotely

Due to Coronavirus, everybody is working remotely from home. This has given me the opportunity to dig into different options for remotely connecting to the Deep Learning computer running Ubuntu we have in our lab. Unix is the preferred code development environment for many code developers, and since I only have a Windows machine available at home, I'm doing my best to ditch my local Windows environment for a remote Unix environment using SSH!

The tools I detail below are the most-used tools for our machine learning research. As long as I'm able to edit and run Python code (`.py` files) and Jupyter notebooks (`.ipynb` files), I'm able continue my work relatively uninterrupted. Let's get into it!

## SSH Basics

1. Connect to the network the remote machine is connected to
    - In our case, I connect to the UIUC network using the Cisco AnyConnect VPN software

1. In Windows Command Prompt, set up a basic SSH connection using the following command

        $ssh username_on_remote_machine@remote_machine_ip_address

    - I also use the Bitvise software for the visual file browser which makes transfer of files between machines easier

1. You now have a terminal to run commands on the remote machine

## Directly edit files on a remote machine (using VS Code)

You can directly SSH using certain text editors, allowing use of a familiar text editing environment. Gone are the days of using Vim or Emacs to edit files on a remote machine through a difficult-to-learn interface (I would learn it, but there's no incentive in my current role!). In this case I use Visual Studio Code, although I'm sure other text editors support a similar functionality.

1. Install the "Remote - SSH" extension for Visual Studio Code

1. Add a new SSH connection by typing `ctrl+shift+p` and searching Remote-SSH: Add New SSH Host.  Enter the same information as with a normal SSH connection

        $ ssh username_on_remote_machine@remote_machine_ip_address

1. Type `ctrl+shift+p` and search Remote-SSH: Connect to Host, then select the desired SSH connection
    - If successful, a new window will appear which is directly connected to the remote machine

1. You can now edit files on the remote machine as if they were on your local machine

## Running Jupyter Notebooks on a Remote machine

1. Start a Jupyter notebook using a terminal SSHed into the remote machine

        $ jupyter notebook --no-browser --port=8080

    - note that the choice of port 8080 is arbitrary

1. Port forward to your local machine using

        $ ssh -N -L 8080:localhost:8080 username_on_remote_machine@remote_machine_ip_address

1. You can now copy the jupyter notebook URL (make sure to include the token) to a browser on your local machine, and it will open the Jupyter notebook running on the remote machine
