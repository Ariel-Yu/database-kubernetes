# Services

## NodePort

- Target port: The port on the pod
- Port: The port on the service
- NodePort: The port on the node (30000 ~ 32767)

Create a service of type NodePort for directing traffic to pods with label: `tier: frontend`. The pods can be in the same node or distributed in many nodes
```
apiVersion: v1
kind: Service
metadata:
  name: my-service

spec:
  type: NodePort
  ports:
    - targetPort: 80
      port: 80
      nodePort: 30008

  selector:
    tier: frontend
```

```
kubectl create -f <service_definition_file>
kubectl get services
kubectl get services -o wide
kubectl describe services
```

## ClusterIP

Creatre a service with type ClusterIP in front of a group of pods of the same applicaion with label `tier: backend`, ex: frontend, backend, cache, etc. Other applications will access this group of pods through the service
```
apiVersion: v1
kind: Service
metadata:
  name: backend-service

spec:
  type: ClusterIP
  ports:
    - targetPort: 80
      port: 80

  selector:
    tier: backend
```

## LoadBalancer
