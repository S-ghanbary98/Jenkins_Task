

Vagrant.configure("2") do |config|
    config.vm.box = "hashicorp/bionic64"
    config.vm.network "private_network", ip: "192.168.10.150"
    config.vm.provision "shell", path: "provision.sh"
end
