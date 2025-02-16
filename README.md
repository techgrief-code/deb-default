# Remove cdrom from repository

    nano /etc/apt/sources.list
Remove or # the first (or all) cdrom line/s.
From:

    deb cdrom:...
To:

    #deb cdrom:...

# Update

    apt update -y && apt upgrade -y

# Install Sudo

    apt install sudo

# Static Ip
    sudo nano /etc/network/interfaces
Remove or # following:

>remember your network interface enp0s25

    allow-hotplug enp0s25  
    iface enp0s25 inet dhcp
Set your static ip in the same file.

> Replace **enp0s25** with your network interface
> Set your static ip like **192.168.1.56**
> Set your router ip (gateway)

    auto enp0s25
    iface enp0s25 inet static
            address 192.168.1.56
            netmask 255.255.255.0
            gateway 192.168.1.1
            dns-nameservers 1.1.1.1 8.8.8.8
Restart networking service

    sudo systemctl restart networking.service

# Install Docker

    wget https://gitlab.com/bmcgonag/docker_installs/-/raw/main/install_docker_nproxyman.sh
    chmod +x ./install_docker_nproxyman.sh
    ./install_docker_nproxyman.sh

# Install Dockge
### Create directories that store your stacks and stores Dockge's stack

    mkdir -p /opt/stacks /opt/dockge
    cd /opt/dockge

### Download the compose.yaml

    curl https://raw.githubusercontent.com/louislam/dockge/master/compose.yaml --output compose.yaml

### Start the server

    docker compose up -d

# Mount

