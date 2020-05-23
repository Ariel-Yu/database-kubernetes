# Pods

## Pods concept
* Pod usually has a **1:1** relationship with container
* To scale up the application, we can add more pods with the **same** application image to the same node or add more nodes with containers with the **same** application image to the same cluster
* A pod can have multiple containers. These containers usually have **different** application images. Some of the containers are usually helper containers of another container
* What resources can be shared within a pod
  * Network namespace
  * Storage
  * Same thread

## Pods kubectl
```
kubectl run <pod_name> --image=<image_name> --restart=Never
kubectl get pods
kubectl get pods -o wide
kubectl describe pods
kubectl delete pod <pod_name>

kubectl create deployment <deployment_name> --image=<image_name> → Create a deployment
```

## Pods yml

pod-definition.yml
```
apiVersion: v1

kind: Pod

metadata:
  name: ariel-pod
  labels:
    app: ariel

spec:
  containers:
    - name: nginx-container
      image: nginx
```

Create a pod with a yaml file
```
kubectl create -f pod-definition.yml
```
