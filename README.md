# Ansible

Ansible scripts that I use for various infrastructure setups.

## OSE

This playbook can be used to deploy an OSE infrastructre. This can be used to deploy a broker and a node or many nodes with different districts.

Although very flexible, this playbook makes the following asumptions.

* ssh-key access to all the nodes (with root or a user with sudo privlages)
  * It's *possible*  to pass `--ask-pass` and `--ask-sudo-pass` to the `ansible-playbook` command; it's no recommended
* You are running RHEL 6.x (current version doesn't support any EL variants)
* Hostnames are set beforehand on the servers.
* You have `git` and `ansible` installed on your system.
* The target servers have `ssh` running and open and has `python` installed
* Target Servers can reach the RHN
* You have delegated a domain or subdomain to the IP address that will be the broker

Setup:

1. Clone the repo on a system where you have installed ansible and have ssh access to the target servers.
2. All configurations are done under the `ansible/ose/group_vars/all` file.
  * The configuration file is well comented and should give you everything you need
3. Run the `ansible-playbook` command within the `ansible/ose` directory.
  * After a basic configuration; the command can be as simple as:
  ```
  ansible-playbook ose.yml -i hosts -e "uservar=ec2-user" --sudo 
  ```
  * Quick note about the `uservar` variable. This is the remote user to run the commands as. If you're using root you can omit the `--sudo` option and set `uservar=root`
4. Profit!

Note:

* If you're using OS1; you probably want to put the servernames in your `/etc/hosts` file (unless you put IP addresses in the `ansible/ose/hosts` file)
* EC2 users can pass the `--private-key` option to the playbook command to specify the key

## Lamp

This is a playbook that installs a webserver and a db server in a basic "lamp" stack. This is mostly for example and isn't really ready for any sort of production workflow.
