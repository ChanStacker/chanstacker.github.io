---
layout: post
title: "Docker Cheatsheet"
date: 2023-01-03 09:00:00 +0100
categories: Devops
---

#### Docker Cheat Sheet

* `docker container stop` vs `docker container kill` - to understand the difference, one has to know the underlying Linux signals issued under each command.  Stop issues a `SIGTERM` signal which is a graceful termination of a process where Kill issues a `SIGKILL` signal which is a forceful termination regardless of what the process intends to do with the signal.