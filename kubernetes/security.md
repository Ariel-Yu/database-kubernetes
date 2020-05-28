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

Once a request is authenticated, Kubernetes is going to check what actions is the request allowed to perfrom. There are 3 authorization mode:
  * ABAC (Action Based Access Control)
  * RBAC (Role Based Access Control)
  * WebHook
  
3. Admission Control

## Security Resources

* SecurityContext
* ServiceAccount, ClusterRole, RoleBinding
* NetworkPolicy

### SecurityContext
Security context can be added at pod and container level. Container level security context will out rule pod level security context

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
