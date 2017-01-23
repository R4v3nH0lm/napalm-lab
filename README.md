# napalm-lab

## Setup ##

### Required Software ###
Download and install VirtualBox.
Download and install Vagrant.

### Vagrant ###
This will require the following vagrant boxes be available on your system:
- juniper/ffp-12.1X47-D15.4-packetmode
- ubuntu/trusty64
- vEOS-lab-4.17.3F

### VirtualBox ###
The VM running napalm will require atleast 1024MB to run or else napalm will fail to compile during pip install.

## Tree ##
	.
	└── napalm_lab
		├── README.md
		└── Vagrantfile
	   