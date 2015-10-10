# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  
  config.vm.synced_folder "./www", "/vagrant_data"
  config.vm.synced_folder "./sites", "/etc/apache2/sites-available"
  config.vm.synced_folder "./logs", "/var/log/apache2"

   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "1024"
   end

   config.vm.provision "shell", inline: <<-SHELL
     sudo -i     
     export DEBIAN_FRONTEND=noninteractive
     apt-get update
     apt-get install -y apache2 php5 mysql-server php5-sybase php5-mcrypt php5-curl nmap htop curl php5-mysql git phpunit npm
     a2enmod rewrite
     php5enmod mcrypt
     php5enmod curl
     curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin -- --filename=composer
     echo "127.0.0.1 api.sample admin.sample frontend.sample" >> /etc/hosts

     
   SHELL
   
   config.vm.network :forwarded_port, host: 80, guest: 80
   config.vm.network :forwarded_port, host: 3306, guest: 3306
   
end
