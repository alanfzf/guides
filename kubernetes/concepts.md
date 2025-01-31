# Kubernetes concepts

## Terminology

### POD
A pod is a group of containers and is the smallest unit in Kubernetes, it can have one or more containers, usually if there's multiple containers in a pod is because they are strictly tied.

> [!IMPORTANT]
> Containers in a pod share the same ip address and can communicate trough `127.0.0.1` without extra configuration.

### Deployment
A Deployment is basket that holds multiple pods, it orchestrates how they scale and how they update/create basically it defines the life cycle of our pods

> [!NOTE]
> Deployments are a subset of replica sets

### Service
A service exposes our deployments to other **resources** inside our kubernetes cluster, a service is required because a deployment by itself cannot communicate with other **resources** without a service.

### Node
A node can either be a physical or virtual machine that runs kubernetes resources

### Cluster
A cluster is a group of nodes, fundamentally its composed by at least a master node and one ore more worker nodes.

### Namespace

## Miscellaneous concepts

### Config map
### Secrets map
### Persistent Volume Claim (data persistence)
### Pull Policy
### Strategy type
### The `Selector` keyword

## Networking

### Cluster IP
A Cluster IP is a kubernetes resource that provides internal IP addresses to make services across our cluster accessible to each other.

### Node Port
A node port helps us expose a service on a static port from the range of 30000 to 32767, users can access the service trough [NodeIP]:[NodePORT],
as far as i know this is only useful for Dev/QA purposes.

### Load Balancer
A load balancer is a kubernetes resource that provisions public IP addresses to expose our services, to the outside world.

It requires a cloud provider load balancer like:
- AWS ELB
- Azure Load Balancer
- GCP LB

> [!NOTE]
> If we are running a managed kubernetes cluster in our own servers, we require a custom load balancer like [MetalLB](https://metallb.io/) otherwise we cannot expose our services to the public.

### Ingress Controller
An Ingress Controller is a component in Kubernetes that manages external access to services within a cluster. It is responsible for routing HTTP and HTTPS traffic based on the rules defined in Ingress resources.
