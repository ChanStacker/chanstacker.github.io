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
* `tree -d n` Display a tree of directories
* `pwd` 	Show the present working directory
* `cd` 	    Change directory to some other location
* `file` 	View the type of any file
* `systemctl` Utility responsible for examining and analysing the systemd service manager
* `pstree` Displays the process tree
* `top` Displays info about the system and processes included memory. Switches: z, x, <, >, 1

## GUI
* GNOME and KDE are popular Graphical interfaces for linux
* Graphical desktops can be started and stopped depending on distribution
`sudo system stop gdm`
`sudo system start gdm`

`$ sudo shutdown -h 01:00 "Message to the users"` - this is to schedule a shutdown of the system with a message sent to the users.  `shutdown` is the command to also reboot the system when passing the switch `-r`

`which <applicationname>` and `whereis <applicationname>`  - to locate the source of an application and to find the man files respectively.

## File Utilities
* `wc` word count, gives also the number of lines
* `cat` displays the content of a file, with -n to display the line number
* `less` displays a file in a paginate way, -N for line number
* `head` with switch -<n>, shows first n lines of a file
* `tail` with switch -<n>, shows last n lines of a file

  
