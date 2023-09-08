---
title: Creating Containers
---

# Creating Containers
## The Openshift's hello-pod
* After being connected, switch to Cluster Console by selecting it in the drop menu located at the topbar:  

  ![cluster console](../img/create-obj-1.png)

* Run container image `hello-openshift` in a pod called example:  
  Go to Workloads > Pods and click Create Pod:    
  
  ![pod menu](../img/create-obj-2.png)

  Paste this code:  

  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    name: example
    labels:
      app: hello-openshift
    namespace: rahtidemotest # Must match your namespace / project name
  spec:
    containers:
      - name: hello-openshift
        image: openshift/hello-openshift
        ports:
          - containerPort: 8080
  ```
  
  ![create pod](../img/create-obj-3.png)

* Click Create

* Get the standard output of the container by going to Applications > Pods  
  Click on your Pod (should be `example`) and go to Logs tab.  
  You should see this:
  ![hello openshift](../img/pod-logs.png)


## Cleanup
On the pod page, click Action > Delete Pod