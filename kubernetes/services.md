# Services

## Serivces kubectl

```
kubectl create -f <service_definition_file>
kubectl expose deployment <deployment_name> --port=<port> [--name=<service_name>] [--type=<NodePort | ClusterIP>]

<SHORTNAME of services = svc>
kubectl get services [<service_name>] 
kubectl get services [<service_name>] -o wide
kubectl describe services [<service_name>]

kubectl delete services <service_name>
```

## NodePort

- Map ports of the nodes to ports of the pods
- Make internal pods accessible through the ports of the nodes
- Ports
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

## ClusterIP

- A virtual IP created in the cluster for the communication among different microservices, ex: group of frontend microservices, group of backend microservices, ect.
- Ports
  - targetPort
  - port

Creatre a service with type ClusterIP in front of a group of pods of the same microservice with label `tier: backend`. Other applications will access this group of pods through the service
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
