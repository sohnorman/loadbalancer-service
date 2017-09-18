---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# SSL Offload

For all incoming HTTPS connections, the load balancer service terminates SSL connection and establishes plain-text HTTP communication with the back-end server. The back-end servers are thus offloaded from performing CPU-intensive SSL handshakes and encryption/decryption tasks, so they can use all their CPU cycles for processing application traffic. An SSL certificate is required for the load balancer to perform SSL offload tasks. You may use a pre-existing SSL certificate or purchase a new one, and manage it through the [Bluemix/Softlayer Certificate Store ](https://control.softlayer.com/security/sslcerts). 

**NOTE:** The load balancer service supports TLS version 1.2 with SSL offload. It does not support SSLv3 due to its vulnerabilities. The SSL cipher list can not be customized at this time. 
