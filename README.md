## CKAN Vagrant Box

**Installs CKAN Vagrant Box in a standalone Vagrant box ([debian/buster64](https://app.vagrantup.com/debian/boxes/buster64)), though the use of Ansible (2.10) playbook**


Requirements to run box:
* [Git](https://git-scm.com/downloads)
* [Vagrant](https://www.vagrantup.com/downloads.html)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

Installed CKAN extensions:
* Datastore
* Datapusher
* Dcat
* Harvest

## Run

Run the following steps in Terminal (Linux/macOS) or Git Bash (Windows):
```bash
cd ckanbox
vagrant up
```

After installation process has finished, CKAN Vagrant Box will be running at 
<http://192.168.100.101> and **CKAN will be running at <http://192.168.100.101/box/ckan>** with default **admin user** `admin` and **password** `adminpwd`

In [host_vagrant.yml](./host_vagrant.yml) the following variables are defined and can be changed:
* `ckan_url_path: '/box/ckan'`
* `ckan_admin_user: 'admin'`
* `ckan_admin_user_password: 'adminpwd'`
* `ckan_admin_user_email: 'admin@mail.com'`
* `vm_url: 'http://192.168.100.101'`

## Other Vagrant commands


`vagrant up` creates a new Vagrant box and runs the Ansible  playbook

`vagrant reload --provision` restarting the Vagrant box and re-runs the Ansible playbook 

`vagrant provision` re-runs the Ansible playbook without restarting VM

`vagrant ssh` allows to sshing into the Vagrant box

`vagrant halt`  shuts down the vagrant

`vagrant suspend` saves the state of the Vagrant box and suspends it

`vagrant resume` resumes the Vagrant box from its saved state


## Box source structure & files
* *Vagrant box configuration file*: [Vagrantfile](./Vagrantfile)  
* *Ansible invetory file* for the Vagrant box: [host_vagrant.yml](./host_vagrant.yml)
* *Ansible configuration* file: [ansible.cfg](./ansible.cfg)
* *Ansible entry playbook*: [ansible/playbook.yml](./ansible/playbook.yml)
* *Ansible roles* directory: [ansible/roles](./ansible/roles)
    * *Ansible 00_utils role main task*: [ansible/roles/01_utils/tasks/main.yml](./ansible/roles/01_utils/tasks/main.yml)
* *Ansible roles/collections requirements*: [ansible/requirements.yml](./ansible/requirements.yml)

# TODO
* enable and datapusher and harvester
* enable DCAT