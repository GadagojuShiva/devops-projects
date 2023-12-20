<a href="https://kubernetes.io/" target="_blank"><img src="https://img.shields.io/badge/Kubernetes-blue?logo=kubernetes&style=for-the-badge&logoColor=white&labelColor=blue" alt="Kubernetes" width="1000"></a>


# What is Kubernetes?
- Kubernetes is a container orchestration platform that automates the deployment, scaling, and management of containerized applications.
# Why Kuberenetes?
- In scenarios where a DevOps engineer individually manages containers, accessibility to applications can become challenging. For instance, if numerous containers are running in production and some go down, manually restarting each container becomes impractical. Kubernetes addresses this challenge by automating the orchestration and management of containers, ensuring high availability, scalability, and efficient deployment of applications at scale.

# Differences between Docker and Kubernetes

<!-- Docker vs Kubernetes Table -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    table {
      border-collapse: collapse;
      width: 100%;
    }

    th, td {
      border: 1px solid #ddd;
      padding: 8px;
      text-align: left;
    }

    /* Light background color for Docker header cell */
    th:first-child {
      background-color: #f2f2f2;
    }

    /* Light background color for Kubernetes header cell */
    th:nth-child(2) {
      background-color: #f2f2f2;
    }
  </style>
</head>
<body>

<table>
  <thead>
    <tr>
      <th>Docker</th>
      <th>Kubernetes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Ephemeral state: Containers are designed for stateless applications with data often lost after stopping.</td>
      <td>Long-lived: Manages stateful applications, ensuring persistence and handling disruptions.</td>
    </tr>
    <tr>
      <td>No autoscaling: Requires manual scaling based on demand.</td>
      <td>Autoscaling: Provides automatic horizontal scaling based on metrics like CPU utilization.</td>
    </tr>
    <tr>
      <td>No autohealing: Lacks built-in mechanisms for automatic recovery from failures.</td>
      <td>Autohealing: Automatically detects and recovers from container or node failures.</td>
    </tr>
    <tr>
      <td>No enterprise support: Limited official enterprise-grade support.</td>
      <td>Enterprise support: Backed by vendors, offers strong enterprise-grade support with SLAs.</td>
    </tr>
  </tbody>
</table>

</body>
</html>


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




# Kubernetes Architecture Components

Lets Take an example of two node 1. Maste Node(Control Plan), 2. Worker Node(Data Plan)

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

# Kubernetes Architecture
 - Coming Up...............