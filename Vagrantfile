# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'yaml'

yaml = YAML.load_file("environment.yaml")

Vagrant.configure("2") do |config|
  yaml.each do |server|


    config.vm.define server["name"] do |srv|
      srv.vm.box = server["system"]
      srv.vm.network "private_network", ip: server["ip"]
      srv.vm.hostname = server["hostname"]
      srv.vm.provider "virtualbox" do |vb|
        vb.name = server["name"]
        vb.memory = server["memory"]
        vb.cpus = server["cpus"]
      end

      config.vm.provision "shell", inline: "cp -r /vagrant/k3s-lab /home/vagrant"
      config.vm.provision "shell", inline: "cp /vagrant/hosts /etc/hosts"

    end
  end
end   
