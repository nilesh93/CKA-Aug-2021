kubectl create deploy busybox --image busybox:1.28 -o yaml --dry-run=client > env-example.yaml

kubectl exec -it busybox-86d4844444-5qxds -- env

kubectl create cm db-creds --from-literal=host=postres.com --from-literal=pass=abc1234 -o yaml --dry-run=client > dbcred-cm.yaml