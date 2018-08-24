Vagrant.configure("2") do |config|

  config.vm.define "etcd" do |etcd|
    etcd.vm.box = "ubuntu/bionic64"
    etcd.vm.network "private_network", ip: "192.168.2.5", netmask: "255.255.255.0"
    
    etcd.vm.provision "ansible" do |ansible|
      ansible.playbook = "etcd.yml"
    end
  end

  config.vm.define "vault0" do |vault0|
    vault0.vm.box = "ubuntu/bionic64"
    vault0.vm.network "forwarded_port", guest: 8200, host: 8200
    vault0.vm.network "private_network", ip: "192.168.2.10", netmask: "255.255.255.0"

    vault0.vm.provision "ansible" do |ansible|
      ansible.playbook = "vault.yml"
    end
  end

  config.vm.define "vault1" do |vault1|
    vault1.vm.box = "ubuntu/bionic64"
    vault1.vm.network "forwarded_port", guest: 8200, host: 8201
    vault1.vm.network "private_network", ip: "192.168.2.11", network: "255.255.255.0"

    vault1.vm.provision "ansible" do |ansible|
      ansible.playbook = "vault.yml"
    end
  end
end

