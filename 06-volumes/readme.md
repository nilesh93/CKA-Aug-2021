kubectl create deploy busybox --image busybox:1.27 -o yaml --dry-run=client > emptydir.yaml

kubectl create deploy busybox --image busybox:1.27 -o yaml --dry-run=client > hostpath.yaml

 kubectl explain pod.spec.volumes

 kubectl create deploy busybox --image busybox:1.27 -o yaml --dry-run=client > cm-secret-mount.yaml

## list storage class
kubectl get sc


 kubectl create deploy busybox --image busybox:1.27 -o yaml --dry-run=client > pvc-mount.yaml

 https://kubernetes.io/docs/concepts/storage/persistent-volumes/