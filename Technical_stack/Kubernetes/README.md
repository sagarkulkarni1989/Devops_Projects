* Kunernetes architecture

![image](https://user-images.githubusercontent.com/46215433/227093320-0d78b681-7e9b-4a6b-bef4-2c8402312c71.png)

* Minikube installation
* Service account:A service account provides an identity for processes that run in a Pod, and maps to a ServiceAccount object. It is used to authenticate machine level processes to get access to our Kubernetes cluster. The API server is responsible for such authentication to the processes running in the pod
* User Account: It is used to allow us, humans, to access the given Kubernetes cluster. Any user needs to get authenticated by the API server to do so. A user account can be an admin or a developer who is trying to access the cluster level resources.
      

* init container and sidecar container : https://blog.knoldus.com/sidecar-container-vs-init-container-in-kubernetes/
* configmap, Secrets and Custom Resource definition(CRD)
* Different between podman and docker engine
* How to get node external IP on to Pod?
* Pod afinity and pod anti afinity 
* Adapter container 
* How to setup scalable jenkins on top of kubernetes cluster 
* Persistent volume type: NFS in k8s 
* Network policies 
* Auto scaling of pods based on CPU utlization using Horizantal pod autoscaler
* Deployment strategies
* Docker vs Docker compose vs docker swarm vs kubernetes
* statefulset, stateless and daemonset 
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
