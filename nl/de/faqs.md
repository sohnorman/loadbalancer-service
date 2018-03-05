---

copyright:
  years: 2017
lastupdated: "2017-11-02"

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

## Wieviele Lastausgleichsoptionen stehen in {{site.data.keyword.BluSoftlayer_notm}} zur Verfügung?

Einen detaillierten Vergleich der IBM Load Balancer-Angebote finden Sie in [Lastausgleichsfunktionen erkunden](https://dev-console.bluemix.net/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers).

## Kann für die Lastausgleichsfunktion ein anderer DNS-Name verwendet werden?

Der automatisch zugeordnete DNS-Name für die Lastausgleichsfunktion kann nicht angepasst werden, Sie können jedoch einen CNAME-Datensatz (CNAME = kanonischer Name) hinzufügen, der vom bevorzugten DNS-Namen auf den automatisch zugeordneten DNS-Namen der Lastausgleichsfunktion verweist. Beispiel: Die Nummer Ihres Kontos lautet 123456, die Lastausgleichsfunktion ist im Rechenzentrum "dal09" bereitgestellt, der Name der Lastausgleichsfunktion lautet "myapp" und der automatisch zugeordnete DNS-Name der Lastausgleichsfunktion lautet "myapp-123456-dal09.lb.bluemix.net". Ihr bevorzugter DNS-Name lautet "www.myapp.com". Sie können einen CNAME-Datensatz zuordnen (über den DNS-Provider, den Sie zur Verwaltung von myapp.com verwenden), der von "www.myapp.com" auf den DNS-Namen "myapp-12345-dal09.lb.bluemix.net" der Lastausgleichsfunktion verweist.

## Wie viele virtuelle Ports können mit dem Service für die Lastausgleichsfunktion maximal definiert werden?

Beim erstmaligen Erstellen eines neuen Service für die Lastausgleichsfunktion können Sie bis zu zwei virtuelle Ports definieren. Nach der Erstellung des Service können weitere virtuelle Ports definiert werden. Maximal sind 10 virtuelle Ports zulässig. 

## Wie viele Recheninstanzen können der Lastausgleichsfunktion maximal zugeordnet werden?

50.

## Kann ich eine rein interne private Lastausgleichsfunktion erstellen, auf die nur von internen Clients zugegriffen werden kann?  

Derzeit ist dies nicht möglich. Dem Service, der von IBM Cloud Load Balancer gehostet wird, ist ein vollständig qualifizierter Domänennamen zugewiesen, auf den vom öffentlichen Internet aus zugegriffen werden kann.  

## Wie lauten die Standardeinstellungen und zulässigen Werte für die unterschiedlichen Parameter für die Statusprüfung?

Die Standardeinstellungen und zulässigen Werte werden nachfolgend aufgelistet:

* **Intervall für Statusprüfung:** Die Standardeinstellung ist 5 Sekunden, der zulässige Bereich liegt zwischen 2 und 60 Sekunden.
* **Antwortzeitlimit für Statusprüfung:** Die Standardeinstellung ist 2 Sekunden, der zulässige Bereich liegt zwischen 1 und 59 Sekunden.
* **Maximale Neuversuche:** Die Standardeinstellung ist 2 Neuversuche, der zulässige Bereich liegt zwischen 1 und 10 Neuversuchen.

**Hinweis:** Der Wert für das Antwortzeitlimit für die Statusprüfung muss immer niedriger als der interne Wert für die Statusprüfung sein. 

## Kann ich mit diesem Service Recheninstanzen verwenden, die sich in fernen Rechenzentren befinden? 

Es wird empfohlen, dass sich der Service für die Lastausgleichsfunktion und die Recheninstanzen lokal in demselben Rechenzentrum befinden. In der grafischen Benutzerschnittstelle des Service für die Lastausgleichsfunktion werden Recheninstanzen von anderen fernen Rechenzentren nicht angezeigt. In der grafischen Benutzerschnittstelle sind jedoch die Recheninstanzen aus anderen Rechenzentren in derselben Stadt eingeschlossen (also Rechenzentren, deren Namen die ersten drei Buchstaben gemeinsam haben, wie zu zum Beispiel GERxx). In der API-Schnittstelle können Sie jedoch Recheninstanzen in einem beliebigen fernen Rechenzentrum hinzufügen. 

## Welche TLS-Version wird mit der SSL-Auslagerung unterstützt? Welche Verschlüsselungen werden unterstützt?

Vom IBM Cloud Load Balancer-Service wird TLS 1.2 mit SSL-Terminierung unterstützt.  

In der folgenden Liste werden die unterstützten Verschlüsselungen (in der Reihenfolge ihrer Priorität) aufgeführt:  

* ECDHE-RSA-AES256-GCM-SHA384 
* ECDHE-RSA-AES256-SHA384 
* DHE-RSA-AES256-GCM-SHA384 
* DHE-RSA-AES256-SHA256 
* AES256-GCM-SHA384 
* AES256-SHA256 
* ECDHE-RSA-AES128-GCM-SHA256 
* ECDHE-RSA-AES128-SHA256 
* DHE-RSA-AES128-GCM-SHA256 
* DHE-RSA-AES128-SHA256 
* AES128-GCM-SHA256 
* AES128-SHA256 

## Kann ich meine SSL-Verschlüsselungsliste anpassen?

Derzeit ist dies nicht möglich.

## Wie viele Instanzen des Service für die Lastausgleichsfunktion kann ich für mein Konto erstellen? 

Derzeit können Sie bis zu 20 Serviceinstanzen erstellen. Wenn Sie mehr Instanzen benötigen, wenden Sie sich an den IBM Support. 

## Kann Load Balancer as a Service mit VMWare verwendet werden? 

Virtuelle VMware-Maschinen, denen portierbare private SoftLayer-Adressen zugewiesen sind, können als Back-End-Server für die Lastausgleichsfunktion angegeben werden. Dieses Feature ist zurzeit nur über die API verfügbar, nicht über die Webbenutzerschnittstelle (GUI). Portierbare private IP-Adressen, die über die API hinzugefügt werden, werden in der GUI als "unbekannt" angezeigt, da sie von SoftLayer nicht zugewiesen werden. Beachten Sie, dass diese Art der Konfiguration auch mit anderen Hypervisoren wie Xen und KVM verwendet werden kann.

Virtuelle VMware-Maschine, denen Adressen zugewiesen sind, bei denen es sich nicht um SoftLayer-Adressen handelt (wie bei VMware NSX-Netzen), können nicht direkt als Back-End-Server zur Lastausgleichsfunktion hinzugefügt werden. Abhängig von der Konfiguration kann es jedoch möglich sein, ein Vermittlersystem, wie z. B. ein NSX-Gateway, mit einer privaten SoftLayer-Adresse als Back-End-Server für die Lastausgleichsfunktion zu konfigurieren (wobei die eigentlichen Server VMs sind, die mit einem oder mehreren von VMware NSX verwalteten Netzen verbunden sind).

## Angenommen, ich verwende für die Bereitstellung der Lastausgleichsfunktion ein öffentliches VLAN unter meinem Konto und für das öffentliche VLAN ist eine Firewall eingerichtet, welche Konfigurationen sind für die Firewall erforderlich, damit der Load Balancer-Service verwendet werden kann? 

TCP-Port 56501 wird zur Verwaltung verwendet. Stellen Sie sicher, dass der Datenverkehr an diesem Port und an den Ports Ihrer Anwendung nicht durch die Firewall blockiert wird, da andernfalls die Load Balancer-Bereitstellung fehlschlägt.

