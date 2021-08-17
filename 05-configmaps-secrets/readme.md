kubectl create deploy busybox --image busybox:1.28 -o yaml --dry-run=client > env-example.yaml

kubectl exec -it busybox-86d4844444-5qxds -- env

kubectl create cm db-creds --from-literal=host=postres.com --from-literal=pass=abc1234 -o yaml --dry-run=client > dbcred-cm.yaml


kubectl explain pod.spec.containers.env.valueFrom.configMapKeyRef


kubectl create secret generic db-creds-secret --from-literal=host=postres.com --from-literal=pass=abc1234 -o yaml --dry-run=client > dbcred-secret.yaml


### convert base64
echo "root" | base64


sudo apt-get install jq

 kubectl get secret default-token-lhn7w  -o json | jq -r .data.token | base64 -D


 https://kubernetes.io/docs/concepts/configuration/secret/