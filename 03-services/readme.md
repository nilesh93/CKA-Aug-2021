kubectl create deployment nginx --image quay.io/bitnami/nginx --port 80 -o yaml --dry-run=client > deploy.yaml


kubectl expose deploy/nginx --port 8080 --target-port=80 --type=ClusterIP -o yaml --dry-run=client > service.yaml

kubectl run -it --rm busybox --image busybox:1.28 -- /bin/sh


If we are on the same namespace: service name is the dns name
Correct DNS name for any given service is,
<service-name>.<namespace-name>.svc.cluster.local


kubectl run -it --rm busybox --image busybox:1.28 -- nslookup nginx > lookup.txt

kubectl expose deploy/nginx --port 8080 --target-port=80 --type=NodePort -o yaml --dry-run=client > service.yaml
kubectl expose deploy/nginx --port 8080 --target-port=80 --type=LoadBalancer -o yaml --dry-run=client > service.yaml



Fully Qualified name for pods

<pod-ip-with-dashes-instead-of-dots>.<namespace>.pod.cluster.local


### Activity 

kubectl create ns training
kubectl create deploy nginx --image quay.io/bitnami/nginx:v1 --port 8080 -n training --replicas=3
kubectl expose deploy/nginx --port 80 --target-port 8080

kubectl run busybox --image busybox:1.28 -it -- /bin/sh

wget -O- <url>