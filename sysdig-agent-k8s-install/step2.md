## Create Service Account and Secret Key

`kubectl apply -f sysdig-agent-clusterrole.yaml`{{execute HOST1}}

`kubectl create serviceaccount sysdig-agent`{{execute HOST1}}

`kubectl create clusterrolebinding sysdig-agent --clusterrole=sysdig-agent --serviceaccount=default:sysdig-agent`{{execute HOST1}}


## Create secret key

Get agent access key and add it to ENV variable access_key.

"export agent_key=<your sysdig access key>"

Create secret key using the command

`kubectl create secret generic sysdig-agent --from-literal=access-key=$access_key`{{execute HOST1}}

