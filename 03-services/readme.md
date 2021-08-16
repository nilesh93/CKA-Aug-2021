kubectl create deployment nginx --image quay.io/bitnami/nginx --port 80 -o yaml --dry-run=client > deploy.yaml


kubectl expose deploy/nginx --port 8080 --target-port=80 --type=ClusterIP -o yaml --dry-run=client > service.yaml

kubectl run -it --rm busybox --image busybox:1.28 -- /bin/sh


If we are on the same namespace: service name is the dns name
Correct DNS name for any given service is,
<service-name>.<namespace-name>.svc.cluster.local


kubectl run -it --rm busybox --image busybox:1.28 -- nslookup nginx > lookup.txt

kubectl expose deploy/nginx --port 8080 --target-port=80 --type=NodePort -o yaml --dry-run=client > service.yaml
kubectl expose deploy/nginx --port 8080 --target-port=80 --type=LoadBalancer -o yaml --dry-run=client > service.yaml