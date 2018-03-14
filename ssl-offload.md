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

For all incoming HTTPS connections, the load balancer service terminates the SSL connection and establishes a plain-text HTTP communication with the back-end server. CPU-intensive SSL handshakes and encryption/decryption tasks are shifted away from the back-end servers, allowing them to use all their CPU cycles for processing application traffic. 

An SSL certificate is required for the load balancer to perform SSL offload tasks. You may use a pre-existing SSL certificate or purchase a new one, and manage it through the [IBM Cloud Certificate Store ](https://control.softlayer.com/security/sslcerts). 
