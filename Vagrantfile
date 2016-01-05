$hosts_script = <<SCRIPT
cat > /etc/hosts <<EOF
127.0.0.1       localhost
192.168.100.100		cdh-master
192.168.100.101		cdh-slave1
192.168.100.102		cdh-slave2
192.168.100.103		cdh-slave3


EOF
SCRIPT

Vagrant.configure("2") do |config|

  # Define base image
  config.vm.box = "cdh5v2"
  config.vm.box_url = "https://www.dropbox.com/s/iz3gu6ljred9n7s/cdh5v2.box"

  config.hostmanager.enabled = false
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true
  config.hostmanager.ignore_private_ip = false

  config.vm.define :master do |master|
    master.vm.provider :virtualbox do |v|
      v.name = "master-vm"
      v.customize ["modifyvm", :id, "--memory", "4096"]
    end
    master.vm.network :private_network, ip: "192.168.100.100"
    master.vm.hostname = "master-vm"
    master.vm.provision :shell, :inline => $hosts_script
    master.vm.provision :hostmanager
  end

  config.vm.define :slave1 do |slave1|
    slave1.vm.box = "cdh5v2"
    slave1.vm.provider :virtualbox do |v|
      v.name = "slave1-vm"
      v.customize ["modifyvm", :id, "--memory", "2048"]
    end
    slave1.vm.network :private_network, ip: "192.168.100.101"
    slave1.vm.hostname = "slave1-vm"
    slave1.vm.provision :shell, :inline => $hosts_script
    slave1.vm.provision :hostmanager
  end

  config.vm.define :slave2 do |slave2|
    slave2.vm.box = "cdh5v2"
    slave2.vm.provider :virtualbox do |v|
      v.name = "slave2-vm"
      v.customize ["modifyvm", :id, "--memory", "2048"]
    end
    slave2.vm.network :private_network, ip: "192.168.100.102"
    slave2.vm.hostname = "slave2-vm"
    slave2.vm.provision :shell, :inline => $hosts_script
    slave2.vm.provision :hostmanager
  end

  config.vm.define :slave3 do |slave3|
    slave3.vm.box = "cdh5v2"
    slave3.vm.provider :virtualbox do |v|
      v.name = "slave3-vm"
      v.customize ["modifyvm", :id, "--memory", "2048"]
    end
    slave3.vm.network :private_network, ip: "192.168.100.103"
    slave3.vm.hostname = "slave3-vm"
    slave3.vm.provision :shell, :inline => $hosts_script
    slave3.vm.provision :hostmanager
  end

end