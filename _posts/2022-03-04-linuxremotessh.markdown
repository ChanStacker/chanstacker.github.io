---
layout: post
title:  "Remoting onto a linux server"
date:   2022-03-04 09:00:00 +0100
categories: linux
---

* Even though username/password (basic auth) can be used to remote on a linux box, the preferred way to remote is `SSH`. 
* The commands typed on a local shell session are routed through a secure tunnel to the remote machine for execution.
* `ssh {user}@{host}` - is the key command that instructs your system that you want to open an encrypted Secure Shell Connection.

## SSH authentication process using asymmetric encryption
* The user must first generate a SSH key pair.
* To add permission for the user on a linux machine, the public key of the user is added under `~/.ssh/authorized_keys`.
* When user attempt to connect to remote, the `public key` is sent upon which remote checks if the `public key` is exist as an authorised key.
* If so, remote generates a random string and encrypts it with the `public key` of the user and send it client.
* The client then uses its `private key` to decrypt the random string.
* The client combines the random string with a previously negotiated session id and generates an MD5 hash.
* The hash is sent to the remote.  Given that the latter already has both the session id and the random string, it performs the same Md5 hashing operation and compares with the value sent by the client.
* If the hashes match, it concludes that the client is authentic as it needed to have the correct `private key` to be able to decrypt the random string.
