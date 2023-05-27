Vagrant.configure(2) do |config|
    #ansible = <<-ANSIBLE
    #yum -y install ansible
    #ANSIBLE
    common = <<-SCRIPT
    if ! grep -q controlz /etc/hosts; then  sudo echo "192.168.56.120     controlz" >> /etc/hosts ;fi
    if ! grep -q node01 /etc/hosts; then  sudo echo "192.168.56.121     node01" >> /etc/hosts ;fi
    if ! grep -q node02 /etc/hosts; then  sudo echo "192.168.56.122     node02" >> /etc/hosts ;fi
    if ! id saleh >  /dev/null 2>&1 ; then sudo useradd -m -s /bin/bash -p $(openssl passwd -1 ubuntu) saleh; fi
    if [ ! -f /etc/sudoers.d/saleh ] ; then sudo echo "saleh        ALL=(ALL)       NOPASSWD: ALL" > /etc/sudoers.d/saleh ; fi
    sudo apt update
    sudo apt -y install net-tools git python3-pip
    SCRIPT
    
    #ansible_control_node = <<-SCRIPT
    #SCRIPT
  
      config.vm.box = "ubuntu/focal64"
      config.vm.box_url = "https://app.vagrantup.com/ubuntu/boxes/focal64"
  
      config.vm.define "controlz" do |control|
          control.vm.hostname = "controlz"
          control.vm.network "private_network", ip: "192.168.56.120"
          control.vm.provider "virtualbox" do |v|
              v.customize [ "modifyvm", :id, "--cpus", "1" ]
              v.customize [ "modifyvm", :id, "--memory", "312" ]
          end
          #config.vm.provision :shell, :inline => ansible
          config.vm.provision :shell, :inline => common
          #config.vm.provision "ansible_local" do |ansible|
          #	ansible.playbook = "playbook.yml"
          #end
      end
      config.vm.define "node01" do |node1|
          node1.vm.hostname = "node01"
          node1.vm.network "private_network", ip: "192.168.56.121"
          node1.vm.provider "virtualbox" do |v|
              v.customize [ "modifyvm", :id, "--cpus", "2" ]
              v.customize [ "modifyvm", :id, "--memory", "2000" ]
          end
          #config.vm.provision :shell, :inline => ansible
          config.vm.provision :shell, :inline => common
          #config.vm.provision "ansible_local" do |ansible|
          #	ansible.playbook = "playbook.yml"
          #end
      end
      config.vm.define "node02" do |node2|
          node2.vm.hostname = "node02"
          node2.vm.network "private_network", ip: "192.168.56.122"
          node2.vm.provider "virtualbox" do |v|
              v.customize [ "modifyvm", :id, "--cpus", "2" ]
              v.customize [ "modifyvm", :id, "--memory", "2000" ]
          end
          #config.vm.provision :shell, :inline => ansible
          config.vm.provision :shell, :inline => common
          #config.vm.provision "ansible_local" do |ansible|
          #	ansible.playbook = "playbook.yml"
          #end
      end
  end