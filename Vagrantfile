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
    napalm.vm.network "private_network", virtualbox__intnet: "swp1"
    napalm.vm.network "private_network", virtualbox__intnet: "swp2"
    #napalm.vm.network "private_network", virtualbox__intnet: "swp3"
    #napalm.vm.network "private_network", virtualbox__intnet: "swp4"
    napalm.vm.provision "shell", inline: <<-SHELL
      sudo apt-get install -y lldpd
      sudo apt-get install -y python-pip python-dev build-essential 
      sudo pip install --upgrade pip 
      sudo pip install napalm
      SHELL
    end

    config.vm.define "veos" do |veos|
      veos.vm.box = veos
      veos.vm.provider :virtualbox do |vb|
        #vb.customize ["modifyvm", :id, "--memory", "512"]
        #vb.customize ["modifyvm", :id, "--cpus", "1"]
        #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
      end
      veos.vm.hostname = "veos"
      veos.vm.network "private_network", virtualbox__intnet: "swp1"
      #veos.vm.network "private_network", virtualbox__intnet: "swp2"
      #veos.vm.network "private_network", virtualbox__intnet: "swp3"
      #veos.vm.network "private_network", virtualbox__intnet: "swp4"
    end

      config.vm.define "junos" do |junos|
        junos.vm.box = junos
        junos.vm.provider :virtualbox do |vb|
          #vb.customize ["modifyvm", :id, "--memory", "512"]
          #vb.customize ["modifyvm", :id, "--cpus", "1"]
          #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
        end
        junos.vm.hostname = "junos"
        #junos.vm.network "private_network", virtualbox__intnet: "swp1"
        junos.vm.network "private_network", virtualbox__intnet: "swp2"
        #junos.vm.network "private_network", virtualbox__intnet: "swp3"
        #junos.vm.network "private_network", virtualbox__intnet: "swp4"
      end
end