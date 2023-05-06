# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

IMAGE_DEBIAN_11 = "generic/debian11"
VM_IP = "10.0.0.65"
VM_NAME = "debian11"

Vagrant.configure("2") do |config|
  config.vm.define VM_NAME do |machine|
    machine.ssh.insert_key = false
    machine.vm.box = IMAGE_DEBIAN_11
    config.vm.box_version = "4.2.16"
    machine.vm.hostname = VM_NAME
    machine.vm.synced_folder '.', '/vagrant', type: 'rsync', disabled: true
    machine.vm.synced_folder '.', '/vagrant', disabled: true

    machine.vm.network :private_network, :ip => VM_IP,
                       :libvirt__forward_mode => "route",
                       :libvirt__dhcp_enabled => false

    machine.vm.provider "libvirt" do |lv|
      lv.memory = 1024
      lv.cpus = 2
    end

    # machine.vm.provision :ansible do |ansible|
    #   ansible.limit = "all"
    #   ansible.host_key_checking = false
    #   # ansible.verbose = "-vvv"
    #   ansible.extra_vars = {
    #     ansible_ssh_private_key_file: './ansible/insecure_private_key'
    #   }
    #   ansible.playbook = "./ansible/site.yaml"
    #   ansible.host_vars = {
    #     "jenkins-master" => {"ansible_ssh_host" => VM_IP}
    #   }
    # end
  end
end