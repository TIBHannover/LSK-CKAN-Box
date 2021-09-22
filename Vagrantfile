# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "ckanbox" do |ckanbox|
      ckanbox.vm.box = "debian/buster64"
      ckanbox.ssh.insert_key = false
      ckanbox.vm.hostname = "ckanbox.box"
      ckanbox.vm.synced_folder ".", "/vagrant", create: true, disabled: false
      ckanbox.vm.network :private_network, ip: "192.168.100.101"
  
      ckanbox.vm.provider :virtualbox do |vb|
        vb.name = "ckanbox_box"
        vb.memory = 4096
        vb.cpus = 2
      end
    end
    config.vm.provision "ansible_local"  do |ansible|
      ansible.install = true
      ansible.version = "latest"
      ansible.compatibility_mode = "2.0"
      ansible.install_mode = "pip_args_only"
      ansible.pip_install_cmd = "sudo apt install -y python3-distutils && curl https://bootstrap.pypa.io/get-pip.py | sudo python3"
      ansible.pip_args = "ansible==2.10.7"
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "host_vagrant.yml"
      ansible.galaxy_role_file = "ansible/requirements.yml"
      ansible.verbose = true
      ansible.config_file = "ansible/ansible.cfg"
      ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
      # ansible.start_at_task = "add custome name to redis service in docker-compose.yml"
      # ansible.tags = "ckan"  # limit playbook execution to tag
    end
  end