# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

 # Set memory and cpu size
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "2048"]
    v.name = "test"
  end

 # Vagrant box
  config.vm.box = "laravel/homestead"

 # Network
  config.vm.network "private_network", ip: "192.168.44.44"
  config.vm.network "forwarded_port", guest: 3306, host: 33060
  config.vm.network "forwarded_port", guest: 22, host: 23
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # Install those to be able to use gitfs
  config.vm.provision :shell, :inline => "sudo apt-get -y install git-core"
  config.vm.provision :shell, :inline => "sudo apt-get -y install python-setuptools"
  config.vm.provision :shell, :inline => "sudo easy_install GitPython"

 # Install SaltStack
  config.vm.provision "shell", inline: "curl -L https://bootstrap.saltstack.com | sudo sh"

 # Shared
  config.vm.synced_folder ".", "/var/www", :nfs => true
end