# -*- mode: ruby -*-
# vi: set ft=ruby : vsa

Vagrant.configure(2) do |config| 
 config.vm.box = "centos/8" 
 config.vm.box_version = "2011.0" 
 config.vm.provider "virtualbox" do |v| 
 v.memory = 512 
 v.cpus = 1 
 end 
 config.vm.define "syst" do |syst| 
 #syst.vm.network "private_network", ip: "192.168.56.10",  virtualbox__intnet: "net1" 
 syst.vm.hostname = "syst" 
 end 
   config.vm.provision "shell", inline: <<-SHELL
      cd /etc/yum.repos.d/
      sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
      sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
      yum install nano -y
   SHELL
end
