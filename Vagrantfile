# -*- mode: ruby -*-
# vi: set ft=ruby :

#VAGRANTFILE_API_VERSION = "2"

#Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
#  config.vm.box = "centos/7"
#  config.ssh.insert_key = false
#  config.vm.synced_folder ".", "/vagrant", disabled: true

#  config.vm.provider :virtualbox do |v|
#    v.name = "jenkins"
#    v.memory = 512
#    v.cpus = 2
#    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
#    v.customize ["modifyvm", :id, "--ioapic", "on"]
#  end

#  config.vm.hostname = "jenkins"
#  config.vm.network :private_network, ip: "192.168.33.55"

  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
#  config.vm.define :jenkins do |jenkins|
#  end

  # Ansible provisioner.
#  config.vm.provision "ansible" do |ansible|
#    ansible.playbook = "provisioning/playbook.yml"
#    ansible.inventory_path = "provisioning/inventory"
#    ansible.sudo = true
#  end

#end

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"
    config.vm.boot_timeout = 120
    config.vm.hostname = "jenkins"

    config.vm.provider "virtualbox" do |vb|
        vb.memory = 2048
        vb.cpus = 2
        vb.name = "jenkins"
    end

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provisioning/install.yml"
        ansible.host_key_checking = false
        ansible.sudo = true
        ansible.tags = ['common', 'java8', 'jenkins', 'maven', 'jenkins-plugins']
    end

    config.vm.network "private_network", ip: "192.168.107.10"
    config.vm.network "forwarded_port", host: 8080, guest: 8080, autocorrect: true
end