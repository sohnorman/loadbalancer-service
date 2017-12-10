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


# Getting Started

To get started with the IBM Cloud Load Balancer service, select **Network > Load Balancers > IBM Cloud Load Balancer** from the IBM Cloud catalog, then perform the following procedure:

1. Select your data center and review the service plan. Click **Next**.
2. Select the subnet to which you'd like to deploy your load balancer. Your load balancer service instance will have one of its network interfaces on this subnet. Ensure that your application servers are either on this subnet or reachable from this subnet. If necessary, enable VLAN spanning. Click **Next**.
3. Define your basic service parameters, such as the name, description, front-end and back-end application protocols and ports, and load balancing method. You may define a maximum of two protocols during the initial service creation. You may define up to ten protocols after the service is created. You must also use a unique front-end port. Click **Next**.
4. Adjust your health check parameters if desired, otherwise use the default settings. Click **Next**.
5. Associate one or more server instances behind your load balancer. You'll only see server instances local to your data center. Click **Next**.
6. Review the summary page then click **Create**. 


The summary page displays the load balancer service instance you just created. Note the **Status** field. A status of `Offline` implies the load balancer is not in service. No new configurations can be made and no load balancing service can be provided until its status changes to `Online`. You may need to refresh your screen to see the current status.
 
Clicking on the service name on this page takes you to the service overview page. You can navigate to the **Protocols**, **Health Checks** and **Server Instances** tabs to edit your existing configuration.
