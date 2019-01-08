# Description

A set of Ansible roles to configure various features on Ubiquity EdgeRouter X series devices.

## Features

Below are the features that this playbook is capable of configuring on the EdgeRouter. 

### AD Block

### Dynamic DNS

This Role will configure all of the settings need for Dynamic DNS on your EdgeRouter. The easiest way to get this working is to setup an account with [DNS-O-Matic](https://www.dnsomatic.com), and update your hostname provider that way.

### IPSec Server

This Role will configure and L2TP over IPSec VPN tunnel, as well as the firewall rules need so you can use to remote back into your home network. 

### Let's Encrypt

This Role will configure Let's Encrypt SSL on your device as well as block traffic to the Web UI of the router from outside of the network. 

### WireGuard

This Role can be used to accomplish multiple items depending on your use case. In this case it is being used to create secured tunnels with and AWS instance. 

## Running the playbook
Committing configurations can take extra time on certain edgerouter models so ANSIBLE_PERSISTENT_COMMAND_TIMEOUT needs to be set to 30 seconds to not timeout while configuring the aws tunnels. I'm using ansible-vault to encrypt hosts.yml, so I keep the decrypt password in a file at ~/.vault_pw and run ansible-playbook with --vault-password-file.

```
ANSIBLE_PERSISTENT_COMMAND_TIMEOUT=30 ansible-playbook playbook.yml -i hosts.yml --vault-password-file ~/.vault_pw
```