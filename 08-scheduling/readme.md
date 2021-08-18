kubectl taint node worker-1 app=java:NoSchedule

## make a node unschedulable
kubectl cordon node worker-1

kubectl uncordon node worker-1

## make a node into maintenance
kubectl drain node worker-1