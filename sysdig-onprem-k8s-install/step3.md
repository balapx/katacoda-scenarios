##  Enter and Deploy Your Quay Pull Secret 

A specific Quay pull secret is sent via email with your license key when you purchase the Sysdig on-premises platform for Kubernetes.

1. Edit the file sysdigcloud/pull-secret.yaml and change the place holder <PULL_SECRET> with the provided pull secret.

2. Deploy the pull secret object by running the command: 

`kubectl -n sysdigcloud create -f sysdigcloud/pull-secret.yaml`{{execute HOST1}}
