# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
 
  config.vm.box = "boicotaz/ubuntu-20.04-gui"
  	config.vm.network "private_network", ip: "192.168.100.20", auto_config: true
	config.vm.network "forwarded_port", guest: 80, host: 8081, auto_correct: true

   config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"



   config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     vb.memory = "1024"
   end

  
   config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get update
  	sudo apt-get install openjdk-8-jdk -y
  	sudo apt-get install openjdk-11-jdk -y

  	sudo apt-get install git -y
  	git clone https://github.com/SergioLangaritaBenitez/ElviraWebBackEnd.git
  	cp ElviraWebBackEnd/target/ElviraWebs-1.war ./ElviraWebs.war
  	#http://localhost:8080/ElviraWebs-1/rest/elvira/graph
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
