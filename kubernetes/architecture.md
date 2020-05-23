# Kubernetes, 
a Container Orchestration Technology

## Architecture
* Node / Worker node / Minion: Worker server/machine
* Cluster: A set of nodes
* Master / Master node: A node that orchestrates all the containers on the nodes within a cluster

## Components
* API server: 
    * Serve as the frontend of Kubernetes
    * Users, management devices and CLI all talk to the API server
* etcd
    * A distributed key-value store used by Kubernetes to store all the data used to manage the cluster
    * Logs
* Scheduler
    * Distribute containers among all nodes
    * Distribute work among all containers on the nodes
* Controller
    * Brain of the orchestration
    * Notice and respond to if any API or node is down
    * Decide if a new node or container is needed
    * Types of controller
        * Node controller
        * Replica controller
* kubelet
    * The agent that is run on each node in the cluster
    * Ensure that the containers are run successfully on each node
* Container runtime
    * Underlying software used to run containers ex: Docker

## Master node vs. Worker node
### Master node
* API server - what makes the server a master node
* etcd
* Scheduler
* Controller
### Worker node
* kubelet: 
    * Talks to API server on the master node
    * Provide health information of the worker nodes
    * Carry out actions that are instructed by the master node
* Container runtime
