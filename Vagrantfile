# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |cfg|
  cfg.vm.box = "debian/bookworm64"
  cfg.ssh.insert_key = false

  cfg.vm.define "server" do |server|
    server.vm.hostname = "dhcp-server"
    server.vm.network :private_network, ip: "192.168.57.10"
    server.vm.provision :ansible do |ansible|
      ansible.playbook = "dhcp-playbook.yaml"
    end
  end

  cfg.vm.define "c1" do |c1|
    c1.vm.hostname = "client1"
    c1.vm.network :private_network, ip: "192.168.57.20"
  end

  cfg.vm.define "c2" do |c2|
    c2.vm.hostname = "client2"
    c2.vm.network :private_network, ip: "192.168.57.21"
  end
end

