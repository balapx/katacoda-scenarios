## Create secret key

Get agent access key and add it to ENV variable access_key.

"export agent_key=<your sysdig access key>"

Create secret key using the command

`kubectl create secret generic sysdig-agent --from-literal=access-key=$access_key`{{execute HOST1}}

## Enable Kube State Metrics and Other Configmap Edits

Edit sysdig-agent-configmap.yaml to 
    - uncomment the line: collector and add collector-staging.sysdigcloud.com
    - uncomment the line: new_k8s: true
    - uncomment the line: k8s_cluster_name: and add your cluster name

`vi sysdig-agent-configmap.yaml`{{execute HOST1}}

Apply the configmap changes

`kubectl apply -f sysdig-agent-configmap.yaml`{{execute HOST1}}

## Edit the Daemonset and Deploy the Agents

Apply the daemonset-v2.yaml

`kubectl apply -f sysdig-agent-daemonset-v2.yaml`{{execute HOST1}}
