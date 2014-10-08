# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "precise64"
  config.vm.network :private_network, ip: '192.168.33.10'
  config.vm.network :forwarded_port, guest: 8080, host: 4080
  config.vm.network :forwarded_port, guest: 8680, host: 4680
  config.vm.network :forwarded_port, guest: 8480, host: 4480
  config.vm.network :forwarded_port, guest: 8380, host: 4380
  config.vm.network :forwarded_port, guest: 8280, host: 4280

  config.vm.synced_folder "/tmp/artifacts", "/tmp/artifacts", create: true
  config.vm.provision :puppet, :module_path => "manifests/modules" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "default.pp"
  end
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end
end
