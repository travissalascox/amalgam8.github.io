# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
sudo apt-get -y update
sudo apt-get -y install curl git
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -sSL https://get.rvm.io | bash -s stable
. ~/.bashrc
. ~/.bash_profile
rvm install 2.2.2
rvm --default use 2.2.2
cd /vagrant
gem install bundler
bundle update

# install nodejs4 - needed for some jekyll plugins
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
sudo apt-get install -y nodejs
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-12.04"
  config.vm.hostname = "jekyll"
  config.vm.network "private_network", ip: "192.168.33.100"
  config.vm.provision "shell", inline: $script, privileged: false
  config.vm.synced_folder ".", "/vagrant"
end