# Build a Kubernetes cluster using k3s via Ansible



## K3s Ansible Playbook

Build a Kubernetes cluster using Ansible with k3s. The goal is easily install a Kubernetes cluster on machines running:

- [X] Debian
- [X] Ubuntu
- [X] CentOS

on processor architecture:

- [X] x64
- [X] arm64
- [X] armhf

## System requirements

Deployment environment must have Ansible 2.4.0+
Master and nodes must have passwordless SSH access

## Usage

Add the system information gathered above into a file called `hosts.ini` in the same directory as this README file. There is a template in the `inventory` directory. You may have a different network setup. For example:

```bash
[master]
172.16.20.9 

[node]
172.16.20.[10:13]

[k3s_cluster:children]
master
node
```

Start provisioning of the cluster using the following command:

```bash
ansible-playbook site.yml
```

## Kubeconfig

To get access to your **Kubernetes** cluster just

```bash
scp debian@master_ip:~/.kube/config ~/.kube/config
```
