Vagrant.configure("2") do |config|

  if Vagrant.has_plugin?("vagrant-vbguest")
  config.vbguest.auto_update = false
  end
  config.vm.boot_timeout = 600


  # =======================
  # VM Application : srv-back
  # =======================
  config.vm.define "srv-back" do |srv_back|
    srv_back.vm.box = "ubuntu/jammy64"
    srv_back.vm.box_check_update = false

    srv_back.vm.network "forwarded_port", guest: 8080, host: 8081
    srv_back.vm.network "private_network", ip: "192.168.56.14"

    # Synchroniser le projet complet avec la VM
    srv_back.vm.synced_folder "C:/Users/DELL/IdeaProjects/Tp3-spring-boot-devops", "/home/vagrant/project"

    srv_back.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "srv-back"
      vb.cpus = 2
      vb.memory = 1024
    end
  end

  # =======================
  # VM Database : srv-dba
  # =======================
  config.vm.define "srv-dba" do |srv_dba|
    srv_dba.vm.box = "ubuntu/jammy64"
    srv_dba.vm.box_check_update = false

    srv_dba.vm.network "private_network", ip: "192.168.56.15"

    srv_dba.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "srv-dba"
      vb.cpus = 2
      vb.memory = 1024
    end
  end

  # =======================
  # VM Frontend : srv-front
  # =======================
  config.vm.define "srv-front" do |srv_front|
    srv_front.vm.box = "ubuntu/jammy64"
    srv_front.vm.box_check_update = false
    srv_front.vm.network "private_network", ip: "192.168.56.16"

    srv_front.vm.synced_folder "C:/Users/DELL/IdeaProjects/frontend", "/home/vagrant/frontend"

    srv_front.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "srv-front"
      vb.cpus = 2
      vb.memory = 1024
    end
  end

end
