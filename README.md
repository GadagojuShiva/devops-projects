<a href="https://kubernetes.io/" target="_blank"><img src="https://img.shields.io/badge/Kubernetes-blue?logo=kubernetes&style=for-the-badge&logoColor=white&labelColor=blue" alt="Kubernetes" width="1000"></a>


# What is Kubernetes?
- Kubernetes is a container orchestration platform that automates the deployment, scaling, and management of containerized applications.
# Why Kuberenetes?
- In scenarios where a DevOps engineer individually manages containers, accessibility to applications can become challenging. For instance, if numerous containers are running in production and some go down, manually restarting each container becomes impractical. Kubernetes addresses this challenge by automating the orchestration and management of containers, ensuring high availability, scalability, and efficient deployment of applications at scale.

# Differences between Docker and Kubernetes

<!-- Docker vs Kubernetes Table -->
 <table>
    <thead>
      <tr>
        <th style="background-color: #f2f2f2;">Docker</th>
        <th style="background-color: #f2f2f2;">Kubernetes</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Ephemeral state:</strong> Containers are designed for stateless applications with data often lost after stopping.</td>
        <td><strong>Long-lived:</strong> Manages stateful applications, ensuring persistence and handling disruptions.</td>
      </tr>
      <tr>
        <td><strong>No autoscaling:</strong> Requires manual scaling based on demand.</td>
        <td><strong>Autoscaling:</strong> Provides automatic horizontal scaling based on metrics like CPU utilization.</td>
      </tr>
      <tr>
        <td><strong>No autohealing:</strong> Lacks built-in mechanisms for automatic recovery from failures.</td>
        <td><strong>Autohealing:</strong> Automatically detects and recovers from container or node failures.</td>
      </tr>
      <tr>
        <td><strong>No enterprise support:</strong> Limited official enterprise-grade support.</td>
        <td><strong>Enterprise support:</strong> Backed by vendors, offers strong enterprise-grade support with SLAs.</td>
      </tr>
    </tbody>
  </table>

# How Kubernetes Solves Docker Challenges

<ul>
  <li>
    <strong>Clustering solves Ephemeral nature:</strong>
    <p>Kubernetes clusters manage containers across nodes, addressing the ephemeral nature of Docker by redistributing workloads and ensuring high availability.</p>
  </li>
  <li>
    <strong>Replica sets enable autoscaling:</strong>
    <p>Kubernetes replica sets dynamically scale containerized applications based on demand, automating the process of adjusting the number of replicas for optimal resource utilization.</p>
  </li>
  <li>
    <strong>Autohealing with Kubernetes control:</strong>
    <p>Kubernetes provides automated recovery mechanisms, detecting and mitigating container or node failures to maintain application stability and reliability.</p>
  </li>
</ul>


# Kubernetes Architecture
![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/Kubernetes.jpg)


# Kubernetes Architecture Components

Lets Take an example of two nodes Maste Node(Control Plan), Worker Node(Data Plan)

## Master Node (Control Plane) Components:

1. **API-Server:**
   - Exposes the Kubernetes API and handles requests from users, as well as internal components like the kubelet.

2. **ETCD:**
   - Key-value store that stores the configuration data of the Kubernetes cluster, ensuring consistency and providing a reliable source of truth.

3. **Scheduler:**
   - Assigns workloads to nodes based on resource availability and constraints, ensuring efficient distribution of tasks.

4. **Control Manager:**
   - Manages various controllers that regulate the state of the cluster. Examples include the Node Controller, Replication Controller, and Endpoints Controller.

5. **Cloud Controller Manager (CCM):**
   - Integrates with cloud provider APIs to allow Kubernetes to control the underlying cloud infrastructure. This facilitates features like load balancing and storage provision. Each cloud provider may have its own CCM.

## Worker Node (Data Plane) Components:

1. **Kubelet:**
   - Ensures that containers are running in a Pod. It communicates with the API-Server to receive instructions and manages the containers on the node.

2. **Kube Proxy:**
   - Maintains network rules on nodes, enabling communication between Pods and external traffic. It helps with service discovery and load balancing.

3. **Container Runtime:**
   - Responsible for running containers. Kubernetes supports multiple container runtimes, such as Docker, containerd, and others.

# What is Kubernetes distrubutions
- A Kubernetes distribution is a software package that provides a pre-built version of Kubernetes
- For Examples: 
  Linux-
  - | Amazon Linux
  - | Ubuntu
  - | CentOs
  
