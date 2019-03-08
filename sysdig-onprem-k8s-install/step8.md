Confirm Installation

Once the installation has been completed, your output should look similar (please note that the below output is an example):

kubectl get pods -n sysdigcloud {{execute}}
 
kubectl -n sysdigcloud get services {{execute}}

kubectl -n sysdigcloud describe service sysdigcloud-api {{execute}}
 
kubectl -n sysdigcloud describe service sysdigcloud-collector {{execute}}

