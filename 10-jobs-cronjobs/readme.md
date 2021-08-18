kubectl create job hello --image busybox -o yaml --dry-run=client > job.yaml

kubectl create cronjob hello --image busybox -o yaml --dry-run=client --schedule='* * * * *' > cronjob.yaml