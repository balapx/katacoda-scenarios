Install Components 
Confirm Storage Classes and Edit storageClassName Parameters
If you are using EKS or GKE, default storage classes are provided; check for them in step 1. In other environments, you may need to create a storage class (step 2).  Finally, enter the storageClassName in the appropriate .yaml files, as detailed in step 3. . 

Verify whether a storage class has been created, by running the command: 

kubectl get storageclass {{execute}}

If no storage class has been defined, create a manifest for one, and then deploy it. 
For example, a manifest could be named sysdigcloud-storageclass.yaml and contain the following contents (for a storage class using GP2 volumes in AWS):

apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: gp2
  annotations:
    storageclass.beta.kubernetes.io/is-default-class: "true"
  labels:
    kubernetes.io/cluster-service: "true"
    addonmanager.kubernetes.io/mode: EnsureExists
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp2
Now run the command: 

kubectl create -f sysdigcloud-storageclass.yaml {{execute}}

Using either the existing storage class name from step 1, or the storage class name defined in step 2, edit the storageClassName in the following .yaml files: 

datastores/as_kubernetes_pods/manifests/cassandra/cassandra-statefulset.yaml {{execute}}
datastores/as_kubernetes_pods/manifests/elasticsearch/elasticsearch-statefulset.yaml {{execute}}
