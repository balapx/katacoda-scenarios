Confirm Installation

Once the installation has been completed, your output should look similar (please note that the below output is an example):

`kubectl get pods -n sysdigcloud`{{execute HOST1}}
 
`kubectl -n sysdigcloud get services`{{execute HOST1}}

`kubectl -n sysdigcloud describe service sysdigcloud-api`{{execute HOST1}}
 
`kubectl -n sysdigcloud describe service sysdigcloud-collector`{{execute HOST1}}

