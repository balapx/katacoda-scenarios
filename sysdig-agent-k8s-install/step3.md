## Enable Kube State Metrics and Other Configmap Edits

2. Edit sysdig-agent-configmap.yaml to 
    - Uncomment the line: collector and add collector-staging.sysdigcloud.com
    - uncomment the line: new_k8s: true
    - uncomment the line: k8s_cluster_name: and add your cluster name

3. Aplly the configmap changes

`kubectl apply -f sysdig-agent-configmap.yaml`{{execute HOST1}}

## Edit the Daemonset and Deploy the Agents

1. Edit sysdig-agent-daemonset-v2.yaml to uncomment the line: serviceAccount: sysdig-agent.

`vi sysdig-agent-daemonset-v2.yaml`{{execute HOST1}}

2. Apply the daemonset-v2.yaml
`kubectl apply -f sysdig-agent-daemonset-v2.yaml`{{execute HOST1}}
