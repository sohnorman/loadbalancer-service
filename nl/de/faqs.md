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

# Häufig gestellte Fragen (FAQs)

Dieser Abschnitt enthält Antworten auf einige häufig gestellte Fragen zum IBM Cloud Load Balancer-Service.

## Wie viele Lastausgleichsoptionen stehen in {{site.data.keyword.BluSoftlayer_notm}} zur Verfügung?

Einen detaillierten Vergleich der IBM Load Balancer-Angebote finden Sie in [Lastausgleichsfunktionen erkunden](https://dev-console.bluemix.net/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers).

## Kann für die Lastausgleichsfunktion ein anderer DNS-Name verwendet werden?

Der automatisch zugeordnete DNS-Name für die Lastausgleichsfunktion kann nicht angepasst werden, Sie können jedoch einen CNAME-Datensatz (CNAME = kanonischer Name) hinzufügen, der vom bevorzugten DNS-Namen auf den automatisch zugeordneten DNS-Namen der Lastausgleichsfunktion verweist. Beispiel: Die Nummer Ihres Kontos lautet 123456, die Lastausgleichsfunktion ist im Rechenzentrum "dal09" bereitgestellt, der Name der Lastausgleichsfunktion lautet "myapp" und der automatisch zugeordnete DNS-Name der Lastausgleichsfunktion lautet "myapp-123456-dal09.lb.bluemix.net". Ihr bevorzugter DNS-Name lautet "www.myapp.com". Sie können einen CNAME-Datensatz zuordnen (über den DNS-Provider, den Sie zur Verwaltung von myapp.com verwenden), der von "www.myapp.com" auf den DNS-Namen "myapp-12345-dal09.lb.bluemix.net" der Lastausgleichsfunktion verweist.

## Wie viele virtuelle Ports können mit dem Service für die Lastausgleichsfunktion maximal definiert werden?

Beim erstmaligen Erstellen eines neuen Service für die Lastausgleichsfunktion können Sie bis zu zwei virtuelle Ports definieren. Nach der Erstellung des Service können weitere virtuelle Ports definiert werden. Maximal sind 10 virtuelle Ports zulässig. 

## Wie viele Recheninstanzen können der Lastausgleichsfunktion maximal zugeordnet werden?

50.

## Wie lauten die Standardeinstellungen und zulässigen Werte für die unterschiedlichen Parameter für die Statusprüfung?

Die Standardeinstellungen und zulässigen Werte werden nachfolgend aufgelistet:

* **Intervall für Statusprüfung:** Die Standardeinstellung ist 5 Sekunden, der zulässige Bereich liegt zwischen 2 und 60 Sekunden.
* **Antwortzeitlimit für Statusprüfung:** Die Standardeinstellung ist 2 Sekunden, der zulässige Bereich liegt zwischen 1 und 59 Sekunden.
* **Maximale Wiederholungsversuche:** Standardeinstellung ist 2 Wiederholungsversuch, der gültige Bereich liegt zwischen 1 und 10 Wiederholungsversuchen.

**HINWEIS:** Der Antwortzeitlimitwert für die Statusprüfung muss immer kleiner als der Intervallwert für die Statusprüfung sein. 

## Kann ich mit diesem Service Recheninstanzen verwenden, die sich in fernen Rechenzentren befinden? 

Es wird empfohlen, den Lastenausgleichsservice und die Recheninstanzen lokal in demselben Rechenzentrum auszuführen. In der grafischen Benutzerschnittstelle des Service für die Lastausgleichsfunktion werden Recheninstanzen von anderen fernen Rechenzentren nicht angezeigt. In der grafischen Benutzerschnittstelle sind jedoch Recheninstanzen von weiteren Rechenzentren in derselben Stadt eingeschlossen (zum Beispiel Rechenzentren, deren Name dieselben drei ersten Buchstaben aufweisen, wie beispielsweise DALxx). Sie können die API-Schnittstelle jedoch dazu verwenden, um Recheninstanzen von einem fernen Rechenzentrum hinzuzufügen. 

## Welche TLS-Version wird mit der SSL-Auslagerung unterstützt?

Vom IBM Cloud Load Balancer-Service wird TLS 1.2 mit SSL-Terminierung unterstützt. 

In der folgenden Liste werden die unterstützten Verschlüsselungen (in der Reihenfolge ihrer Priorität) aufgeführt:  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## Wie viele Instanzen des Service für die Lastausgleichsfunktion kann ich für mein Konto erstellen? 

Derzeit können Sie bis zu 20 Serviceinstanzen erstellen. Falls Sie weitere Instanzen benötigen, wenden Sie sich an den IBM Support. 

## Kann der IBM Cloud Load Balancer-Service mit VMWare verwendet werden? 

Virtuelle VMware-Maschinen, denen portierbare private SoftLayer-Adressen zugeordnet sind, können als Back-End-Server für die Lastausgleichsfunktion angegeben werden. Diese Funktion ist derzeit nur bei Verwendung der API verfügbar, nicht jedoch in der Webbenutzerschnittstelle. Portierbare private IPs, die mithilfe der API hinzugefügt wurden, werden in der grafischen Benutzerschnittstelle mit der Kennzeichnung 'Unbekannt' angezeigt, da sie nicht von SoftLayer zugewiesen werden. Beachten Sie, dass diese Art der Konfiguration auch mit anderen Hypervisoren wie Xen und KVM verwendet werden kann.

Virtuelle VMware-Maschinen, denen keine SoftLayer-Adressen zugewiesen wurden (zum Beispiel VMWare NSX-Netze), können nicht direkt als Back-End-Server für die Lastausgleichsfunktion hinzugefügt werden. Abhängig von der Konfiguration kann es möglich sein, einen Vermittler zu konfigurieren, zum Beispiel eine private SoftLayer-Adresse als Back-End-Server für die Lastausgleichsfunktion (hierbei müssen die mit den virtuellen Maschinen verbundenen Server mit den Netzen verbunden sein, die von VMware NSX verwaltet werden).

## Angenommen, ich verwende für die Bereitstellung der Lastausgleichsfunktion ein öffentliches VLAN unter meinem Konto und für das öffentliche VLAN ist eine Firewall eingerichtet, welche Konfigurationen sind für die Firewall erforderlich, damit der Load Balancer-Service verwendet werden kann?

TCP-Port 56501 wird zur Verwaltung verwendet. Stellen Sie sicher, dass der Datenverkehr zu diesem Port sowie die Ports der Anwendung nicht von Ihrer Firewall blockiert werden, da die Bereitstellung der Lastausgleichsfunktion sonst fehlschlägt.

## Was ist zu tun, wenn der Fehler 'This SoftLayer account is not linked to any Bluemix account' (Dieses SoftLayer-Konto ist mit keinem Bluemix-Konto verknüpft) angezeigt wird?

Stellen Sie sicher, dass Ihr SoftLayer-Konto mit Ihrem Bluemix-Konto verknüpft ist. Weitere Anweisungen hierzu finden Sie unter [SoftLayer-Link](https://console.bluemix.net/docs/account/softlayerlink.html#switching-to-ibmid).
