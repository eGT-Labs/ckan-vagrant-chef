# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.berkshelf.enabled = true
  config.vm.box = 'bento/centos-7.2'
  config.vm.hostname = 'default.ckanhosted.dev'
  config.vm.network :private_network, ip: '192.168.42.42'
  config.vm.network "forwarded_port", guest: 8983, host: 8983
  config.vm.network "forwarded_port", guest: 5000, host: 5000  # paster server (development)

  config.vm.provider 'virtualbox' do |v|
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.provision :chef_solo do |chef|
    chef.run_list = [
      "recipe[ckan]"
    ]
  end
end
