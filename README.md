Ansible Gluster
-------

This playbook will install and configure gluster on fresh ubuntu 16.04 machines reported by MAAS.
This repository is in development and probably not ready for production use.

Requirements
-------

- ansible
- MAAS

Maas needs to be up and running and you need some deployed machines.

The dynamic inventory script needs requests and oauth.
You can install those with

```
pip install requests oauth
```

If you want to use the MAAS dynamic inventory script you will also have to set the
MAAS_API_KEY and MAAS_API_URL environmental variables:

```
export MAAS_API_KEY=<my_api_key>
export MAAS_API_URL=http://<my_maas_server>/MAAS/api/1.0
```

How to use the playbook:

```
ansible-playbook --private-key <path_to_ssh_key_for_maas> -i ansible_maas_dynamic_inventory.py -u <maas_username> install_gluster.yml
```
By default this will create a distributed and replicated gluster volume test1, so you need at least 4 machines in MAAS to use this playbook.
