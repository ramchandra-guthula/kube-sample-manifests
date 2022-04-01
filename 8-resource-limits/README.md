- Try create a pod by having excess of node resources, assume node has 1Gb memory and 1v CPU. use below manifest and create a pod

```
apiVersion: v1
kind: Pod
metadata:
  name: myapp
  labels:
    name: myapp
spec:
  containers:
  - name: myapp
    image: nginx
    resources:
      requests:
        memory: "1500Mi"
        cpu: "1200m"
    ports:
      - containerPort: 80
```
- Pod will be in pending state and you will see below error 

```
Events:
  Type     Reason            Age              From               Message
  ----     ------            ----             ----               -------
  Warning  FailedScheduling  8s (x2 over 9s)  default-scheduler  0/2 nodes are available: 1 Too many pods, 2 Insufficient cpu, 2 Insufficient memory.
```

- Apply resource limits to a  specfic namespace to understand how limits work 
```
kubectl create namespace product-app

kubectl apply -f limit.yml -n product-app

```

- Try create a pod exceeding or below the limit range and observe the error logs, you may see the below logs

```
[ec2-user@ip-172-31-36-232 ~]$ kubectl apply -f nginx.yaml
Error from server (Forbidden): error when creating "nginx.yaml": pods "myapp" is forbidden: minimum memory usage per Container is 128Mi, but request is 64Mi

```