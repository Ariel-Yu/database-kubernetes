# Deployments

## Actions
- Deploy
- Update
    - Recreate
    - Rolling update  
- Rollback
- Pause
- Resume

## Deployment strategies for update
- Recreate
    - `kubectl describe deployments >> StrategyType: Recreate`

- Rolling update
    - `kubectl describe deployments >> StrategyType: RollingUpdate`
    - Create revisions ex: `kubectl describe deployments >> Annotations: deployment.kubernetes.io/revision: 1`
    - A new replicaset will be created during the application upgrade `kubectl get replicasets`
    
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
kubectl create -f deployment-definition.yml [--record]

kubectl get deployments
kubectl describe deployments [<deployment_name>]
kubectl get all
kubectl get replicasets
kubectl get pods
```

## Update

```
kubectl apply -f <edited_definition_file>
kubectl set image deployment/<deployment_name> <containers_name>: <image_name>

kubectl rollout status deployment/<deployment_name>
kubectl rollout history deployment/<deployment_name>
```

## Rollback

```
kubectl rollout undo deployment/<deployment_name>
```
