# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagranyfile API/syntax version
VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 2.2.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  servers=[
      {
        :hostname => "lab01",
        :box      => "generic/ubuntu1804",
        :boxurl   => "generic/ubuntu1804",
        :ip       => "10.1.1.11"
      },
      {
        :hostname => "lab02",
        :box      => "generic/ubuntu1804",
        :boxurl   => "generic/ubuntu1804",
        :ip       => "10.1.1.12"
      },
      {
        :hostname => "lab03",
        :box      => "generic/ubuntu1804",
        :boxurl   => "generic/ubuntu1804",
        :ip       => "10.1.1.13"
      },
      {
        :hostname => "lab04",
        :box      => "generic/centos7",
        :boxurl   => "generic/centos7",
        :ip       => "10.1.1.14"
      }

    ]

  servers.each do |machine|
    config.vm.define machine[:hostname] do |node|
      node.vm.hostname = machine[:hostname]
      node.vm.box      = machine[:box]
      node.vm.box_url  = machine[:boxurl]
      node.vm.network :private_network, ip: machine[:ip]

      node.vm.provider :libvirt do |libvirt|
        libvirt.memory = 512
        libvirt.cpus = 1
      end
    end
  end

  lab_pub = File.read(File.join(Dir.home, ".ssh", "lab.pub"))

  config.vm.provision :shell,
        :inline => "echo 'appending SSH public key to ~vagrant/.ssh/authorized_keys' && echo '#{lab_pub }' >> /home/vagrant/.ssh/authorized_keys && chmod 600 /home/vagrant/.ssh/authorized_keys"

  config.ssh.insert_key = false
end
