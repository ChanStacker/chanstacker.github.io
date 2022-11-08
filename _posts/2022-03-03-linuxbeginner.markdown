---
layout: post
title:  "Linux for beginners"
date:   2022-03-03 09:00:00 +0100
categories: linux
---

* Kernel is the first software loaded when the computer boots – loaded by the bootloader. 
* Linux is a kernel – kernel is what interact software with hardware. 
* Kernel uses the device drivers to interact with the hardware. 
 
* GNU + Linux = a distro.  Ubuntu, Fedora and Mint are distros 

In linux, everything is shown as a file even hardwares 
`C`– character device 
`D` – block device 

## Beginner cheatsheet
* `ls`    List all the files in a directory
* `ls -l` List all files and their details (owner, mtime, size, etc)
* `ls -a` List all the files in a directory (including hidden files)
* `ls -ltra` List all the files sort by last modified time with most recently modified on top (including hidden files)
* `pwd` 	Show the present working directory
* `cd` 	    Change directory to some other location
* `file` 	View the type of any file
* `systemctl` Utility responsible for examining and analysing the systemd service manager
* `pstree` Displays the process tree
* `top` Displays info about the system and processes included memory. Switches: z, x, <, >, 1