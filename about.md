---

copyright:
  years: 2017
lastupdated: "2018-03-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# About

The IBM Cloud Load Balancer service helps customers improve availability of their business-critical applications by distributing traffic among multiple application server instances, and by forwarding traffic to healthy instances only.

## Overview of Features
The IBM Cloud Load Balancer Service offers the following features:

* Public (internet-facing) load balancer
	* Publicly-accessible service through its fully qualified domain name (FQDN)
	* Backend server instances on private subnets
* Internal load balancer
	* Privately-accessible service through its fully qualified domain name (FQDN)
	* Client requests are routed over the private network
	* Backend server instances on private subnets
* Basic load balancing
	* Traffic distribution based on Layer-4 application port information
	* Support for HTTP, HTTPS and TCP-based applications 
	* Variety of load balancing methods such as round-robin (RR), weighted round-robin, and least connections
	* Load balancing among virtual server and bare metal compute instances residing locally within a data center
* Server health checks
	* Periodic monitoring of server health to ensure that traffic is forwarded to healthy servers only 
	* Layer-4 health checks for TCP ports and Layer-7 health checks for HTTP port 
* SSL offload
	* Termination of incoming SSL (HTTPS) traffic using plain-text HTTP communication with backend servers
* Advanced traffic management
	* Client stickiness (session persistence)
	* Maximum connections per virtual port
* Easy management using intuitive graphical interface and API
* Built-in reliability 
* Usage-based pricing 
* Monitoring
    * Monitors the Throughput, Active Connections and Connection Rate metrics for HTTP, HTTPS, and TCP protocols over user specified time intervals. Refer to [Monitoring Metrics](monitoring-metrics.html) for additional details.