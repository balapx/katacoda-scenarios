## Create a  Service Account for the Sysdig Agent

`kubectl apply -f sysdig-agent-clusterrole.yaml`{{execute HOST1}}

`kubectl create serviceaccount sysdig-agent`{{execute HOST1}}

`kubectl create clusterrolebinding sysdig-agent --clusterrole=sysdig-agent --serviceaccount=sysdig-agent`{{execute HOST1}}