![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/Distrubutions_of_Kubernetes.jpg)

# Difference Between Kubernetes and EKS

<table>
    <tr>
      <th>Kubernetes</th>
      <th>Amazon EKS</th>
    </tr>
    <tr>
      <td>Not managed (self-managed)</td>
      <td>Managed by AWS</td>
    </tr>
    <tr>
      <td>Open Source</td>
      <td>Amazon EKS is a managed service provided by AWS, and the management aspect is not open source.</td>
    </tr>
  </table>

# What is Mean By POD in kubernetes
- A Pod is like a blueprint that tells Kubernetes how to run a container. In Docker, we use a command like docker run to start a container, but in Kubernetes, we create a file called pod.yml to define everything, and then we use kubectl apply -f pod.yml to make it happen. Usually, a Pod has only one container, but sometimes it might have more.

- **Example of pod.yml file: [Link to pod.yml](pod.yml)**

# What is Kubectl 
- Kubectl is a command-line tool for working with Kubernetes. It helps you manage your applications running on a Kubernetes cluster.

# Some of the most used kubectl commands:

```bash 
# Create a pod based on the configuration in pod.yml
kubectl create -f pod.yml

# Get information about the nodes in the cluster
kubectl get nodes

# See the list of running pods
kubectl get pods

# Get more details about a specific pod
kubectl get pod -o wide

# Display information about all resources
kubectl get all

# Display information in watch mode
kubectl get pod -w
```

# Kubernetes Deployment
A Kubernetes Deployment is a way to achieve automatic healing and scaling for your applications.

<strong>Auto-Healing:</strong>
When you create a Deployment in Kubernetes, it automatically takes care of ensuring that the desired number of replicas (defined in the replicas variable in the deployment.yml file) are always running. For instance, if you set replicas: 2, and one pod unexpectedly goes down or is intentionally deleted, Kubernetes Deployment will swiftly create a new pod to replace it. This ensures that the specified number of pods is maintained, promoting resilience and minimizing downtime.

<strong>Auto-Scaling:</strong>
The concept of auto-scaling is inherent in Kubernetes Deployments. If you need to scale your application based on demand or other metrics, you can easily adjust the replicas value in your Deployment configuration. For example, if you initially set replicas: 2 and later decide to scale up to handle increased traffic, you can update it to replicas: 3, and Kubernetes will automatically create an additional pod.

<strong>In summary:</strong> 
Kubernetes Deployments provide a robust mechanism for managing the lifecycle of your application, automatically healing it in case of failures, and allowing for seamless scaling to adapt to changing requirements.



# Some of Kubernetes Deployments commands

```bash
# Get information about Deployments
kubectl get deploy

# Get information about ReplicaSets
kubectl get rs

# Apply a Deployment configuration from a YAML file
kubectl apply -f deployment.yml
```
**Example of deployment.yml file: [Link to Deployment.yml](deployment.yml)**

# Deployment Overview

![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/pod-depolyement.jpg)

# Why Services in Kubernetes?

- In Kubernetes, services play a crucial role in ensuring reliable and accessible communication between different components of an application. <strong>Let's first understand how Kubernetes operates without services.</strong>

- <strong>Example</strong>: Imagine you have three pods (P1, P2, P3) serving an application, and three individuals (I1, I2, I3) are accessing these pods. Now, if one of the pods, let's say P1, goes down due to some issue, Kubernetes automatically creates a new pod to replace it. However, the problem arises because the new pod gets a new IP address. As a result, I1, who was using the old IP to access the application, can no longer reach the newly created pod.

- This manual assignment of IP addresses to customers becomes impractical. This is where Kubernetes services come into play.

<Strong>How Kubernetes Works with Services:</Strong>

- Kubernetes introduces services to address the issue mentioned earlier. Here's how it works:

- <strong>Load Balancing:</strong> Kubernetes has a service called load balancing. This service is placed in front of your deployment, and you provide the IP address of this load balancer to the individuals (I1, I2, I3). Now, regardless of which pod is serving the application, users can access it through the load balancer's IP.

- <strong>Discovery Services:</strong> Even with load balancing, there's a potential problem of changing IP addresses. This is where discovery services come in. Kubernetes uses labels and selectors to overcome this challenge.

- When you define your deployment in the deployment.yaml file, you include metadata with a label, for example, label: exampleapp. This label is associated with all pods created by that deployment.

