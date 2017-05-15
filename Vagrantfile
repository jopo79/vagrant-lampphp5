# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "ubuntu/trusty64"
     # Mount shared folder using LINUX NFS
    config.vm.synced_folder ".", "/vagrant",
        id: "core",
        :nfs => true,
        :mount_options => ['nolock,vers=3,udp,noatime']

    # Forward ports to Apache and MySQL
    config.vm.network "private_network", ip: "192.168.100.100"
    config.vm.network "forwarded_port", guest: 80, host: 8888
    config.vm.network "forwarded_port", guest: 3306, host: 8889

	config.vm.provision "shell", path: "provision.sh"

  config.vm.provider "virtualbox" do |vb|
     # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "3072"]
     vb.customize ["modifyvm", :id, "--cpus", 2]
     
   end
   
   
   
end
