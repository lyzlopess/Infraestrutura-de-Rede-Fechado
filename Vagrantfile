Vagrant.configure("2") do |config|
  # Configuracao da Gateway - Servidor Gateway e Firewall
  config.vm.box = "generic/ubuntu2004"

  config.vm.define "gateway" do |gateway|
    gateway.vm.hostname = "gateway"
    gateway.vm.network "private_network", type: "static", ip: "192.168.56.1"
    gateway.vm.network "public_network", type: "dhcp"
    gateway.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    gateway.vm.provision "shell", inline: <<-SCRIPT
      # Instalacao do Apache
      sudo apt update
      sudo apt install net-tools
      sudo apt install -y apache2
    SCRIPT
  end

  # Configuracao da VM1 - Maquina Cliente 01
  config.vm.define "vm1" do |vm1|
    vm1.vm.hostname = "vm1"
    vm1.vm.network "private_network", type: "static", ip: "192.168.56.10"
    vm1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    vm1.vm.provision "shell", inline: <<-SCRIPT
      # Instalacao do MySQL
      sudo apt update
      sudo apt install net-tools
      sudo apt install -y mysql-server
      sudo ip route add default via 192.168.56.1
    SCRIPT
  end

  # Configuracao da VM2 - Maquina Cliente 02
  config.vm.define "vm2" do |vm2|
    vm2.vm.hostname = "vm2"
    vm2.vm.network "private_network", type: "static", ip: "192.168.56.20"
    vm2.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    vm2.vm.provision "shell", inline: <<-SCRIPT
      # Instalacao do MySQL
      sudo apt update
      sudo apt install net-tools
      sudo apt install -y mysql-server
      sudo ip route add default via 192.168.56.1
    SCRIPT
  end
end

