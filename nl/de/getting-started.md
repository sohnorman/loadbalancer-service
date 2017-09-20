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


# Einführung

Wählen Sie für den Einstieg in den IBM Bluemix-Service für die Lastausgleichsfunktion **Netz > Lastausgleichsfunktionen > IBM Bluemix-Lastausgleichsfunktion** in Bluemix Catalog aus und führen Sie anschließend die folgende Prozedur aus: 

1. Wählen Sie Ihr Rechenzentrum aus und überprüfen Sie den Serviceplan. Klicken Sie auf **Weiter**. 
2. Wählen Sie das Teilnetz aus, für das Sie die Lastausgleichsfunktion implementieren möchten. Die Instanz des Service für die Lastausgleichsfunktion verfügt über eine der Netzschnittstellen in diesem Teilnetz. Stellen Sie sicher, dass die Anwendungsserver entweder in diesem Teilnetz oder aus diesem Teilnetz erreichbar sind. Aktivieren Sie bei Bedarf das VLAN-Spanning. Klicken Sie auf **Weiter**. 
3. Definieren Sie die Basisserviceparameter, wie zum Beispiel Name, Beschreibung, Protokolle und Ports für Front-End- und Back-End-Anwendungen oder die Lastausgleichsmethode. Während der erstmaligen Serviceerstellung können Sie maximal zwei Protokolle definieren. Sie können bis zu zehn Protokolle definieren, wenn der Service erstellt ist. Sie müssen auch einen eindeutigen Front-End-Port verwenden. Klicken Sie auf **Weiter**. 
4. Passen Sie bei Bedarf die Parameter für die Statusprüfung an; verwenden Sie andernfalls die Standardeinstellungen. Klicken Sie auf **Weiter**. 
5. Ordnen Sie mindestens eine Serverinstanz hinter der Lastausgleichsfunktion zu. Es werden nur Serverinstanzen angezeigt, die sich lokal im Rechenzentrum befinden. Klicken Sie auf **Weiter**. 
6. Überprüfen Sie die Übersichtsseite und klicken Sie auf **Erstellen**.  


Auf der Übersichtsseite wird die Instanz des Service für die Lastausgleichsfunktion angezeigt, die Sie soeben erstellt haben. Beachten Sie das Feld **Status**. Die Statusangabe `Offline` gibt an, dass die Lastausgleichsfunktion nicht aktiv ist. Es können erst neue Konfigurationen vorgenommen und ein Service für die Lastausgleichsfunktion bereitgestellt werden, wenn sich der Status in `Online` geändert hat. Möglicherweise müssen Sie die Anzeige aktualisieren, um den aktuellen Status anzuzeigen. 
 
Wenn Sie auf den Servicenamen auf dieser Seite klicken, wechseln Sie zur Übersichtsseite des Service. Sie können zu den Registerkarten **Protokolle**, **Statusprüfungen** und **Serverinstanzen** navigieren, um die vorhandene Konfiguration zu bearbeiten. 
