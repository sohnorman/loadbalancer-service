---



copyright:
  years: 2017
lastupdated: "2018-06-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 识别您的应用程序资源

识别您的应用程序资源，例如源池和运行状况检查机制。
 
1. 导航到**源池**部分，并单击**创建池**以定义新的源池。 

   源池是向客户机提供应用程序的服务器资源。 
   
2. 向源池分配名称，并选择先前定义的运行状况检查机制。将您的应用程序服务器添加为源。您可以通过单击**添加源**来添加一个或多个源。 

   **注：**如果应用程序服务器位于本地负载均衡器（例如 IBM Cloud Load Balancer）之后，那么将您的负载均衡器的 FQDN 或虚拟 IP 添加为源，而不是添加您的单独服务器。 
   
3. 单击**供应资源**以完成源池的创建。  

   <img src="images/Reliability6.png" alt="图样" style="width: 300px;"/>
   
   源池起初将显示为**非正常运行状况**。系统成功完成运行状况检查后，其状态将更改为**正常运行状况**。您可能需要刷新浏览器以查看状态更改。 
   
   <img src="images/Reliability9.png" alt="图样" style="width: 300px;"/>
   
   **注：**如果您的源池中有多个源，那么使用正常运行状况的源阈值来指定必须至少有多少个源运行状况正常才可以声明池运行状况正常。 
   
4. 定义与您拥有的应用程序场数量相同的源池。这些场可能位于相同或不同的地理区域。在我们的示例中，我们将创建两个源池来表示美国西海岸和东海岸的应用程序场。 

   <img src="images/Reliability10.png" alt="图样" style="width: 300px;"/>
