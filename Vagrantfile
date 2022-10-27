# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  if Vagrant.has_plugin? "vagrant-vbguest"
    config.vbguest.no_install  = true
    config.vbguest.auto_update = false
    config.vbguest.no_remote   = true
  end

  config.vm.define :balanceador do |balanceador|
    balanceador.vm.box = "bento/ubuntu-20.04"
    balanceador.vm.network :private_network, ip: "192.168.100.2"
    balanceador.vm.hostname = "balanceador"
    balanceador.vm.provision "shell", path: "scriptBalanceador.sh", :args => "192.168.100.2"
  end

  config.vm.define :servidor1 do |servidor1|
    servidor1.vm.box = "bento/ubuntu-20.04"
    servidor1.vm.network :private_network, ip: "192.168.100.3"
    servidor1.vm.hostname = "servidor1"
    servidor1.vm.provision "shell", path: "scriptServicios.sh", :args => "192.168.100.3 2 192.168.100.2"
  end

  config.vm.define :servidor2 do |servidor2|
    servidor2.vm.box = "bento/ubuntu-20.04"
    servidor2.vm.network :private_network, ip: "192.168.100.4"
    servidor2.vm.hostname = "servidor2"
    servidor2.vm.provision "shell", path: "scriptServicios.sh", :args => "192.168.100.4 2 192.168.100.2"
  end
end