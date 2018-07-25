# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"
    config.vm.boot_timeout = 120
    config.vm.hostname = "jenkins"
    ##### If we use Ubuntu Windows we have a problem with SSH private key. This is a solution
    #config.ssh.private_key_path = "~/private_key"


    config.vm.provider "virtualbox" do |vb|
        vb.memory = 2048
        vb.cpus = 2
        vb.name = "jenkins"
    end
 # Ansible configuration
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provisioning/install.yml"
        ansible.host_key_checking = false
        ansible.sudo = true
        ansible.tags = ['common', 'java8', 'jenkins', 'maven', 'jenkins-plugins']
    end

    config.vm.network "private_network", ip: "192.168.107.10"
    config.vm.network "forwarded_port", host: 8080, guest: 8080, autocorrect: true
end