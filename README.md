# K8S
Kubernetes Basics
Kubernetes (K8S)

What  is Kubernetes or K8S?
K8S is the container orchestration platform. What does it mean ?. Before jumping into K8S lets summarise about docker and containers. So Containers are basically the software package of applications + libraries and system dependencies. They are widely used in the organisations to run/test and deploy applications because they are light weight in nature and they require very less dependencies to run the applications on them. Docker is the open source orchestration platform. One of the issue with containers is that they are ephemeral in nature ( they are short lived) lets discuss few of the short comings of containers. 

**CONTAINER Architecture**

<img width="314" alt="image" src="https://github.com/user-attachments/assets/b40cfc31-0639-439a-a4b7-ab75e1d8b6c4">
 
1- Load balancer
2- Firewall
3- Auto scaling
4- Auto Healing
5- API Gateways
6- Enterprise level support

If we have to deploy containers in the real production environments then these issue must be addressed. All of them are solved by K8S and lets discuss them one by one

1- Load balancer 
In Kubernetes, load balancing refers to the method of distributing network traffic across multiple instances of an application or service to ensure reliability, high availability, and efficient resource utilization. Kubernetes provides built-in load balancing mechanisms for managing both internal and external traffic.

2- Firewall 
In Kubernetes, a firewall typically refers to mechanisms that control and restrict network traffic to and from Kubernetes resources (such as pods, services, and nodes) based on specified rules. Kubernetes itself does not come with a built-in firewall in the traditional sense (like iptables or cloud firewalls), but there are several ways to implement network security and traffic control in a Kubernetes cluster, often using Network Policies, Cloud Provider Security Groups, or external firewall solutions.

3- Auto scaling 
Auto-scaling in Kubernetes refers to the process of automatically adjusting the number of running pods or nodes in a Kubernetes cluster to meet changing resource demands. This dynamic scaling helps ensure that applications maintain optimal performance and resource usage while minimizing operational overhead.

4- Auto Healing 
Auto-healing in Kubernetes refers to the system's ability to automatically detect and recover from failures in a cluster to ensure that applications continue running smoothly without manual intervention. This is achieved by using built-in features like self-healing mechanisms to ensure that applications, services, and workloads are always running as expected.

5- API Gateways 
In Kubernetes, an API Gateway is an intermediary layer that handles requests from clients and routes them to appropriate services within the cluster. It is often used to manage, secure, and optimize API traffic in microservices architectures. API Gateways provide several key functionalities like load balancing, authentication, authorization, traffic routing, rate limiting, caching, and monitoring. They act as a single entry point for all client requests, abstracting the complexity of the underlying services.

6- Enterprise level support 
Enterprise-level support in Kubernetes refers to professional services, tools, and solutions provided to help organizations deploy, manage, and scale Kubernetes clusters in production environments. Enterprises typically require more robust support for mission-critical applications, including high availability, security, performance, compliance, and disaster recovery. Kubernetes, being an open-source platform, offers powerful capabilities, but enterprises often seek additional support to ensure reliability, uptime, and governance at scale.


<img width="437" alt="image" src="https://github.com/user-attachments/assets/7c7a38ac-de4c-4e7a-8342-f0ccadf212c8">


**Master Control Plane:**
API Server: This is the main entry point for all interactions with a Kubernetes cluster. It exposes the Kubernetes API, allowing users, admins, and other components to communicate with the cluster.

etcd: 
A distributed key-value store that holds all the configuration data and state of the Kubernetes cluster. It stores important information such as Pods, Services, and other cluster settings.


Controller Manager: 
This component ensures that the desired state of various cluster objects (like Pods and Deployments) is maintained. If any object drifts from its desired state, the Controller Manager takes corrective actions.


Scheduler: 
The Scheduler decides where to place Pods within the cluster, considering factors such as available resources and constraints.
Together, these components form the master control plane, which manages and coordinates the entire Kubernetes cluster.


Worker Nodes:
Worker nodes, or servers, are where the actual applications run. They execute the workloads of your applications within containers.


Kubelet: An agent on each worker node, it ensures that containers are running as expected based on the desired configuration and communicates with the control plane to manage containers.

Kube Proxy: 
It handles networking and load balancing for Pods, ensuring smooth communication between services and with the outside world.



