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
