# Instructions for Provisioning EC2 Instance

## EC2 Instance Setup
[Article On Setting up EC2 Instance](http://ramhiser.com/2016/01/05/installing-tensorflow-on-an-aws-ec2-instance-with-gpu-support/)

### Steps
1. Setup Spot Instance of g2.2xlarge with Ubuntu
2. Update package manager

	```bash
	sudo apt-get update
	sudo apt-get upgrade
	sudo apt-get install build-essential cmake g++ gfortran git pkg-config python-dev software-properties-common wget
	sudo apt-get install -y build-essential git python-pip libfreetype6-dev libxft-dev libncurses-dev libopenblas-dev gfortran python-matplotlib libblas-dev liblapack-dev libatlas-base-dev python-dev python-pydot linux-headers-generic linux-image-extra-virtual unzip python-numpy swig python-pandas python-sklearn unzip wget pkg-config zip g++ zlib1g-dev
sudo pip install -U pip
sudo apt-get autoremove 
	```

3. [Install Docker for Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntulinux/)

	```bash
	sudo apt-get install apt-transport-https ca-certificates
	sudo apt-key adv \
               --keyserver hkp://ha.pool.sks-keyservers.net:80 \
               --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    ```
   
   Check Ubuntu Version:

	```bash
	$ lsb_release -a
	
	Distributor ID:	Ubuntu
	Description:	Ubuntu 16.04.1 LTS
	Release:	16.04
	Codename:	xenial
	```
	
	```bash
	echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list
	sudo apt-get update
	apt-cache policy docker-engine
	sudo apt-get update
	sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
	sudo apt-get update
	sudo apt-get install docker-engine
	sudo service docker start
	sudo docker run hello-world
	```
	
4. [Install Nvidia drivers on EC2 Instance](https://github.com/saiprashanths/dl-setup#nvidia-drivers)

	Find your current Nvidia Model:

	```bash
	lspci | grep -i nvidia
	```

	[Get Current version of driver](http://www.nvidia.com/Download/index.aspx)
	![](nvidia_graphics_card.png)
	![](nvidia_driver_specs.png)

	```bash
	sudo add-apt-repository ppa:graphics-drivers/ppa
	sudo apt-get update
	
	# Current version on for GRID K520 on Linux = 367
	sudo apt-get install nvidia-367
	
	sudo shutdown -r now
	cat /proc/driver/nvidia/version
	```

5. [Download NVidia Docker Container](https://github.com/NVIDIA/nvidia-docker)

	```bash
	# Install nvidia-docker and nvidia-docker-plugin
	wget -P /tmp https://github.com/NVIDIA/nvidia-docker/releases/	download/v1.0.0-rc.3/nvidia-docker_1.0.0.rc.3-1_amd64.deb
	sudo dpkg -i /tmp/nvidia-docker*.deb && rm /tmp/nvidia-docker*.deb
	
	# Test nvidia-smi
	sudo nvidia-docker run --rm nvidia/cuda nvidia-smi
	```

	