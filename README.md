# towerbox
A script that creates an inventory in [Ansible AWX](https://github.com/ansible/awx) from devices in [NetBox](https://netbox.readthedocs.io/en/stable/).

NetBox is not a supported inventory source within Ansible Tower / AWX.
See the Red Hat article about it here: [Is Netbox a Supported Inventory Source Within Ansible Tower?](https://access.redhat.com/solutions/4264501)
But with this script it becomes possible!

Groups are created within the assigned inventory based upon the values for `site` and `platform` specified within Netbox.


This fork of [joubbi](https://github.com/joubbi)'s original [towerbox](https://github.com/joubbi/towerbox) script adds support for Virtual Machines and multiple groups, and avoids some possible failure states.


### Example of device variables in Tower
```
ansible_host: 192.168.0.1
netbox_device_role: firewall
netbox_platform: asa
netbox_status: active
netbox_tags:
  - tag1
  - tag2
  - tag3
```


## Instructions
1. Copy the contents of towerbox.py as a custom script under Inventory Scripts in Ansible Tower.
2. Set the environment variables `NETBOX_HOST_URL` and `NETBOX_AUTH_TOKEN`.
3. Create a new inventory that uses this new custom script.
4. Enjoy your new dynamic inventory.


This script is tested with Ansible AWX 19.5.1 and NetBox v3.2.1.

