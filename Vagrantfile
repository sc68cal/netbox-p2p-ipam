Vagrant.configure("2") do |config|

  # This vagrant box was built for most common providers,
  # such as vmware, virtualbox, and parallels
  # https://app.vagrantup.com/bento/boxes/ubuntu-22.04/versions/202206.13.0
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.box_version = "202206.13.0"

  config.vm.provider "virtualbox" do |v|
    v.memory = 16384
    v.cpus = 12
  end


  config.vm.provision "shell",
    inline: "sudo apt-get install -y docker.io docker-compose python3.10-venv"
  config.vm.provision "shell",
    inline: 'bash -c "$(curl -sL https://get.containerlab.dev)"'
  config.vm.provision "shell",
    inline: "git clone https://github.com/netbox-community/netbox-docker.git"
  # Check out a version before the cable API broke - see
  # https://github.com/netbox-community/netbox/issues/11210
  config.vm.provision "shell",
    inline: "cd netbox-docker; git checkout 2.0.0"
  config.vm.provision "shell",
    inline: "sudo usermod -a -G docker vagrant"
  config.vm.provision "shell",
    inline: "cd netbox-docker; cp docker-compose.override.yml.example docker-compose.override.yml; docker-compose -f docker-compose.yml up -d"
  config.vm.provision "shell",
    inline: "sudo containerlab deploy -t /vagrant/containerlab.yml"
  config.vm.synced_folder ".", "/vagrant",
    mount_options: ["dmask=022,fmask=022"]

  # Forward netbox port
  Vagrant.configure("2") do |config|
    config.vm.network "forwarded_port", guest: 8000, host: 8000
  end

end
