# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "boicotaz/ubuntu-20.04-gui"
  	config.vm.network "private_network", ip: "192.168.100.20", auto_config: true
	config.vm.network "forwarded_port", guest: 80, host: 8081, auto_correct: true
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
   #config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
   config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
     vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "1024"
   end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  
    #   apt-get update
    #	deplo
  #   apt-get install -y apache2
  
   config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get update
  	sudo apt-get install openjdk-8-jdk -y
  	sudo apt-get install openjdk-11-jdk -y

  	sudo apt-get install git -y
  	git clone https://github.com/SergioLangaritaBenitez/ElviraWebBackEnd.git
  	cp ElviraWebBackEnd/target/ElviraWebs-1.war ./ElviraWebs.war
  	http://localhost:8080/ElviraWebs-1/rest/elvira/graph
  	git clone https://github.com/SergioLangaritaBenitez/ElviraWeb.git
  	wget https://s3-eu-west-1.amazonaws.com/payara.fish/Payara+Downloads/5.194/payara-5.194.zip
  	unzip payara-5.194.zip
  	./payara5/bin/asadmin start-domain
  	./payara5/bin/asadmin deploy ./ElviraWebs.war
  	sudo apt install npm -y
  	#cp ./ElviraWeb/* ./ -r
  	#npm install ./ElviraWeb
  	#npm start
  	#https://addons.mozilla.org/es/firefox/addon/cors-everywhere/

   SHELL
end
