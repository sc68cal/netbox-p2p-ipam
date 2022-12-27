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
    inline: "sudo apt-get install -y docker.io"
  config.vm.provision "shell",
    inline: 'bash -c "$(curl -sL https://get.containerlab.dev)"'
end