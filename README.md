# Ansible setup for openHAB

Ansible playbooks for setting up OpenHAB and its dependencies on Debian/Raspbian Jessie.

## Playbooks

- `infrastructure.yml` - Basic server setup, install "necessary" packages and Oracle Java
- `openhab.yml` - Install OpenHAB
- `homegear.yml` - Install [homegear](https://www.homegear.eu/) service, needed for integrating HomeMatic/ELV MAX devices. 

## Inventoriy variables

Until `homegear.yml` can detect the OS version, your inventory must define the `homegear_repo` variable for the appropriate repository.

Example:

```
[vagrant]
192.168.1.2 ansible_ssh_user=vagrant 

[vagrant:vars]
homegear_repo = "deb https://homegear.eu/packages/Debian/ jessie/"

[raspi]
192.168.1.2 ansible_ssh_user=pi

[raspi:vars]
homegear_repo = "deb https://homegear.eu/packages/Raspbian/ jessie/"
```

## Testing the playbook

Use the provided Vagrantfile
