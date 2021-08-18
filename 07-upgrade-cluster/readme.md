## master

kubectl drain master --ignore-daemonsets
apt-mark unhold kubeadm kubelet kubectl

apt-get install kubeadm=1.21.0-00 kubelet=1.21.0-00 kubectl=1.21.0-00 -y

kubeadm upgrade plan

kubeadm upgrade apply v1.21.0

kubectl uncordon master

## Worker

### run it in master using kubectl
kubectl drain worker-1 --ignore-daemonsets

### run in worker
apt-mark unhold kubeadm

apt-get install kubeadm=1.21.0-00

kubeadm upgrade node

apt-mark unhold kubelet
apt-get install kubelet=1.21.0-00

### run it in master using kubectl
kubectl uncordon worker-1



## Backup ETCD

cat /etc/kubernetes/manifests/etcd.yaml

kubectl get pods -n kube-system

kubectl exec -it -n kube-system <etcd-pod-name> -- /bin/sh



ETCDCTL_API=3 etcdctl --endpoints 10.135.62.106:2379 \
  --cert=/etc/kubernetes/pki/etcd/server.crt \
  --key=/etc/kubernetes/pki/etcd/server.key \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \
snapshot save backup
