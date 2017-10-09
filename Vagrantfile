# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Use the same key for each machine
  config.ssh.insert_key = false

  config.vm.define 'db' do |db|

    # Every Vagrant virtual environment requires a box to build off of.
    db.vm.box = "debian/jessie64"

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    db.vm.network "public_network", ip: "192.168.1.100", bridge: "eth1"

    # If true, then any SSH connections made will enable agent forwarding.
    db.ssh.forward_agent = true

    db.vm.provider "virtualbox" do |vb|
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "1024"]
# cannot resize disk https://tuhrig.de/resizing-vagrant-box-disk-space/
#      vb.customize ["modifyhd", "disk id", "--resize", "10000"]
    end

    Vagrant.configure('2') do |config|
      config.vm.box = 'debian/jessie64'
      config.disksize.size = '10GB'
    end
  end

  config.vm.define 'web' do |web|

    # Every Vagrant virtual environment requires a box to build off of.
    web.vm.box = "debian/jessie64"

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    web.vm.network "public_network", ip: "192.168.1.101", bridge: "eth1"

    # If true, then any SSH connections made will enable agent forwarding.
    web.ssh.forward_agent = true

    web.vm.provider "virtualbox" do |vb|
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end

#    web.vm.provision "ansible" do |ansible|
#      ansible.limit = 'all'
#      ansible.playbook = "mezzanine-across-hosts.yml"
#    end

    Vagrant.configure('2') do |config|
      config.vm.box = 'debian/jessie64'
      config.disksize.size = '10GB'
    end

  end

end

