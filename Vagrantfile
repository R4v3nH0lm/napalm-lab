kali = "Sliim/kali-linux-2.0-amd64"
centos = "centos/7"
cumulus = "cumulus-linux-3.1.1"
junos = "juniper/ffp-12.1X47-D15.4-packetmode"
ubuntu = "ubuntu/trusty64"
veos = "vEOS-lab-4.17.3F"

Vagrant.configure("2") do |config|
  config.vm.define "napalm" do |napalm|
    napalm.vm.box = ubuntu
    napalm.vm.hostname = "napalm"
    napalm.vm.network "private_network", virtualbox__intnet: "link_1", ip: "10.0.1.100"
    napalm.vm.network "private_network", virtualbox__intnet: "link_2", ip: "10.0.2.100"
    #napalm.vm.network "private_network", virtualbox__intnet: "swp3"
    #napalm.vm.network "private_network", virtualbox__intnet: "swp4"
    napalm.vm.provision "shell", inline: <<-SHELL
      sudo apt-get install -y lldpd
      sudo apt-get install -y libffi-dev libssl-dev libxml2-dev libxslt1-dev
      sudo apt-get install -y python-pip python-dev build-essential 
      sudo pip install napalm
    SHELL
  end

  config.vm.define "vEOS" do |vEOS|
    vEOS.vm.box = veos
    vEOS.vm.provider :virtualbox do |vb|
      #vb.customize ["modifyvm", :id, "--memory", "512"]
      #vb.customize ["modifyvm", :id, "--cpus", "1"]
      #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    end
    vEOS.vm.hostname = "vEOS"
    vEOS.vm.network "private_network", virtualbox__intnet: "link_1", ip: "169.254.1.11", auto_config: false
    #vEOS.vm.network "private_network", virtualbox__intnet: "swp2"
    #vEOS.vm.network "private_network", virtualbox__intnet: "swp3"
    #vEOS.vm.network "private_network", virtualbox__intnet: "swp4"
  end

  config.vm.define "juniper" do |juniper|
    juniper.vm.box = junos
    juniper.vm.provider :virtualbox do |vb|
      #vb.customize ["modifyvm", :id, "--memory", "512"]
      #vb.customize ["modifyvm", :id, "--cpus", "1"]
      #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    end
    juniper.vm.hostname = "juniper"
    #juniper.vm.network "private_network", virtualbox__intnet: "swp1"
    juniper.vm.network "private_network", virtualbox__intnet: "link_2", ip: "169.254.1.11", auto_config: false
    #juniper.vm.network "private_network", virtualbox__intnet: "swp3"
    #juniper.vm.network "private_network", virtualbox__intnet: "swp4"
  end
end