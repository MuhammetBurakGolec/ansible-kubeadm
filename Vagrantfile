  Vagrant.configure("2") do |config|

    # Master VM
    config.vm.define "k8s-master" do |master|
      master.vm.box = "bento/ubuntu-22.04-arm64"
      master.vm.network "private_network", ip: "10.50.0.10"
      master.ssh.username = "vagrant-master"
      master.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/id_rsa"
      master.vm.hostname = "k8s-master"
      master.vm.provider "vmware_desktop" do |fusion|
        fusion.memory = 2048
        fusion.gui = true
        fusion.cpus = 2
      end
      master.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbooks/master-dependencies.yaml"
        ansible.inventory_path = "inventory/hosts.ini"
        ansible.limit = "all"
        ansible.extra_vars = {
          ansible_ssh_private_key_file: "~/.ssh/id_rsa"
        }
      end
    end
  
    # Node 1 VM
    config.vm.define "node-1" do |node1|
      node1.vm.box = "bento/ubuntu-22.04-arm64"
      node1.vm.network "private_network", ip: "10.50.0.11"
      node1.vm.hostname = "node-1"
      node1.ssh.username = "vagrant-node-1"
      node1.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/id_rsa"
      node1.vm.provision "shell", inline: <<-SHELL
        echo "node-1" > /etc/hostname
      SHELL
      node1.vm.provider "vmware_desktop" do |fusion|
        fusion.memory = 1024 
        fusion.gui = true
        fusion.cpus = 1
      end
      node1.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbooks/worker-dependencies.yaml"
        ansible.inventory_path = "inventory/hosts.ini"
        ansible.limit = "all"
        ansible.extra_vars = {
          ansible_ssh_private_key_file: "~/.ssh/id_rsa"
        }
      end
    end
  
    # Node 2 VM
    config.vm.define "node-2" do |node2|
      node2.vm.box = "bento/ubuntu-22.04-arm64"
      node2.vm.network "private_network", ip: "10.50.0.12"
      node2.vm.hostname = "node-2"
      node2.ssh.username = "vagrant-node-2"
      node2.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/id_rsa"
      node2.vm.provision "shell", inline: <<-SHELL
        echo "node-2" > /etc/hostname
      SHELL
      node2.vm.provider "vmware_desktop" do |fusion|
        fusion.memory = 1024 
        fusion.gui = true
        fusion.cpus = 1
      end
      node2.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbooks/worker-dependencies.yaml"
        ansible.inventory_path = "inventory/hosts.ini"
        ansible.limit = "all"
        ansible.extra_vars = {
          ansible_ssh_private_key_file: "~/.ssh/id_rsa"
        }
      end
    end

    
  
  end
  