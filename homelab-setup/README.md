# Homelab environment
Build your own homelab environment in a few minutes! Ideal for learning, practicing and testing as it is virtual and doesn't affect host. You can build and destroy it whole day long!

## Setup
We will be using [Vagrant](https://vagrantup.com/). I have two Vagrantfiles (config files for Vagrant), which are used by Vagrant to control hypervisors ([virtualbox](https://www.virtualbox.org/) and [libvirt](https://en.wikipedia.org/wiki/Libvirt)), that control virtual machines. I'll show methods for several platforms.

### Linux

I installed it on my Debian server. Feel free to install it on whatever Linux machine you want, just use the package manager of your distro.

```bash
$ sudo apt-get install vagrant
```
As simple as it can get.

I have a fully working Vagrantfile that manages virtualbox and [Vagrant can use it right away](#usage), but for now I will concentrate on installing libvirt, as it is a bit tricky to install and use for the first time.

Now we need to install some packages that allow Vagrant to use libvirt. Install these:

```bash
$ sudo apt-get install virt-manager libvirt libvirt-daemon libvirt-clients python3-libvirt vagrant-libvirt
```

And now add your user to the libvirt group:

```bash
$ sudo adduser $(id -un) libvirt
```

We are almost finished. Now clone this repo and modify the IP:

```bash
$ git clone https://github.com/Starmaster99/headintheclouds.git
$ cd headintheclouds/homelab-setup/
$ vim libvirt
```

Look for these two:

`sub.vm.network "public_network", ip: "192.168.31.221", "bridge": "enp2s0", "dev": "enp2s0"`\
`sub.vm.network "public_network", ip: "192.168.31.22#{i+1}", "bridge": "enp2s0", "dev": "enp2s0"`

Change the `192.168.31.1` to your router's IP. You might want to use `192.168.1.1` or `192.168.0.1` or something else entirely.

And now you are pretty much done!

## Usage

Vagrant docs can be found [here](https://www.vagrantup.com/docs). All Vagrant command-line interface (CLI) commands are [here](https://www.vagrantup.com/docs/cli). You can browse Vagrant boxes (the images of distros that Vagrant can use, or *the package format for Vagrant environments*) [here](https://app.vagrantup.com/boxes/search), though I use CentOS 7 box.

If you want another box, just change the `IMAGE` variable in the header of the file.\
If you want more or less than two running machines, change the `NODES` variable.

Start the Vagrant:
```bash
$ vagrant up
```
SSH into the one specific machine:
```bash
$ vagrant ssh foo
```
Stop the running machines:
```bash
$ vagrant halt
```
Destroy all machines:
```bash
$ vagrant destroy
```
