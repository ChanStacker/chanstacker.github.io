---
layout: post
title: "VMs in VirtualBox"
date: 2023-05-09 06:00:00 +0100
categories: kubernetes
---

#### Installing VirtualBox on Windows

#### Downloading Ubuntu image

#### Creating a VM with the Ubuntu image

#### Assigning root privilege to user
Restart the VM and hit F12 to access the Advanced Options
Select the recovery mode and this will give a list of options
One of the options will be "Drop to root shell", select this option
A shell will option that will ask for the current user's password
Run the command `usermod -aG root <username>` to add user to root
Run the command `whoami` and this will now display `root`

#### Installing the guest additions - for copy/paste


