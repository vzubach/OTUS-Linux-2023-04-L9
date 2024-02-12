# -*- mode: ruby -*-
# vi: set ft=ruby : vsa

Vagrant.configure(2) do |config| 
 config.vm.box = "centos/8" 
 config.vm.box_version = "2011.0" 
 config.vm.provider "virtualbox" do |v| 
 v.memory = 1024
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
      yum install epel-release -y && yum install spawn-fcgi php httpd -y
	cp /vagrant/LogService/watchlog.* /etc/systemd/system/
	cp /vagrant/LogService/watchlog /etc/sysconfig/
	cp /vagrant/LogService/watchlog.sh /opt/
	cp /vagrant/LogService/watchlog.log /var/log/
	cp /vagrant/Spawn/spawn-fcgi.service /etc/systemd/system/
	cp /vagrant/Spawn/spawn-fcgi /etc/sysconfig/
	cp /vagrant/Apache/httpd.service /etc/systemd/system/
	cp /vagrant/Apache/httpd-* /etc/sysconfig/
	cp /vagrant/Apache/first.conf /etc/httpd/conf/
	cp /vagrant/Apache/second.conf /etc/httpd/conf/
	systemctl start watchlog.timer
	systemctl start spawn-fcgi.service
	systemctl start httpd@first
	systemctl start httpd@second
   SHELL
end
