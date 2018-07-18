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

# Anwendungsressourcen angeben

Geben Sie die Anwendungsressourcen an, zum Beispiel Ursprungspools und Mechanismen für die Statusprüfung.
 
1. Navigieren Sie zum Abschnitt **Ursprungspools** und klicken Sie auf **Pool erstellen**, um einen neuen Ursprungspool zu definieren. 

   Ursprungspools sind Serverressourcen, von denen Anwendungen für Clients bereitgestellt werden. 
   
2. Weisen Sie dem Ursprungspool einen Namen zu und wählen Sie die davor definierte Methode für die überprüfen aus. Fügen Sie den Anwendungsserver als Ihren Ursprung hinzu. Sie können weitere Ursprünge durch Klicken auf **Ursprung hinzufügen** hinzufügen. 

   **HINWEIS:** Wenn sich die Anwendungsserver hinter einer lokalen Lastausgleichsfunktion wie zum Beispiel IBM Cloud Load Balancer befinden, fügen Sie den vollständig qualifizierten Domänennamen oder die virtuelle IP Ihrer Lastausgleichsfunktion als Ursprung hinzu, anstatt einzelne Server hinzuzufügen. 
   
3. Klicken Sie auf **Ressource bereitstellen**, um die Erstellung des Ursprungspools auszuführen.  

   <img src="images/Reliability6.png" alt="Zeichnung" style="width: 300px;"/>
   
   Für den Ursprungspool wird zunächst **Nicht ordnungsgemäß** angezeigt. Nach einer erfolgreichen Statusprüfung durch das System ändert sich der Status zu **In einwandfreiem Zustand**. Möglicherweise müssen Sie den Browser aktualisieren, damit die Statusänderung angezeigt wird. 
   
   <img src="images/Reliability9.png" alt="Zeichnung" style="width: 300px;"/>
   
   **HINWEIS:** Falls im Ursprungspool mehrere Ursprungsserver vorhanden sind, verwenden Sie den Schwellenwert für Ursprungsserver in einwandfreiem Zustand, um die Mindestanzahl der Ursprungsserver anzugeben, die sich in einwandfreiem Zustand befinden müssen, damit der Pool zu einem Pool in einwandfreiem Zustand erklärt werden kann. 
   
4. Stellen Sie beim Definieren der Ursprungspools sicher, dass die Anzahl der definierten Ursprungspools mit der Anzahl der vorhandenen Anwendungs-Farms übereinstimmt. Diese Farms können sich in derselben oder einer anderen geografischen Region befinden. Im vorliegenden Beispiel werden zwei Ursprungspools erstellt, die jeweils eine Anwendungs-Farm an der Ostküste und der Westküste der USA darstellen. 

   <img src="images/Reliability10.png" alt="Zeichnung" style="width: 300px;"/>
