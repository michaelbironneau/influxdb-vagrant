#!/usr/bin/env ruby

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network "forwarded_port", :guest => 8083, :host => 8083
  config.vm.network "forwarded_port", :guest => 8086, :host => 8086
  config.vm.network "forwarded_port", :guest => 8090, :host => 8090
  config.vm.network "forwarded_port", :guest => 8099, :host => 8099

  config.ssh.forward_agent = true

cmd = "apt-get update -qq;
          wget https://s3.amazonaws.com/influxdb/influxdb_0.10.2-1_amd64.deb;
          dpkg -i influxdb_0.10.2-1_amd64.deb;
          sudo service influxdb start;"

  config.vm.provision :shell, :inline => cmd
end
