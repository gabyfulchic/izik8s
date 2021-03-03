# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 2.2.13"

ip_prefix = '10.33.0.'
nodes = [
  { :hostname => 'haproxy-lb-01', :ip_suffix => '101', :memory => '1024', :cpu => '1', :disk => '10' },
  { :hostname => 'k8s-master-01', :ip_suffix => '102', :memory => '3060', :cpu => '3', :disk => '10' },
  { :hostname => 'k8s-master-02', :ip_suffix => '103', :memory => '3060', :cpu => '3', :disk => '10' },
  { :hostname => 'k8s-node-01', :ip_suffix => '104', :memory => '3060', :cpu => '3', :disk => '10' }
]

Vagrant.configure("2") do |config| 
  ## SSH
  # config.ssh.forward_agent = true
  # config.ssh.config = "ssh_config"
  config.ssh.insert_key = false

  ## DEPS
  config.vagrant.plugins = {"vagrant-disksize" => {"version" => "0.1.3"}}
  config.trigger.before :up do |trigger|
    trigger.name = "Checking if Ansible is well installed !"
    trigger.info = "pip install ansible==2.10.3"
    trigger.run = {inline: "bash -c 'pip install ansible==2.10.3'"}
  end

  ## DEFINE VMS
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.provider "virtualbox" do |v|
        v.cpus = node[:cpu]
        v.memory = node[:memory]
        v.check_guest_additions = true
      end
      nodeconfig.vm.box = "debian/buster64"
      nodeconfig.vm.box_version = "10.4.0"
      nodeconfig.vm.hostname = node[:hostname]
      nodeconfig.vm.network :private_network, ip: ip_prefix + node[:ip_suffix]
      nodeconfig.disksize.size = node[:disk] + 'GB'

  ## PROVISION VMS
      if node[:hostname].include? "haproxy"
        nodeconfig.vm.provision :ansible do |ansible|
          ansible.version = "2.10.3"
          ansible.playbook = "ansible/deploy-haproxy-lb.yaml"
          ansible.host_key_checking = "no"
        end
      end
      if node[:hostname].include? "master"
        nodeconfig.vm.provision :ansible do |ansible|
          ansible.version = "2.10.3"
          ansible.playbook = "ansible/master-provisioning.yaml"
          ansible.host_key_checking = "no"
        end
      end
      if node[:hostname].include? "node"
        nodeconfig.vm.provision :ansible do |ansible|
          ansible.version = "2.10.3"
          ansible.playbook = "ansible/node-provisioning.yaml"
          ansible.host_key_checking = "no"
        end
      end
    end
  end
end

# github.com/gabyfulchic/izik8s/Vagrantfile
# Author : @gabyfulchic
