The ConfigMap (config.yaml) is populated with information about usernames, passwords, SSL/TLS certs, and various application-specific settings. 
See Sysdig Install with Kubernetes 1.9+#Making Configuration Changes for the kubectl format to use. 

Apart from the license key, the default config.yaml can be deployed as-is in a test environment, using the default component passwords and settings. 
You would edit this file with enterprise-specific information in a production deployment. 

Edit the sysdigcloud/config.yaml file and find the parameter  sysdigcloud.license: "". 
Enter the key that was emailed to you. 

It is recommended to edit the file to set the JVM options for Cassandra, Elasticsearch, and API, worker, and collector as well.  

To use the AWS implicit key, edit the JVM options as described in AWS: Integrate AWS Account and CloudWatch Metrics (Optional). 
Create the namespace and deploy config.yaml by running the following commands: 

`kubectl create namespace sysdigcloud` {{execute}}

`kubectl -n sysdigcloud create -f sysdigcloud/config.yaml` {{execute}}