- When a pod goes down and is autohealed, Kubernetes uses the same deployment.yaml file to create a new pod. Although the IP address changes, the label remains the same.

- With <strong>labels</strong> and <strong>selectors</strong>, the discovery service ensures that regardless of the pod's IP address, users can reliably access the application through the load balancer using the label.

- In <strong>summary</strong>, Kubernetes services, including load balancing and discovery services, simplify the management of communication between different components of an application, ensuring reliability and accessibility even when pods are dynamically created or replaced.

# Different Types of Services:
<!-- 
1. <strong>ClusterIP:</strong>

   - <strong>Access Scope:</strong> Limited to within the Kubernetes cluster.
   - Access Control: Accessible to other pods within the same cluster.
   - <strong>Use Case:</strong> 
     - Suitable for internal communication between different components (pods) of an application within the Kubernetes cluster. It's not directly accessible from outside the cluster.

2. <strong>NodePort:</strong>

   - <strong>Access Scope:</strong> Accessible within your organization and potentially externally (depending on firewall settings and network configuration).
   - <strong>Access Control:</strong> Offers external access to the service on a specific port across all nodes in the cluster.
   - <strong>Use Case:</strong>
     - Useful when you need to expose a service to users or applications within your organization. It allows external access, but it might not be suitable for public-facing services due to potential security concerns.

  3. <strong>LoadBalancer:</strong>
     - <strong>Access Scope:</strong> Exposes the service to the external world.
     - <strong>Access Control:</strong> Typically accessible globally, making the service reachable from the internet.
     - <strong>Use Case: </strong>
       -  Ideal for services that need to be exposed to the public internet. It utilizes an external load balancer provided by the cloud provider to distribute traffic to the underlying pods. -->

<!-- <strong>In summary:</Strong> -->

1. <strong>ClusterIP:</strong> Internal communication within the cluster.
2. <strong>NodePort:</strong> Accessible within your organization, and potentially externally.
3. <strong>LoadBalancer:</strong> Exposes the service to the external world, suitable for public-facing services.
  
# Example on Node Port:
- **Example of Service.yml file: [Link to service.yml](service.yml)**
- Note:<span style="color: #FF9800;"> We Cannot do loadBalancing or Exposing application to external world on Minikube Because Minikube is a tool designed to run Kubernetes clusters locally for development and testing purposes. It provides a lightweight and easy-to-set-up environment to simulate a Kubernetes cluster on a single machine. However, there are certain limitations in Minikube that make it less suitable for certain production-like scenarios, such as load balancing and exposing applications to the external world in the same way you would in a production environment</span>
- **ClusterIP:** Default Service, This represents the default service type in Kubernetes.

# Ingress

- An Ingress is a Kubernetes object that defines routing rules, facilitating the management of external access to services within a cluster
- In Kubernetes, without using Ingress, the default load balancing mechanism is <strong>round-robin</strong>, where incoming requests are evenly distributed among the available pods. However, for more advanced features and routing capabilities, Ingress can be employed with specific ingress controllers.
- <strong>Motivation for Ingress:</strong>
  - <strong>Problem-1</strong>:Lack of Advanced Features (Round Robin Mechanics) 
  Prior to Kubernetes, many companies utilized virtual machines (VMs) with various load balancers (e.g., Nginx, F5), offering features like <strong>sticky sessions</strong>, <strong>path-based routing</strong>, <strong>domain-based routing</strong>, <strong>IP whitelisting</strong>, <strong>blacklisting</strong>, and more. However, when transitioning to Kubernetes, some of these advanced features were initially missing. While Kubernetes provides options like <strong>load balancing</strong> and <strong>NodePort</strong> for service exposure, features such as sticky sessions and complex routing were not readily available.
  - <strong>Problem-2</strong>: Cost
  - When utilizing a load balancing service in Kubernetes, the cloud provider generates an elastic IP, leading to increased costs.

- <strong>To address this gap</strong>, 
  - Kubernetes introduced the Ingress concept. Instead of building all these features natively into Kubernetes, it encourages users to create Ingress resources. Meanwhile, load balancing companies developed Ingress controllers that integrate with Kubernetes. Users can then select an appropriate Ingress controller, deploy it in their Kubernetes cluster, and create Ingress resources to define specific requirements such as routing rules, thereby solving the identified problem.
  
- [x] <span style="color: #FF0000;">You can find the **Example of ingress.yml file: [Link to ingress.yml](ingress.yml)**</span>

 ```
  # Create Ingress resource from ingress.yml
    kubectl apply -f ingress.yml

    # Check the status of Ingress resources
    kubectl get ingress 
  ```

