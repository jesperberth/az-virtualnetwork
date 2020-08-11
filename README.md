Az-virtualnetnork
=========

Creates a Virtualnetwork resource in Microsoft Azure with one subnet

Requirements
------------

Requires Azure SDK

pip install 'ansible[azure]'

Role Variables
--------------

Role takes following vars, first 4 is a requirement for the az-resourcegroup role and for this role

resourcegroup = name of the resource group to create

location = Azure location to create resourcegroup in

tag_owner = Create tag owner with value

tag_project = Create tag project with value

virtualnetwork_name = name of the Virtual Network

cidr = IP net for the Virtual Network eg. 10.0.0.0/16

subnet_name = Name of the subnet

subnet_cidr = IP net for the subnet, must be a subset of cidr eg. 10.0.0.0/24

virtualnetwork_name, cidr, subnet_name and subnet cidr is predefined in vars/main.yml and can be changed with vars in the playbook

Dependencies
------------

ansible-galaxy install jesperberth.az_resourcegroup or resource group must be created before running this role

Example Playbook
----------------

```ansible
---
- hosts: localhost
  name: Create Virtualnetwork in Azure
  vars:
    resourcegroup: resourcegroupname
    location: northeurope
    tag_owner: jesper
    tag_project: demoproject
  tasks:
    - name: Azure Resource Group
      include_role:
        name: jesperberth.az-resourcegroup

    - name: Azure Virtual Network
      include_role:
        name: jesperberth.az-virtualnetwork

```

License
-------

BSD

Author Information
------------------

Jesper Berth