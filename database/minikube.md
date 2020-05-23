# Minikube,
runs a single-node Kubernetes cluster inside a Virtual Machine (VM) locally

* [Check virtualization is supported on Mac OS]()
* [Install kubectl]()
* [Install Minikube]()
* [Start Minikube]()
* [Stop Minikube]()
* [Delete Minikube cluster]()

## Check virtualization is supported on Mac OS
```
sysctl -a | grep -E --color 'machdep.cpu.features|VMX'
```

## Install kubectl
#### 1. Download the executable
##### curl
```
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
```
##### Make kubectl binary executable
```
chmod +x ./kubectl
```
##### Or brew
```
brew install kubectl
```

#### 2. Move the executable to your path
```
sudo mv ./kubectl /usr/local/bin/kubectl
```

#### 3. Check kubectl version
```
kubectl version --client
```

## Install Minikube
#### 1. Download the executable
```
brew install minikube
brew reinstall minikube
```

#### 2. Move the executable to your path:
```
sudo mv minikube /usr/local/bin
```

## Start Minikube
```
minikube start
```

#### Create a deployment
```
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10
```
> deployment.apps/hello-minikube created

#### Get nodes
```
kubectl get nodes
```
NAME | STATUS | ROLES | AGE | VERSION
---- | ------ | ----- | --- | -------
minikube | Ready | master | 5m41s | v1.18.2

#### Get pods
```
kubectl get pods
```
NAME | READY | STATUS | RESTARTS | AGE
---- | ------ | ----- | -------- | ---
hello-minikube-64b64df8c9-hxwj7 | 1/1 | Running | 0 | 4m18s

#### Expose a deployment as a service
```
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```
> service/hello-minikube exposed

#### Get services
```
kubectl get services
```
NAME | TYPE | CLUSTER-IP | EXTERNAL-IP | PORT(S) | AGE
---- | ---- | ---------- | ----------- | ------- | ---
hello-minikube | NodePort | xx.xxx.xxx.x | <none> | 8080:30507/TCP | 17m
kubernetes | ClusterIP | xx.xxx.xxx.x | <none> | 443/TCP | 28m

#### Get the url of the service
```
minikube service hello-minikube --url
```

#### See the service details
`http://127.0.0.1:xxxxx `

#### Delete a service
```
kubectl delete service hello-minikube
```
> service "hello-minikube" deleted

#### Delete a deployment
```
kubectl delete deployment hello-minikube
```
> deployment.apps "hello-minikube" deleted

## Stop Minikube

## Delete Minikube cluster

## References
[https://kubernetes.io/docs/setup/learning-environment/minikube/](https://kubernetes.io/docs/setup/learning-environment/minikube/) 
