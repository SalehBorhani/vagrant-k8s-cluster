Vagrant.configure("2") do |config|
  config.vm.define "amaster" do |amaster|
    amaster.vm.box_download_insecure = true
    amaster.vm.box = "generic/ubuntu2004"
    amaster.vm.network "private_network", ip: "192.168.56.2"
    amaster.vm.hostname = "amaster"
    amaster.vm.provider "virtualbox" do |v|
      v.name = "amaster"
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "kmaster" do |kmaster|
    kmaster.vm.box_download_insecure = true
    kmaster.vm.box = "generic/ubuntu2004"
    kmaster.vm.network "private_network", ip: "192.168.56.3"
    kmaster.vm.hostname = "kmaster"
    kmaster.vm.provider "virtualbox" do |v|
      v.name = "kmaster"
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "kworker" do |kworker|
    kworker.vm.box_download_insecure = true
    kworker.vm.box = "generic/ubuntu2004"
    kworker.vm.network "private_network", ip: "192.168.56.4"
    kworker.vm.hostname = "kworker"
    kworker.vm.provider "virtualbox" do |v|
      v.name = "kworker"
      v.memory = 2048
      v.cpus = 2
    end
  end

end