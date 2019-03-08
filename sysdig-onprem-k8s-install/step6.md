Install Datastores and Backend Components 
Create the datastore statefulsets (Elasticsearch and Cassandra). Elasticsearch and Cassandra are automatically set up with --replica=3 generating full clusters.

kubectl -n sysdigcloud create -f datastores/as_kubernetes_pods/manifests/cassandra/cassandra-service.yaml {{execute}}
kubectl -n sysdigcloud create -f datastores/as_kubernetes_pods/manifests/cassandra/cassandra-statefulset.yaml {{execute}}
kubectl -n sysdigcloud create -f datastores/as_kubernetes_pods/manifests/elasticsearch/elasticsearch-service.yaml {{execute}}
kubectl -n sysdigcloud create -f datastores/as_kubernetes_pods/manifests/elasticsearch/elasticsearch-statefulset.yaml {{execute}}

Create the datastore deployments (MySQL and Redis).

kubectl -n sysdigcloud create -f datastores/as_kubernetes_pods/manifests/mysql/mysql-deployment.yaml {{execute}}
kubectl -n sysdigcloud create -f datastores/as_kubernetes_pods/manifests/redis/redis-deployment.yaml {{execute}}
The  mysql-deployment.yaml by default employs a local non-persistent volume (emptyDir) that is only for use in non-production environments. If you reboot a cluster with an emptyDir, all data that was MySQL will be lost. In production environments, the emptyDir section should be commented out, and replaced with the persistent volumes of your choosing. (Example snippets are included in the manifest.) 

Wait until datastore pods are in ready state., then deploy the backend deployment sets (worker, collector and API). Pause for 60 seconds after creating the API deployment.

kubectl -n sysdigcloud create -f sysdigcloud/sdc-api.yaml {{execute}}
kubectl -n sysdigcloud create -f sysdigcloud/sdc-collector.yaml {{execute}}
kubectl -n sysdigcloud create -f sysdigcloud/sdc-worker.yaml {{execute}}

