---

copyright:
  years: 2017
lastupdated: "2018-05-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Neuerungen

Informieren Sie sich über neue und aktualisierte Funktionen in IBM Cloud Load Balancer.

## April 2018
### Horizontale Skalierung
Die vertikale Skalierung von IBM Cloud Load Balancer wird jetzt automatisch durchgeführt, wenn die Last zunimmt oder abnimmt. Wenn die Lastausgleichsfunktion erstellt wird, startet sie mit zwei Appliances, die Anzahl der Appliances kann jedoch erhöht werden (derzeit auf bis zu 16), sobald vom Überwachungssystem eine Zunahme der Last erkannt wird. Die IP-Adressen der einzelnen aktiven Appliances werden als DNS A-Datensätze zum vollständig qualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) der Lastausgleichsfunktion hinzugefügt.

### Interne Lastausgleichsfunktion
Jetzt ist die stark nachgefragte "interne" Version von IBM Cloud Load Balancer verfügbar. Diese Lastausgleichsfunktion ist nicht öffentlich zugänglich, kann aber trotzdem dazu verwendet werden, die Last von Anwendungen in ihren privaten IBM Cloud-Netzen auszugleichen (wie in der Abbildung zum Beispiel in einer mehrschichtigen Umgebung). Sie ist sowohl sicher als auch mit den vorherigen Versionen von IBM Cloud Load Balancer auf der öffentlichen Seite konsistent. 

![Interne Lastausgleichsfunktion](./images/InternalLB.png)

### Überwachungsmetriken
Mit dem Service "IBM Cloud Monitoring" können Sie jetzt die folgenden Leistungsmetriken überwachen, die der Lastausgleichsfunktion und der Anwendung zugeordnet sind:

* Durchsatz
* Verbindungsrate
* Aktive Verbindungen 

![Überwachungsmetriken](./images/Metrics.png)

Von der Webbenutzerschnittstelle der Lastausgleichsfunktion werden bis zu zwei Wochen Stichproben erfasst und angezeigt. Die Daten können auch im Serviceportal von IBM Cloud Monitoring angezeigt werden. Falls Sie Daten für mehr als zwei Wochen benötigen, müssen Sie abhängig von der Menge anderer Cloudmetriken, die Sie eventuell an die Cloud Monitoring-Instanz senden, unter Umständen ein Upgrade für den Überwachungsplan durchführen.

Damit diese Funktion genutzt werden kann, müssen die IaaS- und PaaS-Konten von IBM Cloud über einige [einfache Schritte](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts) verknüpft werden. 

### Anpassung der Cipher-Suite
Sie können jetzt die Cipher-Suites anpassen, die verwendet werden, wenn die Lastausgleichsfunktion zur Ausführung der SSL-Terminierung konfiguriert wird.

Wenn Sie die SSL-Terminierung für IBM Cloud Load Balancer aktivieren (durch Auswählen von HTTPS als Front-End-Protokoll), wird eine sorgfältig ausgewählte Standardgruppe aus Cipher-Suites aktiviert, die den besten Sicherheitsverfahren entsprechen. Sie werden genauestens auf neue Sicherheitslücken überwacht; falls solche erkannt werden, wird die Liste entsprechend aktualisiert. Dies trägt zusammen mit der nahtlosen Aktualisierung von Sicherheitsinformationen für Software- und Hardwarekomponenten zu einem durchgehenden Schutz der Anwendungen bei.
