Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/jammy64"

  # MASTER NODE
  config.vm.define "app-server" do |master|
    master.vm.hostname = "k8s-master"
    master.vm.network "private_network", ip: "192.168.56.10"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end

  # WORKER NODE
  config.vm.define "db-server" do |worker|
    worker.vm.hostname = "k8s-worker"
    worker.vm.network "private_network", ip: "192.168.56.11"
    worker.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end
  end

end
