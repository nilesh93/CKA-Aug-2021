kubectl run nginx --image quay.io/bitnami/nginx --port 80 
kubectl delete pods --all

kubectl run nginx --image quay.io/bitnami/nginx --port 80 -o yaml --dry-run=client > nginx-pod.yaml

kubectl explain pod.spec.containers.resources

kubectl exec -it nginx -- /bin/sh

kubectl port-forward nginx 3000:80

cd /usr/share/nginx/html/

kubectl logs ngnix