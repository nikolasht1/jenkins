# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: <<-SHELL
        apt-get update -y
        apt-get install openjdk-8-jre -y
        
        echo "10.0.0.103  bento-jenkins" >> /etc/hosts
    SHELL
    config.vm.provision :shell, path:"C:/jenkins/setJenkinsMachine.sh"
    config.vm.define "bento" do |bento|
        bento.vm.box = "bento/ubuntu-18.04"
        bento.vm.hostname = "bento-jenkins"
        bento.vm.network "private_network", ip: "10.0.0.103"
        bento.vm.provider "virtualbox" do |vb|
            vb.memory = 4096
            vb.cpus = 2
      end
      config.vm.provision :shell, path: "C:/jenkins/jenkins.sh"  
    end  
  end