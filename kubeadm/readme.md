# Overview

This repository will give you a high level of understanding of Kubeadm and clustering.
The kubeadm was chosen here as a more professional "flavor" of Kubernetes comparing to Minikube.
The repo is aimed at newbies (such as myself) to help understand such hard technology.

Start your Kubeadm journey by following the steps lower!

## Prerequisites

I decided to use libvirt as my virtualization provider, so virtualbox won't get the job done.

You need to install:
* Vagrant
* Ansible

Use the package manager of your distro.

```bash
$ sudo pacman -Sy vagrant ansible
```

Install vagrant-libvirt:

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

> **TIP:** Check my other projects! `$ cd ..` 

Wait a little bit and provision the rest by ansible playbook:

```bash
$ ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory setup.yaml
```

You shoud get the `success!` message later.

Check how your newly built cluster is doing:

```bash
$ vagrant ssh master-node
$ sudo kubectl get nodes
```

And now you are good to go!
