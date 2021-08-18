kubectl delete all --all 

kubectl create deploy nginx --image nginx -o yaml --port=80 --dry-run=client > nginx-deploy.yaml

kubectl expose deploy/nginx --port 80 --target-port 80 -o yaml --dry-run=client > nginx-svc.yaml

kubectl run busybox --image busybox:1.27 -it --rm -- /bin/sh