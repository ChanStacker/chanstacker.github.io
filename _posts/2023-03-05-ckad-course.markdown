---
layout: post
title: "Kubernetes For Developers LFD259"
date: 2023-03-05 09:00:00 +0100
categories: kubernetes
---

#### Setting up kubernetes cluster
* The course requires a kubernetes cluster to be running in order to do the labs.  There are instructions on how to achieve it on different platforms.  I decided to pick Google Cloud to gain exposure to the cloud platform. 
* Setting `Google Cloud` was relatively easy.  There are $300 free credit available when creating a Google cloud account.
* A link will be provided in the course for scripts that help set up the Control Plane and the Worker nodes
* When using `wget` to download the scripts, ensure that the underscores are copied over in the link. syntax of wget command is: `wget <URL> --user=<username> --password=<password>`
* There is a script to set up the Control Plane node and another one to set up the Worker node.
* Once the Control Plane and the Worker nodes are set up, it is time for the worker node to join the Control Plane, command is of syntax: `kubeadm join <ControlPlaneNodeIp>:6443 --token <token> --discovery-token-ca-cert-hash <ControlPlaneNodeCertHash>`
* The join token is only valid for 23 hours. In order to add a worker node after that, the command below is to regenerate the token along with the full syntax to run on the worker node: `kubeadm token create --print-join-command`
* In a Production scenarios, Control Plane nodes do not run any application container.  To prevent scheduling of a container, Kubernetes applies `taints` to the CP node.  A `taint` is a key value pair that attaches attributes to nodes.  To view the taint on nodes if any, run `kubeclt get nodes | grep -i taint`

