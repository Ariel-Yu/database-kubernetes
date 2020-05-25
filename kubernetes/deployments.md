# Deployments

## Actions
- Deploy
- Upgrade
- Rolling update
- Rollback
- Pause
- Resume

## Deployments yml

deployment-definition.yml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ariel-deployment
  labels:
    name: deployment

spec:
  template:

    metadata:
      labels:
        tier: front-end
    spec:
      containers:
        - name: nginx
          image: nginx

  replicas: 3
  selector:
    matchLabels:
      tier: front-end
```

Create a deployment with a replicaset with 3 pods with a yaml file
```
kubectl create -f deployment-definition.yml

kubectl get deployments
kubectl describe deployments [<deployment_name>]
kubectl get all
kubectl get replicasets
kubectl get pods
```
