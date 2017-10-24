# Kubernetes testbed

This repo has been created as a simple vagrant based testbed to aid familiarizing yourself with Kubernetes

It uses `kubeadm` to deploy a cluster, the `Vagrantfile` has a configurable number of managers and workers, but there's no multi-master setup so masters should be 1.

If you change number of workers you will need to `vagrant destroy`


## Prerequisites

- Vagrant >=1.8.6
- Ansible >=2.0
- Virtualbox >=5.0 or libvirt (for libvirt you need `VAGRANT_DEFAULT_PROVIDER=libvirt` in your env)

## Usage

Just do `vagrant up`

You will end up with 1 manager and 1 worker:

| Vagrant Machine Name | K8s Role |
| ----- | ---- |
| m01 | Master node |
| w01 | Worker node |
| w02 | Worker node |


After `vagrant up` is done, you should be able to `vagrant ssh <machinename>` and issue `kubectl get node` (as root) to see the swarm nodes.

```
12:47 $ vagrant ssh m01
Last login: Tue Oct 24 11:47:36 2017 from 192.168.121.1
[vagrant@m01 ~]$ sudo su -
[root@m01 ~]# kubectl get node
NAME           STATUS    ROLES     AGE       VERSION
m01.kube.com   Ready     master    37m       v1.8.1
w01.kube.com   Ready     <none>    36m       v1.8.1
w02.kube.com   Ready     <none>    36m       v1.8.1
[root@m01 ~]# 
```


