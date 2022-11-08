# Vmware
# ------------------------------------------------------------

# Vagrant.configure("2") do |config|
#   # Provisiing MongoDB

  
#   # Provisioning NodeJS App
#   config.vm.define "nodeapp" do |nodeapp|
#     nodeapp.vm.box = "spox/ubuntu-arm"
#     nodeapp.vm.network "private_network", ip: "192.168.56.10"
#     nodeapp.hostsupdater.aliases = ["nology.training"]
#     nodeapp.vm.provider "vmware_fusion" do |vb|
#       nodeapp.vm.synced_folder "app/", "/home/vagrant/app/"
#       nodeapp.vm.synced_folder "env/", "/home/vagrant/env"
#     end
#     nodeapp.vm.provision "shell", inline: <<-SHELL
#       systemctl disable apt-daily.service
#       systemctl disable apt-daily.timer
#       sudo apt remove unattended-upgrades -y
#     SHELL
#     nodeapp.vm.provision "shell", path: "env/nodeapp/script.sh"
#   end
# end

# Virtual Box
# --------------------------------------------------------------

Vagrant.configure("2") do |db|
  db.vm.define "mongodb" do |mongodb|
    mongodb.vm.box = "generic/ubuntu2010"
    mongodb.vm.network "private_network", ip: "192.168.56.20"
    mongodb.vm.provider "virtualbox" do |vb|
      mongodb.vm.synced_folder "env/", "/home/vagrant/env"
    end
    mongodb.vm.provision "ansible" do |ansible|
      ansible.playbook = "env/mongodb/playbook.yml"
  end
end


Vagrant.configure("2") do |config|
  # Provisioning NodeJS App
  config.vm.define "nodeapp" do |nodeapp|
    nodeapp.vm.box = "generic/ubuntu2010"
    nodeapp.vm.network "private_network", ip: "192.168.56.10"
    nodeapp.hostsupdater.aliases = ["nology.training"]
    nodeapp.vm.define "nodeapp"
    nodeapp.vm.provider "virtualbox" do |vb|
      nodeapp.vm.synced_folder "app/", "/home/vagrant/app/"
      nodeapp.vm.synced_folder "env/", "/home/vagrant/env"
    end
    nodeapp.vm.provision "ansible" do |ansible|
      ansible.playbook = "env/nodeapp/playbook.yml"
  end
end