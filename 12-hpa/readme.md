kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

kubectl edit deploy metrics-server -n kube-system
### add the flag
--kubelet-insecure-tls



kubectl create deploy nginx --image nginx --port 80 -o yaml --dry-run=client > nginx-deploy.yaml

kubectl autoscale deploy nginx --min 3 --max 10 --cpu-percent=80 -o yaml --dry-run=client > hpa.yaml



autoscaling/v1 - CPU based only
autoscaling/v2Beta1 - CPU and Memory based autoscaling
autoscaling/v2Beta2 - CPU, Memory and custom metric based autoscaling