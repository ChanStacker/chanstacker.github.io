---
layout: post
title: "Kubectl basics"
date: 2023-06-18 06:00:00 +0100
categories: kubernetes
---

#### Configuring kubectl

* A kubeconfig file which is yaml based, is one of the ways to configure the context of kubectl tool.
* When using Rancher, the kubeconfig file can be downloaded from links on the top right of the Rancher UI.
* On Windows, kubectl can be configured by creating an environment variable `KUBECONFIG` with the value being the full path of the yaml config file.
* On Linux, the default location kubectl is going to locate the config file is `~/.kube/config`.  Basically rename the yaml file to simply `config` and place it in a `.kube` directory on the home dir.
* To check that the config is correctly picked up, run `kubectl config current-context`.  This shoud return the cluster name that the config file is pointing to.



