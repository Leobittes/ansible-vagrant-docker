
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "public_network"
  config.vm.synced_folder "./ansible", "/ansible"
  config.vm.boot_timeout
  # config.vm.box_check_update = false
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  # config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
    # vb.name - "vagrant-docker-ansible"
    vb.memory = "1024"
    end
  
    config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    # apt-get install -y ansible
    ansible-playbook --connection=local /ansible/playbook.yml
  SHELL
end
