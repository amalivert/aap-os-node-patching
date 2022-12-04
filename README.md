Ansible nodes OS patching
==========================

Role to patch the underneath Operating System(OS) of Ansible Automation Platform 2.x. Supports Controller, Execution, and Private Automation Hub node.

Information
------------
Role to perform OS Patching and upgrades without breaking AAP. Works on RHEL 8 and RHEL 9 based on this access article:

https://access.redhat.com/solutions/4566711

Can also use this command to patch all AAP nodes:

```console
[admin@aap-pah-1 ~]$ sudo dnf update --exclude=ansible*,automation-*,dumb-init,helm,oniguruma,oniguruma-devel,openshift-clients,pulpcore-selinux,python39*,receptor*,sshpass,supervisor,yamllint
```
Dependency
----------- 

community.general.yum_versionlock collection

Inventory
----------

Create group in your invenotory for Controller nodes and PAH nodes

How to run playbook aginst Controller nodes
--------------------------------------------

```console
$ ansible-playbook yum_patch_aap_nodes.yml --extra-vars "aap_nodes=<controller group>" -bkK
```

How to run playbook against Private Automation Hub nodes
--------------------------------------------------------

```console
$ ansible-playbook yum_patch_pah.yml --extra-vars "pah_nodes=<pah group>" -bkK
```