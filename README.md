# Kubernetes testbed

This repo has been created as a simple vagrant based testbed to aid familiarizing yourself with Kubernetes

It uses `kubeadm` to deploy a cluster, the `Vagrantfile` has a configurable number of managers and workers, but there's no multi-master setup so masters should be 1.

If you change number of workers you will need to `vagrant destroy`


## Prerequisites

- Vagrant >=1.8.6
- Ansible >=2.0
- Virtualbox >=5.0 or libvirt

## Usage

Just do `vagrant up`

You will end up with 1 manager and 1 worker:

| Vagrant Machine Name | K8s Role |
| ----- | ---- |
| m01 | Master node |
| w01 | Worker node |

After `vagrant up` is done, you should be able to `vagrant ssh <machinename>` and issue `kubectl get node` (as root) to see the swarm nodes.




