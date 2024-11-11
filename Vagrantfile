Vagrant.configure("2") do |config|
  
  # Especifica la caja base de Ubuntu
  config.vm.box = "ubuntu/bionic64"

  # Asigna 512 MB de RAM y 1 CPU
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  # Configuración de red (puerto 80 para el servidor web)
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Instala Apache al iniciar la VM
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
  SHELL

  # Sincroniza el directorio local con el directorio de Apache
  config.vm.synced_folder "./web", "/var/www/html"

end