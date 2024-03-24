# Ansible NFS Server and Client Deployment
## Overview
This repository contains Ansible playbooks and roles for the deployment and configuration of an NFS (Network File System) server and client. 
It is designed to provide an example of how to configure NFS server-client architecture using Ansible automation.

## Prerequisites and Limitations
### Control Node
+ **Ansible Version**: Ensure that Ansible version 2.9 or higher is installed on the control node for proper playbook execution.
### Environment
+ **Cloud-Based Nodes**: Both NFS server and client nodes are hosted in the cloud. These nodes will be available for demonstration and testing purposes until April 07, 2024.

+ **Network Configuration**: Due to limitations set by the cloud provider, the NFS protocol can only be utilized within the cloud's private network. This is a common scenario in cloud environments to enhance security.


## Repository Structure
```
.
├── README.md
├── group_vars
├── host_vars
├── inventory
│   └── hosts
├── roles
│   ├── nfsclient
│   │   ├── README.md
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       ├── nfs-automount.j2
│   │       └── nfs-mount.j2
│   └── nfsserver
│       ├── README.md
│       ├── defaults
│       │   └── main.yml
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   └── main.yml
│       └── templates
│           └── exports.j2
├── setup-nfs.yml
└── vaulted_vars
    └── vars.yml
```
## Usage
Clone the repository to your control node:
```
git clone https://github.com/vokborok/nfssetup.git
cd nfssetup
```
Run:
```
ansible-playbook -e @vaulted_vars/vars.yml -i inventory/hosts setup-nfs.yml --ask-vault-pass
```
vault-pass will be sent separately through a secure method
