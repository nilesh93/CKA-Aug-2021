kubectl create sa tester

kubectl create clusterrole pod-getter --verb=get,watch,create --resource=pod,deploy -o yaml --dry-run=client > clusterrole.yaml

[--serviceaccount=namespace:serviceaccountname]

kubectl create rolebinding pod-get-binding --clusterrole=pod-getter --serviceaccount=training:tester -o yaml --dry-run=client -n training > rolebinding.yaml

kubectl auth can-i get pods --as system:serviceaccount:training:tester


kubectl create clusterrolebinding pod-get-binding --clusterrole=pod-getter --serviceaccount=training:tester