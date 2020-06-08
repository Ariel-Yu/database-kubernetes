# Security in Kubernetes
There are 3 steps for accessing Kubernetes API:

1. Authentication

   Kubernetes authentication is done by either one of the following:
   * Basic username:password
   * Token
   * Certificate
   * Webhooks
   * OpenID

2. Authorization

   Permission at role level. Once a request is authenticated, Kubernetes is going to check what actions are the request 
   allowed to perfrom. There are 3 authorization modes:
    * ABAC (Action Based Access Control)
    * RBAC (Role Based Access Control)
    * WebHook
  
3. Admission Control

   Permission at cluter level. Verify what actions are allowed in the certain cluster

## Security Resources

* [SecurityContext](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/5-security.md#securitycontext)
* [ServiceAccount, ClusterRole, RoleBinding](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/5-security.md#serviceaccount-clusterrole-rolebinding)
* [NetworkPolicy](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kubernetes/5-security.md#networkpolicy)

### SecurityContext
- Security context can be added at **pod** and **container** level
- Container level security context will out rule pod level security context
- `capabilities` is only supported at the **container** level

```
apiVersion: v1
kind: Pod
metadata:
  name: securityapp
  labels:
    type: security
spec:
  securityContext:
    runAsUser: 1000
  containers:
  - name: busy
    image: busybox
    command:
      - sleep
      - "3600"
    securityContext:
      runAsUser: 2000
      allowPrivilegeEscalation: false
      capabilities:
        add: ["NET_ADMIN", "SYS_TIME"]
```

### ServiceAccount, ClusterRole, RoleBinding

1. Create a serviceaccount
```
apiVersion: v1
kind: ServiceAccount
metadata:
 name: secret-access-ariel
```

2. Create a clusterrole
```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
 name: secret-access-ariel
rules:
- apiGroups:
  - ""
  resources:
  - secrets
  verbs:
  - get
  - list
```

3. Create a rolebinding
```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
 name: secret-ariel
subjects:
- kind: ServiceAccount
  name: secret-access-ariel
roleRef:
 kind: ClusterRole
 name: secret-access-ariel
 apiGroup: rbac.authorization.k8s.io
```

4. Add serviceaccount to a pod
```
...
spec:
  serviceAccountName: <serviceaccount_name>
  securityContext: {}
  containers: [{}]
  volumes: [{}]
```
   - The pod will only have the permission to get and list secrets by the rules defined in clusterrole binded with the serviceaccount which the pod is using

### NetworkPolicy

```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-default
spec:
  podSelector: {}
  policyTypes:
  - Egress
  - Ingress
  ingress:
  - from:
    - ipBlock:
            cidr: 192.168.0.0/16
    ports:
    - port: 80
      protocol: TCP
```

1. All outbound networking from the cluster will be blocked by `Egress`
2. Inbound networking in the cluster will be blocked by `Igress` except `ingress.from`
   - IPs in the range under `ipBlock`
   - Ports with portocal under `ports`
3. `name: deny-default`

## Security Resources kubectl
```
<SHORTNAME of serviceaccount = sa>
kubectl get serviceaccount|clusterrole|rolebinding [<serviceaccount|clusterrole|rolebinding_name>]
kubectl get serviceaccount|clusterrole|rolebinding [<serviceaccount|clusterrole|rolebinding_name>] -o wide
kubectl describe serviceaccount|clusterrole|rolebinding [<serviceaccount|clusterrole|rolebinding_name>]
kubectl explain serviceaccount|clusterrole|rolebinding
```
