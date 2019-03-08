Configure Access for Connectivity to the Cluster 
To permit incoming connections to the Sysdig API and collector deployments, you can either create a Kubernetes NodePort (for test environments only) or a LoadBalacer service (recommended). 

LoadBalancer 
When creating a service, you have the option of creating a cloud network load balancer. This provides an externally accessible IP address that sends traffic to the correct port on your cluster nodes (provided your cluster runs in a supported environment and is configured with the correct cloud load balancer provider package).

You can create a cloud-based LoadBalancer service for the Sysdig API and collector using kubectl and the templates in the sysdigcloud folder.
Run the command: 

`kubectl -n sysdigcloud create -f sysdigcloud/api-loadbalancer-service.yaml` {{execute}}

`kubectl -n sysdigcloud create -f sysdigcloud/collector-loadbalancer-service.yaml` {{execute}}
