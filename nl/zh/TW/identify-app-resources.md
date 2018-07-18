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

# 識別應用程式資源

識別應用程式的資源，例如原始儲存區及性能檢查機制。
 
1. 導覽至**原始儲存區**區段，然後按一下**建立儲存區**，來定義新的原始儲存區。 

   原始儲存區是將應用程式遞送至用戶端的伺服器資源。 
   
2. 將名稱指派給「原始儲存區」，然後選取先前定義的性能檢查機制。將應用程式伺服器新增為「原始」。您可以按一下**新增原始**，來新增一個以上的「原始」。 

   **附註：**如果應用程式伺服器座落於本端負載平衡器（例如 IBM Cloud Load Balancer）後面，則將負載平衡器的 FQDN 或虛擬 IP 新增為「原始」，而不是新增個別伺服器。 
   
3. 按一下**佈建資源**來完成「原始儲存區」的建立。  

   <img src="images/Reliability6.png" alt="圖片" style="width: 300px;"/>
   
   「原始儲存區」起始會顯示為**不正常**。在系統順利完成性能檢查之後，其狀態將變更為**正常**。您可能需要重新整理瀏覽器，才能看到狀態變更。 
   
   <img src="images/Reliability9.png" alt="圖片" style="width: 300px;"/>
   
   **附註：**如果您在「原始儲存區」內有多個原始，則使用正常原始臨界值，來指定在將儲存區宣佈為正常之前必須正常的原始數目下限。 
   
4. 定義與您具有的應用程式伺服器陣列一樣多的原始儲存區。這些伺服器陣列可能在相同或不同的地理區域內。在我們的範例中，我們將建立兩個原始儲存區，代表美國西岸及東岸中的應用程式伺服器陣列。 

   <img src="images/Reliability10.png" alt="圖片" style="width: 300px;"/>
