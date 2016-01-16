# Ansible setup for openHAB

Ansible playbooks for setting up OpenHAB and its dependencies on Debian/Raspbian Jessie.

## Playbooks

- `infrastructure.yml` - Basic server setup, install necessary packages and Oracle Java
- `openhab.yml` - Install OpenHAB. This playbook is very much tailored to my home setup and not very modular!
- `homegear.yml` - Install [homegear](https://www.homegear.eu/) service, needed for integrating HomeMatic/ELV MAX devices. This is still experimental!

## Inventories

You must create your own inventory file. This file has to have at least the `raspberry` group.

For testing the playbooks with a Vagrant virtual machine you can also add a `vagrant` group.


Example inventory file:

```
[vagrant]
192.168.1.2 ansible_ssh_user=vagrant 

[vagrant:vars]
homegear_repo = "deb https://homegear.eu/packages/Debian/ jessie/"

[raspberry]
192.168.1.3 ansible_ssh_user=pi

[raspberry:vars]
homegear_repo = "deb https://homegear.eu/packages/Raspbian/ jessie/"
```
