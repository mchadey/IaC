# Vagrantfile
Vagrant.configure("2") do |config|

  # Define the first VM
  config.vm.define "AdeolaVM1" do |adeola_vm1|
    adeola_vm1.vm.box = "ubuntu/bionic64"
    adeola_vm1.vm.hostname = "AdeolaVM1"

    # Allocate memory and disk space
    adeola_vm1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 1
      vb.customize ["createhd", "--filename", "adeola_vm1_disk.vdi", "--size", 10240]
    end

    # Configure Static IP for SSH
    adeola_vm1.vm.network "private_network", ip: "192.168.50.4"

    # Provision the VM with required software and users
    adeola_vm1.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y nginx curl git ubuntu-desktop

      # Create users with passwords and passwordless sudo
      sudo adduser --disabled-password --gecos "" ade
      echo "ade:ade" | sudo chpasswd
      echo "ade ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ade

      sudo adduser --disabled-password --gecos "" ola
      echo "ola:ola" | sudo chpasswd
      echo "ola ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ola

      sudo adduser --disabled-password --gecos "" ope
      echo "ope:ope" | sudo chpasswd
      echo "ope ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ope
    SHELL
  end

  # Define the second VM
  config.vm.define "AdeolaVM2" do |adeola_vm2|
    adeola_vm2.vm.box = "ubuntu/bionic64"
    adeola_vm2.vm.hostname = "AdeolaVM2"

    # Allocate memory and disk space
    adeola_vm2.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 1
      vb.customize ["createhd", "--filename", "adeola_vm2_disk.vdi", "--size", 10240]
    end

    # Configure Static IP for SSH
    adeola_vm2.vm.network "private_network", ip: "192.168.50.5"

    # Provision the VM with required software and users
    adeola_vm2.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y nginx curl git ubuntu-desktop

      # Create users with passwords and passwordless sudo
      sudo adduser --disabled-password --gecos "" ade
      echo "ade:ade" | sudo chpasswd
      echo "ade ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ade

      sudo adduser --disabled-password --gecos "" ola
      echo "ola:ola" | sudo chpasswd
      echo "ola ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ola

      sudo adduser --disabled-password --gecos "" ope
      echo "ope:ope" | sudo chpasswd
      echo "ope ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ope
    SHELL
  end
end
