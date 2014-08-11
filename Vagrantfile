# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.synced_folder "./built_package", "/vagrant_data/built_package"
  #config.vm.provider "virtualbox" do |v|
  #  v.memory = 1024 
  #  v.cpus = 2
  #end

# Puppet
  
  config.vm.synced_folder "puppet/modules", "/tmp/vagrant-puppet/puppet/modules"
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.options = ["--modulepath", "/tmp/vagrant-puppet/puppet/modules"]
    puppet.manifest_file  = "site.pp"
  end
  config.vm.provision :shell, :path => "mono_build.sh"

end
