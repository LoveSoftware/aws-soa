# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

  config.vm.define "ansible" do |an|
    
    # Box template to use  
    an.vm.box = "ubuntu/trusty64"

    an.vm.network "private_network", ip: "192.168.4.55"

    an.vm.synced_folder ".", "/vagrant", type: "nfs" 

    an.ssh.forward_agent = true

    an.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.memory = 2048
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.customize ["modifyvm", :id, "--natnet1", "10.0.8.0/24"]
    end

  end

  config.vm.define "web" do |w|
    
    # Box template to use  
    w.vm.box = "labs12.04"
    
    # Increase memory available
    w.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end

    w.vm.network "private_network", ip: "192.168.4.56"

    w.vm.synced_folder ".", "/vagrant", type: "nfs"
    
    w.ssh.forward_agent = true

  end
  
end
