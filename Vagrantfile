Vagrant.configure("2") do |config|
  
  config.vm.define "napalm" do |napalm|
    napalm.vm.box = "ubuntu/trusty64"
    napalm.vm.hostname = "napalm"
    napalm.vm.network "private_network", virtualbox__intnet: "swp1"
    napalm.vm.network "private_network", virtualbox__intnet: "swp2"
    napalm.vm.network "private_network", virtualbox__intnet: "swp3"
    #napalm.vm.network "private_network", virtualbox__intnet: "swp4"
    napalm.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      SHELL
  end
end