Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/jammy64"

  # APP SERVER
  config.vm.define "app-server" do |app|
    app.vm.hostname = "app-server"
    app.vm.network "private_network", ip: "192.168.56.101"

    app.vm.provider "virtualbox" do |vb|
      vb.name = "app-server"
      vb.memory = 2048
      vb.cpus = 2
    end

    app.vm.provision "shell", inline: <<-SHELL
      apt update -y
      apt install -y openjdk-17-jdk docker.io docker-compose maven git
      usermod -aG docker vagrant
      systemctl enable docker
      systemctl start docker
    SHELL
  end

  # DB SERVER
  config.vm.define "db-server" do |db|
    db.vm.hostname = "db-server"
    db.vm.network "private_network", ip: "192.168.56.102"

    db.vm.provider "virtualbox" do |vb|
      vb.name = "db-server"
      vb.memory = 1024
      vb.cpus = 1
    end

    db.vm.provision "shell", inline: <<-SHELL
      apt update -y
      apt install -y mysql-server
      systemctl enable mysql
      systemctl start mysql
    SHELL
  end

end
