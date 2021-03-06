## Installation Steps

Install ContainerD/Docker
Install Kubeadm, Kubectl
Open Ports
Initialize Kubernetes master with Kubeadm
Initialize Kubernetes nodes with Kubeadm
Install CNI





sh prerequisites.sh 1.20.0-00

## Ports

### Master

6443 - api server
2379-2380 - etcd
10250 - kubelet
10255 - kubelet read only
10251 - scheduler 
10252 - controller-manager
8472 UDP  - kube proxy

30000-32767  - node ports


### Worker

10250 - kubelet
10255 - kubelet readonly
8472 UDP -  kube proxy
30000-32767 - nodeports


## Install Kubernetes

### Single Master Cluster
kubeadm init --pod-network-cidr=10.244.0.0/16

### HA Cluster
kubeadm init --pod-network-cidr=10.244.0.0/16 --upload-certs

## Join

Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 10.135.62.106:6443 --token jgbo3e.x528xorothrwqese \
    --discovery-token-ca-cert-hash sha256:bc3330fe39b1898a8ba743bfbb40f1cf02d3ad52fd944965c0186cc07eaf5a7d 

Then you can join any number of master nodes by running the following on each as root:

kubeadm join 10.135.62.106:6443 --token jgbo3e.x528xorothrwqese \
    --discovery-token-ca-cert-hash sha256:bc3330fe39b1898a8ba743bfbb40f1cf02d3ad52fd944965c0186cc07eaf5a7d 


## CNI

### Introduction

https://www.slideshare.net/JurajHantak/4-cncf-kubernetes-comparison-ofexistingcnipluginsforkubernetes?from_action=save

Calico
Cillium
Kube Router
Canal
Weavenet

### Install 
https://docs.projectcalico.org/getting-started/kubernetes/quickstart

kubectl create -f https://docs.projectcalico.org/manifests/tigera-operator.yaml
#### Download the config and change CIDR 

wget https://docs.projectcalico.org/manifests/custom-resources.yaml

kubectl apply -f calico-resources.yaml



#### Make sure quay.io images are loaded

kubectl get pods -n calico-system -o yaml | grep image:

Kubectl delete pod <name> -n calico-system --force --grace-period=0

## Static Resources

/etc/kubernetes/manifests


## Kubelet

systemctl restart kubelet

cd /var/lib/kubelet/

vi /var/lib/kubelet/config.yaml

journalctl -u kubelet --since 'one minute ago'

## Access Kubectl

KUBECONFIG=/etc/kubernetes/admin.conf kubectl get pods