# SSL/TLS termination strategies:
**Here are the main strategies:**
  - SSL PassThrough
  - SSL Offloading
  - SSL Bridging

**SSL PassThrough**
- ‘SSL passthrough’ passes encrypted HTTPS traffics directly to the backend servers without decrypting the traffics on the load balancer. So any nodescan’t read the contents in the traffic and pass through them all the way to the destination.
    <!-- Image -->
![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/SSL-Passthrough.jpg)

**SSL Offloading**
  - SSL termination (a.c.a. SSL Offloading) decrypts all HTTPS traffics when it arrives at the load balancer, and the data is sent to the destination server as plain HTTP traffic.
    <!-- Image -->
![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/SSL-Offloading.jpg)

**SSL Bridging**
  - SSL bridging is a process where incoming encrypted (SSL/TLS) traffic is decrypted at a load balancer or a similar device. The load balancer inspects the decrypted traffic for security purposes, and then re-encrypts it before forwarding to the backend servers. This allows the load balancer to perform security checks on the traffic without burdening the backend servers with the task of SSL/TLS encryption and decryption.
  <!-- Image -->
![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/SSL-Bridging.jpg)

# Introduction to Kubernetes RBAC(Role based action control)

- Kubernetes Role-Based Access Control (RBAC) is a security feature that controls access to Kubernetes resources based on a user's role. It's a type of identity and access management (IAM) in AWS.
- **Example :**
  - Okay, imagine Kubernetes is like a big shared office space, and different teams work in different rooms. RBAC, or Role-Based Access Control, is like giving everyone the right keys to the right rooms and saying what they can do there.
  - **Role:** (Giving permissions to act on a work) A 'Role' is like a specific job. Let's say we have a job called 'Pod Viewer,' which means you can only look at and get information about pods.
  - **Role Binding:** (attacting the role to the user)'Role Binding' is like giving that job to a person. If we give the 'Pod Viewer' job to Alice, it means she can only look at and get info about pods.
    
  - So, in Kubernetes, we create a 'Pod Viewer' job (Role) and then give that job to specific people (Role Binding). This way, each person can only do what their job allows, making sure they don't mess with things they shouldn't. It's like making sure everyone has the right keys to the right rooms in our shared office space.

-  In Kubernetes, creating users is not like how we do it on regular systems like Linux. Instead of using commands to add users, Kubernetes lets external services handle user management. For example, many apps now allow you to log in with your Google or Instagram account. In this case, Kubernetes relies on these external services for user information. So, making users in Kubernetes means connecting to these outside sources for user details, not using the usual user creation commands.

# Custom Resource Definition (CRD):

- **Purpose**: Enhancing Kubernetes with additional features that are not present in the core Kubernetes API.
- **Example Use Case:** If you need an advanced security feature, you might create a Custom Resource Definition for a custom security policy.
- **Components:**
  - **CRD:** Custom Resource Definition is like a blueprint. It defines a new resource type along with its properties, similar to how a Deployment resource is defined in a YAML file.
  - **CR:** Custom Resource is an instance of the custom resource type defined by a CRD. It represents the actual object you want to create or manage, like an instance of your advanced security policy.
  - **Custom Controllers:** These are controllers created to watch and manage Custom Resources. They define the behavior and actions associated with your custom resource type.

