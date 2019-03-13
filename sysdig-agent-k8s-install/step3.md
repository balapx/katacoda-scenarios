## Create secret key

1. Get the agent access key and add it to the environment variable access_key. 

2. Create a secret key using the command

`kubectl create secret generic sysdig-agent --from-literal=access-key=$access_key`{{execute HOST1}}

## Enable Kube State Metrics and Other Configmap Edits

3. Edit sysdig-agent-configmap.yaml to 
    - Uncomment the line: collector and add collector-staging.sysdigcloud.com
    - uncomment the line: new_k8s: true
    - uncomment the line: k8s_cluster_name: and add your cluster name

`vi sysdig-agent-configmap.yaml`{{execute HOST1}}

4. Aplly the configmap changes

`kubectl apply -f sysdig-agent-configmap.yaml`{{execute HOST1}}

## Edit the Daemonset and Deploy the Agents

5. Apply the daemonset-v2.yaml

`kubectl apply -f sysdig-agent-daemonset-v2.yaml`{{execute HOST1}}
