# Ansible

Ansible scripts that I use for various infrastructure setups.

## OSE

This playbook can be used to deploy an OSE infrastructre. This can be used to deploy a broker and a node or many nodes with different districts.

Although very flexible, this playbook makes the following asumptions.

* ssh-key access to all the nodes (with root or a user with sudo privlages)
  * Although it's *possible*  to pass `--ask-pass` and `--ask-sudo-pass` to the `ansible-playbook` command; it's recommended to setup ssh-keys and paswordless sudo
* You are running RHEL 6.x (current version doesn't support any EL variants)
* Hostnames are set

## Lamp

This is a playbook that installs a webserver and a db server in a basic "lamp" stack. This is mostly for example and isn't really ready for any sort of production workflow.
