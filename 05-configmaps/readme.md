kubectl create deploy busybox --image busybox:1.28 -o yaml --dry-run=client > env-example.yaml

kubectl exec -it busybox-86d4844444-5qxds -- env