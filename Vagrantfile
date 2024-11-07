# Vagrantfile para crear una máquina virtual con Apache
Vagrant.configure("2") do |config|
    # tiempo de arranque
    config.vm.boot_timeout = 900
  
    # Ubuntu
    config.vm.box = "ubuntu/bionic64"
  
    # recursos de la máquina virtual
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"     
      vb.cpus = 2           
    end
  
    #carpeta 
    config.vm.synced_folder "./", "/var/www/html", SharedFoldersEnableSymlinksCreate: false
  
    # IP estatica
    config.vm.network "private_network", ip: "192.168.56.10"
  
    # Configurar el script 
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo ufw allow 'Apache Full'
    SHELL
  
    config.vm.hostname = "apache-server"
  end