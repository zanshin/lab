# Introduction
Simple Vagrant project to create a number of small VMs, to be used as lab machines. For example, as
a fleet of machine to be managed by Ansible.

The `Vagrantfile` has an array of servers defined, each with a name, IP Address, and operating
system. This array is used to create the VMs.

Finally a GPG public key is added to each VMs authorized_keys file, to allow easy access.