Container Runtime: 
This software runs the containers on the worker nodes.



Container Storage Interface (CSI): 
Provides persistent storage for containers. Kubernetes uses CSI to allow different storage providers to integrate with the system, ensuring containers have access to storage as needed.


Pods:
Pods are the basic unit in Kubernetes that groups one or more containers. They run together within the same environment and share networking and storage resources.


Container Co-location: Containers within a Pod can communicate with each other using localhost and share the same IP address and ports.

Shared Storage and Volumes: All containers in a Pod can share the same storage volumes, making it easy to share data.

Single Unit of Deployment: Pods are the smallest deployable unit in Kubernetes. Scaling is done at the Pod level, not at the container level.

Init Containers: These are special containers that run before the main application containers to perform setup tasks.

Controllers:
Controllers in Kubernetes are responsible for ensuring that the actual state of the cluster matches the desired state.

Replication Controller: Ensures a specified number of identical Pods are running. If a Pod fails, it creates a new one to maintain the desired number.

Deployment: Helps manage updates to applications by defining the number of replica Pods and performing rolling updates to minimize downtime. It also supports rollbacks if necessary.

StatefulSet: Used for stateful applications that need unique identities and persistent storage, ensuring that Pods have a stable hostname.

DaemonSet: Ensures that a specific Pod runs on every node in the cluster, useful for tasks like monitoring or logging.

Horizontal Pod Autoscaler (HPA): Automatically adjusts the number of Pods based on metrics like CPU usage or custom metrics.

Vertical Pod Autoscaler (VPA): Adjusts resource requests and limits for Pods based on actual usage to improve efficiency.


Services:
Services provide a stable way to expose applications running in Pods to other services, both within and outside the cluster.

Service Types: Different types of services are available, depending on your needs:

ClusterIP: Exposes a service within the cluster.
NodePort: Exposes a service on a static port on each node’s IP for external access.
LoadBalancer: Creates an external load balancer to distribute traffic.
ExternalName: Maps a service to an external DNS name.
Selectors and Labels: Services use selectors to determine which Pods they should target. Pods are identified by labels (key-value pairs).

Load Balancing: Services automatically balance traffic across multiple Pods with the same label.

Headless Services: These services don’t load balance or provide a stable IP, allowing direct access to individual Pods.


Volumes:
Volumes provide persistent storage to containers. They ensure that data is not lost when containers are restarted or rescheduled.

Types of Volumes:
EmptyDir: Temporary storage that’s deleted when the Pod is removed.
HostPath: Mounts a file or directory from the host’s filesystem.
PersistentVolumeClaim (PVC): A request for persistent storage, which Kubernetes can dynamically provision.
ConfigMap and Secret Volumes: Allows you to inject configuration or sensitive data into containers.
NFS: Allows use of network-attached storage.
CSI Volumes: A plugin framework for integrating various storage providers with Kubernetes.
ConfigMaps and Secrets:
ConfigMaps: Store non-sensitive configuration data like environment variables, configuration files, and command-line arguments.


Secrets: 
Store sensitive data like passwords, tokens, and certificates in a secure manner, preventing them from being exposed in plain text.


Namespaces:
Namespaces help organize resources within a cluster, creating isolated environments for different teams or projects.

Purpose of Namespaces:

Resource Isolation: Prevents resource conflicts between teams or projects.
Resource Management: Helps manage and track resources effectively.
Access Control: Enables access control based on teams or roles.
Tenant Separation: Useful for multi-tenant clusters where different customers or services need isolated environments.
Default Namespace: Kubernetes creates a default namespace where resources go if not specified.

Namespace Scope: Some resources like Nodes and PersistentVolumes are global, while others (like Pods and Services) are namespace-specific.
Access Control and Quotas: Allows setting limits and controlling access to resources within each namespace.


Ingress:
Ingress is used to manage external access to your services, typically over HTTP and HTTPS, without modifying the application code.

Purpose of Ingress: It routes external traffic to the appropriate service inside the cluster.

How Ingress Works: Defines rules for routing traffic to services based on hostnames, paths, or other criteria.

Ingress Controller: This component manages the actual routing by watching the Ingress resources and configuring the infrastructure to implement the defined routing rules.








