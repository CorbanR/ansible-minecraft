# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  end
  config.vm.provider "vmware_fusion" do |vm, override|
    override.vm.box = "CorbanRaun/jessie64"
    vm.vmx["memsize"] = "2048"
    vm.vmx["numvcpus"] = "2"
  end
  config.vm.define "minecraft" do |rundmc|
    rundmc.vm.hostname = "minecraft"
    rundmc.vm.provision "ansible" do |ansible|
      ansible.limit = 'all'
      ansible.playbook = "vagrant.yml"
    end
  end
end
