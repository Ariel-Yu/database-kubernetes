# Kubernetes, 
a Container Orchestration Technology

- [Architecture](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/1-architecture.md#architecture)
- [Agents](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/1-architecture.md#agents)
- [Master node vs Worker node](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/1-architecture.md#master-node-vs-worker-node)
- [Resources (Objects)](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/1-architecture.md#resources-objects)

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
1. Smallest handling unit in Kubernetes
    * [Pod](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/3.1-pods.md)

2. Pod managers, managing pods with different manners
    * [Replicaset](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/3.2.1-replicasets-%26-repliation-controllers.md): Ensure that the desired number of pods are running in the cluster. The pods can be deployed on the same or different nodes
    * [Deployment](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/3.2.2-deployments.md): Create and kill pods of the same container in random sequence. A replicaset will be created along with deployment creation
    * Daemonset: Ensure that a container is deployed to all the nodes (one pod one node)
    * Statefulset: Create and kill pods of the same container in sequence
    * Job
    * CronJob

3. Networking
    * [Service](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/3.3.1-services.md)
    * Endpoint
    * Ingress

4. Namespace
    * Namespace

5. Volume
    * PersistentVolume
    * PersistentVolumeClaim

6. Sharing data
    * [Secrets](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/3.6.1-secrets.md)
    * ConfigMaps
  
7. Security
    * securityContext (feature of pods)
    * [ServiceAccount, ClusterRole, RoleBinding](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/5-security.md#serviceaccount-clusterrole-rolebinding)
    * [NetworkPolicy](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/5-security.md#network-policy)