![Alt Text](https://github.com/GadagojuShiva/kubernetes-examples/blob/main/flow-of-custom-resources.jpg)

- **Example Explanation:**

  - Imagine you want to manage a specialized security policy in your Kubernetes cluster.
  - You create a Custom Resource Definition (CRD) that defines what this security policy should look like and what properties it should have.
  - Users can then create instances of this security policy using Custom Resources (CR). These instances conform to the blueprint laid out by the CRD.
  - Custom Controllers watch for these custom resources. For instance, you might have a "SecurityPolicyController" specifically built to handle the lifecycle of your custom security policies.
  - When a user creates or updates a custom resource, the associated custom controller takes action. It could enforce security policies, update configurations, or trigger other actions based on the defined behavior.

- **Analogy:**

  - Think of a CRD as the form you fill out to request a new service (e.g., advanced security).
  - The CR is the actual form you submit, specifying the details of the service you want.
  - Custom Controllers are like the service providers who process your form, ensuring that the requested service is implemented and maintained according to your specifications.
  - This mechanism provides extensibility to Kubernetes, allowing users to define and manage custom resources beyond what is provided by default in Kubernetes.
     
# ConfigMaps and Secrets in kubernetes

- **ConfigMaps:**
  - ConfigMaps are used to store non-sensitive configuration data in key-value pairs, which can be consumed by Pods and other resources in a Kubernetes cluster.
- **Example**
  - Imagine you have a web application that connects to a MySQL database. The database connection details, including the host, port, username, and password, are essential for the application to function. Instead of hardcoding these details into the application code or Docker image, you decide to use a ConfigMap to manage the configuration separately.
  
- **Secrets:**
  -  Secrets are used to separate sensitive data from application code and configuration, ensuring a more secure handling of sensitive information within the cluster and this are encrypted with base64-encoded
- **Example:**
  - Passwords,bd details

# Differences between ConfigMap and Secrets

<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th>Secrets</th>
      <th>ConfigMaps</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Purpose</strong></td>
      <td>Securely store sensitive data</td>
      <td>Store non-sensitive configuration</td>
    </tr>
    <tr>
      <td><strong>Data Security</strong></td>
      <td>Encoded (not encrypted)</td>
      <td>Plain text</td>
    </tr>
    <tr>
      <td><strong>Example Use Cases</strong></td>
      <td>Database credentials, API keys</td>
      <td>Environment variables, config files</td>
    </tr>
    <tr>
      <td><strong>Pod Consumption</strong></td>
      <td>Environment variables, volumes</td>
      <td>Environment variables, volumes</td>
    </tr>
    <tr>
      <td><strong>Immutability</strong></td>
      <td>Immutable after creation</td>
      <td>Immutable after creation</td>
    </tr>
    <tr>
      <td><strong>Encoding</strong></td>
      <td>Base64 encoded</td>
      <td>Plain text</td>
    </tr>
  </tbody>
</table>

# Kubernetes Monitoring

- **Monitoring** is crucial in Kubernetes to keep track of how everything is running. When dealing with multiple clusters, manually watching each one becomes impractical. That's where monitoring platforms like Prometheus and Grafana come in.

- **Prometheus:** Think of Prometheus as the detective. It asks questions about what's happening in the clusters.

- **Grafana:** Now, imagine Grafana as the artist who takes the detective's findings and turns them into visual, easy-to-understand charts and graphs. It helps you see and understand what's going on.

- So, Prometheus queries the clusters, Grafana makes the information look good, and together they help you keep everything in check.

  <!-- Image -->
__________________________________
# Kubernetes Interview Questions and Answers

## 1. What is the difference between Docker and Kubernetes?
- **Docker:** Containerization platform for packaging, distributing, and running applications.
- **Kubernetes:** Container orchestration platform for automating deployment, scaling, and management of containerized applications.

## 2. What are the main components of the Kubernetes architecture?
### Master Node Components:
- API Server
- ETCD
- Scheduler
- Control Manager
- Cloud Controller Manager (CCM)
### Worker Node Components:
- Kubelet
- Kube Proxy
- Container Runtime

## 3. Difference between Pod and container?
- **Pod:** Smallest deployable unit in Kubernetes, can contain one or more containers sharing the same network namespace.
- **Container:** Lightweight, standalone, and executable software package that includes everything needed to run a piece of software.

## 4. What is Mean By namespace in Kubernetes?
- **Namespace:** It is a logical separation of resources, network policies, RBAC, and everything else within a Kubernetes cluster. For example, if there are two projects using the same cluster, one can use `ns1` and another one can use `ns2` without any overlaps.


## 5. What is the role of Kube-proxy?
- **Kube-proxy:** Maintains network rules on nodes, enabling communication between pods and external traffic. It helps with service discovery and load balancing.

## 6. Different types of services in Kubernetes?
- **ClusterIP:** Internal communication within the cluster.
- **NodePort:** Accessible within the organization and potentially externally.
- **LoadBalancer:** Exposes services to the external world.

## 7. Difference between node port and load balancer?
- **NodePort:** When a service is created using NodePort, Kube-proxy updates the IPtable with the node IP address and port chosen in the service configuration of the pod.
- **LoadBalancer:** In this, Cloud Controller Manager creates an external load balancer IP using the underlying cloud provider's logic.


## 8. What is the role of Kubelet?
- **Kubelet:** Ensures that containers are running in a pod on a node. It communicates with the API server to receive instructions and manages the containers on the node.





