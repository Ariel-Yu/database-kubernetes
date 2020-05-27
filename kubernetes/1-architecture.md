# Kubernetes, 
a Container Orchestration Technology

- [Architecture](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#architecture)
- [Agents](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#agents)
- [Master node vs Worker node](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#master-node-vs-worker-node)
- [Resources (Objects)](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/architecture.md#resources-objects)

## Architecture
* Worker node / Minion: Worker server/machine
* Master / Master node: A node that orchestrates all the containers on the nodes within a cluster
* Cluster: A set of nodes
   * Resources (CPU, memory, networking, ect) are shared within a cluster from all nodes

## Agents
* kube-apiserver: 
    * Serve as the frontend of Kubernetes
    * API requests talks to kube-apiserver (external to the cluster)
    * ***kubectl*** talks to kube-apiserver (external to the cluster)
    * All the other agents talk to the kube-apiserver (internal of the cluster)
* etcd
    * A distributed key-value store used by Kubernetes to store all the data used to manage the cluster
    * Persist cluster and only cluster states
* kube-scheduler
    * Find the right node to distribute containers (pods)
    * Distribute work among all containers on the nodes
* kube-controller
    * Brain of the orchestration
    * Notice and respond to if any API or node is down
    * Decide if a new node or container is needed
    * Types of controller
        * Node controller
        * Replication controller / Replicaset
* [cloud-controller]
   * Optional agents for the cluster
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
* [Pod](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/pods.md)
* [Replicaset](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/replicasets-&-repliation-controllers.md) *
   * Ensure that the desired number of pods are running in the cluster. The pods can be deployed on the same or different nodes
* [Deployment](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/deployments.md) *
   * Create and kill pods of the same container in random sequence
* Daemonset *
   * Ensure that a container is deployed to all the nodes (one pod one node)
* Statefulset *
   * Create and kill pods of the same container in sequence
* Job *
* CronJob *
* [Service](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/services.md)
* Namespace

`* Different pod managers, managing pods with different manners`
