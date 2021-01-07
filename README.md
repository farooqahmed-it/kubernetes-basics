# Kubernetes

## Basics of access and exploring Kubernetes API.
## Demonstrates CRUD operation on Kubernetes resource.

### Observability ###
**$ kubectl version --short**

Client Version: v1.18.0

Server Version: v1.18.0


**$ kubectl get componentstatus**
 
NAME                 STATUS    MESSAGE             ERROR

scheduler            Healthy   ok

controller-manager   Healthy   ok

etcd-0               Healthy   {"health":"true"}



**$ kubectl get nodes**

NAME           STATUS   ROLES    AGE    VERSION

controlplane   Ready    master   160m   v1.18.0

node01         Ready    <none>   159m   v1.18.0



### Namespace ###
**$ kubectl get ns**
 
NAME              STATUS   AGE

default           Active   3h9m

kube-node-lease   Active   3h9m

kube-public       Active   3h9m

kube-system       Active   3h9m



### Access API via kubectl ###
**$ kubectl get --raw /**

{

  "paths": [
  
    "/api",
	
    "/api/v1",
	
	"/logs",
	
    "/metrics",
	
    "/version"
	
  ]
  
}



### Introspect objects in the cluster via the API ###
**$ kubectl get --raw /api/v1** 


**$ kubectl get --raw /api/v1/namespaces/default | jq .** 


### Discover api-resources and api-versions ###
**$ kubectl api-resources** 


### Discover the Explain and Describe commands ###
The Explain command is a great way to understand the defined structure of a resource or kind. This is accomplished through 
kubectl explain <kind> command,

**$ kubectl explain ns** 


### Describe reports the details of the instance of a resource. ###
**$ kubectl describe namespace kube-system**

Name:         kube-system

Labels:       <none>

Annotations:  <none>

Status:       Active


No resource quota.

No LimitRange resource.