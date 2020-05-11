Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder "/Users/kennyh/IaC", "/vagrant"
  config.vm.network :private_network, ip: "192.168.4.2"
  config.vm.network :public_network, bridge: "en2: Wi-Fi (AirPort)", ip: "192.168.1.245"
  config.vm.network "forwarded_port", guest: 8080, host: 8081
  config.vm.network "forwarded_port", guest: 8081, host: 8082
  config.vm.network "forwarded_port", guest: 9000, host: 9000
  config.vm.hostname = "docker-host"

  config.vm.provider :virtualbox do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "2"]
  end

  config.vm.provision "ansible" do |ansible|
  ansible.playbook = "./playbooks/master-playbook.yml"

  end
end
