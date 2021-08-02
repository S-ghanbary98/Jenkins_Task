# Jenkins Setup 

## Vagrant, VirtualBox and Jenkins

Setting up Jenkins can be done relatively easily and with full automation using a `provision.sh` file which should contain the following.
```python
!#/bash

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt install openjdk-11-jdk -y      # Download Java
java -version
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update -y 
sudo apt-get install jenkins -y   #Installing Jenkins

```

The configuration for the virtual machine can be found in the Vagrantfile, which is the following.

```python

Vagrant.configure("2") do |config|
    config.vm.box = "hashicorp/bionic64"    # Configured for Ubuntu 18-04
    config.vm.network "private_network", ip: "192.168.10.150"
    config.vm.provision "shell", path: "provision.sh"
end

```