# Overview

This repository will give you a high level of understanding of Kubeadm and clustering.
The kubeadm was chosen here as a more professional "flavor" of Kubernetes comparing to Minikube.
The repo is aimed at newbies (such as myself) to help understand such a complex technology.

Start your Kubeadm journey by following the steps lower!

## Prerequisites

I decided to use libvirt as my virtualization provider, so virtualbox won't get the job done.

You need to install:

* Vagrant
* Ansible

Use the package manager of your distro.

Installation example for Arch Linux:

```bash
$ sudo pacman -Sy vagrant ansible
```

Install vagrant-libvirt and vagrant-scp:

```bash
$ vagrant plugin install vagrant-libvirt
```

## Setup

Clone the directory and deploy Vagrant VMs:

```bash
$ cd ~
$ git clone https://github.com/Starmaster99/headintheclouds.git
$ cd headintheclouds/kubeadm
$ vagrant up
```

> **TIP:** You can just follow the instructions you see in debug task messages.

Wait a little bit and provision the rest by ansible playbook:

```bash
$ ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory setup.yaml
```

You shoud get the `success!` message later.


## Deploy

Congratulations! Your first application has just been deployed. 

Simply navigate to [172.16.0.2:30001](http://172.16.0.2:30001) and marvel at its beauty.

> **NOTE:** It doesn't matter what node you choose to go to since Kubernetes has a built-in load balancer.
> We will touch the load balancer topic later.

If you just followed me here, you should see my static website. It will explain some general information about me.

## Links

* [Kubeadm official docs](https://kubernetes.io/)
* [What are init systems?](https://news.ycombinator.com/item?id=7203623)
* [Container runtimes](https://kubernetes.io/docs/setup/production-environment/container-runtimes/)
* [Kubernetes networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/#how-to-implement-the-kubernetes-networking-model)
