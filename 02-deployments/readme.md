
## deploy
kubectl create deployment nginx --image quay.io/bitnami/nginx --port 80 -o yaml --dry-run=client > deploy.yaml

## pod
kubectl run nginx --image quay.io/bitnami/nginx --port 80 -o yaml --dry-run=client > pod.yaml

kubectl explain pod.spec = kubectl explain deploy.spec.template.spec

kubectl get deploy nginx -o yaml > backup.yaml

kubectl get pods -o yaml > pod-backup.yaml


kubectl get pods,deploy


kubectl get rs
 kubectl rollout history deploy/nginx

 kubectl rollout undo  deploy/nginx --to-revision=1