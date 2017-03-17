# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # create debian_lab node
  config.vm.define :debian_lab do |debian_lab_config|
      debian_lab_config.vm.box = "debian/jessie64"
      debian_lab_config.vm.hostname = "debian-lab"
      debian_lab_config.vm.network :private_network, ip: "192.168.64.10"
      debian_lab_config.vm.network "forwarded_port", guest: 80, host: 8010
      debian_lab_config.vm.synced_folder "sync_debian_lab", "/sync_host_data"
      debian_lab_config.vm.provider "virtualbox" do |vb|
          vb.memory = "1024"
      end
      debian_lab_config.vm.provision "ansible" do |ansible|
          ansible.playbook = "playbook.yml"
      end
  end


  # create centos_lab node
  config.vm.define :centos_lab do |centos_lab_config|
      centos_lab_config.vm.box = "centos/7"
      centos_lab_config.vm.hostname = "centos-lab"
      centos_lab_config.vm.network :private_network, ip: "192.168.64.20"
      centos_lab_config.vm.network "forwarded_port", guest: 80, host: 8020
      centos_lab_config.vm.synced_folder "sync_centos_lab", "/sync_host_data"
      centos_lab_config.vm.provider "virtualbox" do |vb|
          vb.memory = "1024"
      end
      centos_lab_config.vm.provision "ansible" do |ansible|
          ansible.playbook = "playbook.yml"
      end
  end

end
