# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  config.vm.boot_mode = :gui

  # Define one puppetmaster
  config.vm.define :puppetmaster do |config|
    config.vm.box       = "puppetmaster"
    config.vm.host_name = "puppetmaster.cloud.gwdg.de"
    config.vm.customize ["modifyvm", :id, "--memory", 768]
#    config.hosts.aliases = %w(puppetmaster.example.com)

    # Make puppetmaster use the swift modules as default
    config.vm.share_folder "swift", "/etc/puppet/modules", "../swift"

    config.vm.network :hostonly, "10.1.255.2",  :netmask => "255.255.0.0"
#    config.vm.forward_port 80,   8080
#    config.vm.forward_port 443,  8443
  end
 
  # Define one swift-proxy node
  config.vm.define :proxy1 do |config|
    config.vm.box       = "ubuntu-12.04.2"
    config.vm.host_name = "swift-proxy-1.cloud.gwdg.de"
    config.vm.customize ["modifyvm", :id, "--memory", 512] 
    config.vm.network :hostonly, "10.1.255.3",  :netmask => "255.255.0.0"
  end

  # Define 1. swift-storage node
  config.vm.define :storage1 do |config|
    config.vm.box       = "ubuntu-12.04.2"
    config.vm.host_name = "swift-storage-1.cloud.gwdg.de"
    config.vm.customize ["modifyvm", :id, "--memory", 512] 
    config.vm.network :hostonly, "10.1.255.11",  :netmask => "255.255.0.0"
  end

  # Define 2. swift-storage node
  config.vm.define :storage2 do |config|
    config.vm.box       = "ubuntu-12.04.2"
    config.vm.host_name = "swift-storage-2.cloud.gwdg.de"
    config.vm.customize ["modifyvm", :id, "--memory", 512] 
    config.vm.network :hostonly, "10.1.255.12",  :netmask => "255.255.0.0"
  end

  # --- defaut vagrant stuff ---

  # Share an additional folder to the guest VM. The first argument is
  # an identifier, the second is the path on the guest to mount the
  # folder, and the third is the path on the host to the actual folder.
  # config.vm.share_folder "v-data", "/vagrant_data", "../data"

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  # You will need to create the manifests directory and a manifest in
  # the file puppet-devel-ubuntu-12.10.pp in the manifests_path directory.
  #
  # An example Puppet manifest to provision the message of the day:
  #
  # # group { "puppet":
  # #   ensure => "present",
  # # }
  # #
  # # File { owner => 0, group => 0, mode => 0644 }
  # #
  # # file { '/etc/motd':
  # #   content => "Welcome to your Vagrant-built virtual machine!
  # #               Managed by Puppet.\n"
  # # }
  #
  # config.vm.provision :puppet do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "puppet-devel-ubuntu-12.10.pp"
  # end

end
