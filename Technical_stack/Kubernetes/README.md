* Kunernetes architecture

![image](https://user-images.githubusercontent.com/46215433/227093320-0d78b681-7e9b-4a6b-bef4-2c8402312c71.png)

* Minikube installation
* Service account:A service account provides an identity for processes that run in a Pod, and maps to a ServiceAccount object. It is used to authenticate machine level processes to get access to our Kubernetes cluster. The API server is responsible for such authentication to the processes running in the pod
* User Account: It is used to allow us, humans, to access the given Kubernetes cluster. Any user needs to get authenticated by the API server to do so. A user account can be an admin or a developer who is trying to access the cluster level resources.
* init container and sidecar container : https://blog.knoldus.com/sidecar-container-vs-init-container-in-kubernetes/
* ConfigMap: A ConfigMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume.
* Secrets: A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key. Such information might otherwise be put in a Pod specification or in a container image. Using a Secret means that you don't need to include confidential data in your application code.
* Custom resource definition(CRD): A custom resource is an object that extends the Kubernetes API or allows you to introduce your own API into a project or a cluster. A custom resource definition (CRD) file defines your own object kinds and lets the API Server handle the entire lifecycle.
* POD status troubleshooting: https://docs.bitnami.com/kubernetes/faq/troubleshooting/troubleshooting-pods/#:~:text=Troubleshoot%20pod%20issues-,Detect%20issues,to%20obtain%20more%20detailed%20information.
* Different between podman and docker engine
* How to get node external IP on to Pod?
* Pod afinity and pod anti afinity 
* Adapter container 
* How to setup scalable jenkins on top of kubernetes cluster 
* Persistent volume

![image](https://user-images.githubusercontent.com/46215433/227110931-1e1adf49-da57-4cc2-895d-c59efd26e785.png)

1. Ephemeral Volumes - These are used for applications that need storage but do not need to access the data after a restart. Ephemeral volumes only last the lifetime of their PODs, and are deleted when the POD stops running. Ephemeral volumes are applicable for low latency applications where limited memory size may impact performance. Kubernetes allows various kinds of ephemeral volumes for different uses, including: emptyDir, Secrets, ConfigMaps and the downwardAPI
2. A persistent volume (PV) is the "physical" volume on the host machine that stores your persistent data. A persistent volume claim (PVC) is a request for the platform to create a PV for you, and you attach PVs to your pods via a PVC.

* Network policies 
* Auto scaling of pods based on CPU utlization using Horizantal pod autoscaler
* Deployment strategies: https://spot.io/resources/kubernetes-autoscaling/5-kubernetes-deployment-strategies-roll-out-like-the-pros/
 1. Rolling Deployment/Update: A rolling deployment is the default deployment strategy in Kubernetes. It replaces the existing version of pods with a new version, updating pods slowly one by one, without cluster downtime. 
 2. Recreate: This is a basic deployment pattern which simply shuts down all the old pods and replaces them with new ones. You define it by setting the spec:strategy:type section of your manifest to Recreate
 3. Canary Deployment: Canary deployments are typically used to test some new features on the backend of an application. Two or more services or versions of an application are deployed in parallel, one running an existing version, and one with new features. Users are gradually shifted to the new version, allowing the new version to be validated by exposing it to real users.
* Replication Type:  
1. Deployment: A Deployment is a Kubernetes object that manages a set of identical pods, ensuring that a specified number of replicas of the pod are running at any given time. It provides a declarative approach to managing Kubernetes objects, allowing for automated rollouts and rollbacks of containerized applications.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
        - name: myapp-container
          image: myapp:latest
          ports:
            - containerPort: 80
```
2. ReplicaSets: A ReplicaSet is a Kubernetes object that ensures that a specified number of replicas of a pod are running at any given time. It manages the lifecycle of pods and provides a way to scale and maintain the desired state of the application.
3. ReplicationController: A ReplicationController ensures that a specified number of pod replicas are running at any one time
4. Different between ReplicationController vs ReplicaSets: the replication controller only supports equality-based selectors whereas the replica set supports set-based selectors.
5. Different between Replicaset vs Deployment

![image](https://user-images.githubusercontent.com/46215433/227103845-1ea9dd9b-a6cb-459a-8e8a-5296f2c753bf.png)

* DaemonSet: DaemonSets are an integral part of the Kubernetes cluster facilitating administrators to easily configure services (pods) across all or a subset of nodes.
* DaemonSet Reference: https://www.bmc.com/blogs/kubernetes-daemonset/

* Docker vs Docker compose vs docker swarm vs kubernetes
* stateless applications don’t “store” data. On the other hand, stateful applications require backing storage. For example, applications like the Cassandra, MongoDB, and MySQL databases require some type of persistent storage to survive service restarts.
* Reference: https://www.weka.io/blog/cloud-storage/stateless-vs-stateful-kubernetes/

* Taints and tolerations are a mechanism that allows you to ensure that pods are not placed on inappropriate nodes. Taints are added to nodes,
while tolerations are defined in the pod specification. When you taint a node, it will repel all the pods except those that have a toleration for that taint. A node can have one or many taints associated with it.
* Taints are a Kubernetes node property that enable nodes to repel certain pods. Tolerations are a Kubernetes pod property that allow a pod to be scheduled on a node with a matching taint.
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    env: test
spec:
  containers:
  - name: nginx
    image: nginx
    imagePullPolicy: IfNotPresent
  tolerations:
  - key: "example-key"
    operator: "Exists"
    effect: "NoSchedule"
 ```
* nodeSelector. nodeSelector is the simplest recommended form of node selection constraint. You can add the nodeSelector field to your Pod specification and specify the node labels you want the target node to have
* node affinity: It is similar to nodeSelector but provides more granular control over the selection process. Node affinity enables a conditional approach with logical operators in the matching process, while nodeSelector is limited to looking for exact label key-value pair matches. Node affinity is specified in the PodSpec using the nodeAffinity field in the affinity section.
```
apiVersion: v1
kind: Pod
metadata:
  name: with-node-affinity
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: topology.kubernetes.io/zone
            operator: In
            values:
            - antarctica-east1
            - antarctica-west1
      preferredDuringSchedulingIgnoredDuringExecution:
      - weight: 1
        preference:
          matchExpressions:
          - key: another-node-label-key
            operator: In
            values:
            - another-node-label-value
  containers:
  - name: with-node-affinity
    image: registry.k8s.io/pause:2.0
 ```
