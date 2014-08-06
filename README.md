# Prequisites

The first step is to install Vagrant, VirtualBox, and Ansible on your computer.

1. [Install Vagrant](http://www.vagrantup.com/downloads.html)
2. [Install VirtualBox](https://www.virtualbox.org/wiki/Downloads)
3. [Install Ansible](http://docs.ansible.com/intro_installation.html#latest-releases-via-homebrew-mac-osx)

## Vagrantfile

This defines the operating system and other configuration for the virtual machine.

This will create a box using Ubuntu 14.04 Trusty 64-bit with 1 GB of memory. It will also forward ports 3000 and 5432 from the virtual machine so we can access Rails web server and PostgreSQL db server from the host machine.

*Note:* You may have to change lines 33 and 34 and replace `appname` to the actual name of your project.

## Ansible playbooks

Ansible will provision the dev box and will install all the necessary packages to setup Git, rbenv, Ruby 2.1.2 and PostgreSQL. Feel free to modify the files inside the `provision` folder to suit your needs, like installing MySQL instead.

*Note:* To change the version of Ruby and other variables used in the playbook, just edit `provision\setup\vars\main.yml`.

# Running Vagrant

Copy the `provision` folder and `Vagrantfile` into your project directory and run `vagrant up` on the terminal.

This will take a while because it will provision the virtual machine with the Ansible playbook. To ssh into the dev box, use `vagrant ssh`.


If you made changes to the playbook later, you can use this command to reconfigure the machine.

`vagrant provision`

