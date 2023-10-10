# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
    vb.check_guest_additions = false
  end

  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.define "docker-node" do |node|

    node.vm.box = "ubuntu2004g"
    node.vm.hostname = "docker-node"
    # node.vm.network "forwarded_port", guest: 9100, host: 9100, host_ip: "127.0.0.1"
    # node.vm.network "forwarded_port", guest: 9090, host: 9090, host_ip: "127.0.0.1"
    node.vm.network "forwarded_port", guest: 3000, host: 3000, host_ip: "127.0.0.1"

    node.vm.provision :ansible, run: "always" do |ansible|
      ansible.compatibility_mode = "2.0"  
      ansible.playbook = "provisioning/main.yml"
    end

  end

end
