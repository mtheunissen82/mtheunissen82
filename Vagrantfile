# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.network "private_network", ip: "192.168.1.82"
  config.vm.hostname = "mtheunissen82"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "mtheunissen82"
    vb.memory = "2048"
  end

  # provision several usefull configuration files from guest to guest
  config.vm.provision "file", source: "~/.ssh/id_rsa", destination: "/home/vagrant/.ssh/id_rsa"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/id_rsa.pub"
  config.vm.provision "file", source: "~/.ssh/id_ed25519", destination: "/home/vagrant/.ssh/id_ed25519"
  config.vm.provision "file", source: "~/.ssh/id_ed25519.pub", destination: "/home/vagrant/.ssh/id_ed25519.pub"

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    chmod 600 /home/vagrant/.ssh/id_rsa
    chmod 644 /home/vagrant/.ssh/id_rsa.pub
    chmod 600 /home/vagrant/.ssh/id_ed25519
    chmod 644 /home/vagrant/.ssh/id_ed25519.pub

    sudo apt-get update -y

    sudo apt-get install -y vim curl cowsay fortune git silversearcher-ag npm

    npm install -g diff-so-fancy

    curl -o git-completion.bash https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
    sudo mv git-completion.bash /etc/bash_completion.d
  SHELL

  end
