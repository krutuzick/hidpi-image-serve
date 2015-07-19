# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.6.3"

Vagrant.configure("2") do |config|
    config.vm.define "hidpi-image-serve.machine" do |hidpi_config|
        # basic configuration
        hidpi_config.vm.box = 'hashicorp/precise64'
        hidpi_config.vm.hostname = 'hidpi-image-serve'
        hidpi_config.vm.network :private_network, ip: '192.168.55.55'
        
        # virtual machine configuration
        hidpi_config.vm.provider "virtualbox" do |v|
            v.gui = false
            v.name = 'hidpi-image-serve.machine'
            v.memory = 512
            v.cpus = 1
            v.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
        end
    end
    
    
    # fix "no tty" notice on Windows hosts
    config.vm.provision "shell", privileged: false, inline: "sudo sed -i '/tty/!s/mesg n/tty -s \\&\\& mesg n/' /root/.profile"
    
    # install nginx and attach config
    $shell_provision = <<SCRIPT
apt-get -qqy update > /dev/null 2>&1
apt-get -qqy install nginx > /dev/null 2>&1

rm -rf /etc/nginx/sites-enabled/*

for f in /vagrant/nginx/*.conf
do
    ln -snf $f /etc/nginx/sites-enabled/$(basename "$f")
done

service nginx restart

SCRIPT
    config.vm.provision "shell", inline: $shell_provision
end