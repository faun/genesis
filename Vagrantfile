# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "pairing" do |node|
    node.vm.box = "hashicorp/precise64"
    node.vm.provision "ansible" do |ansible|
      ansible.inventory_path = "ansible/inventory"
      ansible.playbook = "pairing.yml"
    end
  end

  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_vagrant'
    override.vm.box = 'digital_ocean'
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"

    provider.token = ENV.fetch('DIGITAL_OCEAN_TOKEN')
    provider.image = 'ubuntu-14-04-x64'
    provider.region = 'sfo1'
    provider.size = '512mb'
  end
end
