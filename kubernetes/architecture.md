# Kubernetes, 
a Container Orchestration Technology

- [Architecture](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#architecture)
- [Agents](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#agents)
- [Master node vs Worker node](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#master-node-vs-worker-node)
- [Resources (Objects)](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#resources-(objects))

## Architecture
* Worker node / Minion: Worker server/machine
* Master / Master node: A node that orchestrates all the containers on the nodes within a cluster
* Cluster: A set of nodes

## Agents
* kube-apiserver: 
    * Serve as the frontend of Kubernetes
    * Users, management devices and CLI all talk to the API server
    * ***kubectl*** talks to kube-apiserver
* etcd
    * A distributed key-value store used by Kubernetes to store all the data used to manage the cluster
    * Persist cluster and only cluster states
* kube-scheduler
    * Distribute containers among all nodes
    * Distribute work among all containers on the nodes
* kube-controller
    * Brain of the orchestration
    * Notice and respond to if any API or node is down
    * Decide if a new node or container is needed
    * Types of controller
        * Node controller
        * Replication controller / Replicaset
* kubelet
    * The agent that is run on every node in the cluster
    * Ensure that the properties (kube-scheduler, kube-controllers, container, ect) have necessary resources and are run successfully on each node
    * kubelets on master nodes and worker nodes have different configuration default by Kubernetes
* kube-proxy
    * Create and manage networking rules
* Container runtime
    * Underlying software used to run containers ex: Docker

## Master node vs. Worker node
### Master node
* kube-apiserver - what makes the server a master node
* etcd
* kube-scheduler
* kube-controller
* kubelet
* kube-proxy
### Worker node
* kubelet: 
    * Talk to kube-apiserver on the master node
    * Provide health information of the worker nodes
    * Carry out actions that are instructed by the master node
* kube-proxy
* Container runtime

## Resources (Objects)
* Pod
* Namespace
* Replicaset
* Deployment
* Statefulset
* Job
* CronJob
