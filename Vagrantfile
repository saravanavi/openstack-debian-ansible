# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|  
  config.vm.define :controller do |controller|
    controller.vm.box = "binarydata/debian-jessie"
    controller.vm.hostname = "controller"
    controller.vm.network :private_network, ip: "192.168.222.101" # eth1 internal
    controller.vm.network :private_network, ip: "192.168.221.101" # eth2 external
    controller.vm.provider "virtualbox" do |vbox|
      vbox.customize ["modifyvm", :id, "--memory", "2048"]
      vbox.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"] # eth2
      vbox.customize ["createhd",
                      '--filename', "tmp/disk",
                      '--size', "3000" ]
      vbox.customize ['storageattach', :id,
                     '--storagectl', 'SATA Controller',
                     '--port', 1,
                     '--device', 0,
                     '--type', 'hdd',
                     '--medium', "tmp/disk.vdi"]
    end
  end
end
