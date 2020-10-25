Vagrant.configure("2") do |config|
  config.vm.define :wikijs do |wikijs|
    wikijs.vm.box = "bento/ubuntu-20.04"
    wikijs.vm.network "private_network", ip: "192.168.1.40"
    wikijs.vm.network "forwarded_port", guest: 3000, host: 3000
    wikijs.vm.hostname = "wikijs"
    wikijs.vm.synced_folder ".", "/vagrant", disabled: true
    wikijs.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update -y
      sudo apt-get install python-apt -y
    SHELL
  end

  config.vm.define :ansible do |ansible|
    ansible.vm.box = "bento/ubuntu-20.04"
    ansible.vm.network "private_network", ip: "192.168.1.50"
    ansible.vm.hostname = "ansible"
    ansible.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update -y
      sudo apt-get install software-properties-common -y
      sudo apt-add-repository --yes --update ppa:ansible/ansible
      sudo apt-get install ansible -y
      sudo ansible-galaxy collection install community.general
    SHELL
  end
end