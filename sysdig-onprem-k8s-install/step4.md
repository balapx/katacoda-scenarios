## Set Up SSL/TLS Connectivity to the Backend 

SSL/TLS communication is used between user browsers and the Sysdig API server(s), and optionally between the Sysdig agent and the collectors. 
To set this up, you must: 

- Use an existing SSL/TLS certificate and key or
- Create a self-sign certificate and key 

To create a self-signed cert: 

`openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 -subj "/C=US/ST=CA/L=SanFrancisco/O=ICT/CN=onprem.sysdigcloud.com" -keyout server.key -out server.crt`{{execute HOST1}}

Create a Kubernetes secret for the cert: 

`kubectl -n sysdigcloud create secret tls sysdigcloud-ssl-secret --cert=server.crt --key=server.key`{{execute HOST1}}

