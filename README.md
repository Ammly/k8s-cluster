# Kubernetes Cluster Setup

Kubernetes cluster using Ansible and Vagrant

## Requirements

You'll need the following installed on your workstation

1. [Ansible](https://www.ansible.com/)
2. [Vagrant](https://www.vagrantup.com/)
3. [Virtualbox](https://www.virtualbox.org/)
4. [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Usage

1. `git clone https://github.com/Ammly/k8s-cluster.git`
2. `cd k8s-cluster`
3. `vagrant up`

This will set up the following

- A master node called `k8s-master`
- 2 worker nodes `k8s-worker-1` and `k8s-worker-2`

## Accessing master

    vagrant ssh k8s-master

## Accessing nodes

     vagrant ssh k8s-worker-1
     vagrant ssh k8s-worker-2

To access your cluster from your host, run the following command to copy kube config from `k8s-master` to your home dir

    scp vagrant@k8s-master.test:/etc/kubernetes/admin.conf ~/.kube/config

Alternatively you can install [`vagrant scp`](https://github.com/invernizzi/vagrant-scp) plugin and run the following

    vagrant scp k8s-master:/etc/kubernetes/admin.conf ~/.kube/config

Create `.kube/` directory if it doesn't exist

### Get cluster info

    kubectl cluster-info

### Get nodes in your cluster

    kubectl get nodes

### Tested on

    Ubuntu 20.04 LTS

## More information

Get more information on the setup here: [https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant](https://kubernetes.io/blog/2019/03/15/kubernetes-setup-using-ansible-and-vagrant/)
