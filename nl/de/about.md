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

# Produktinformation

Der IBM Cloud Load Balancer-Service unterstützt die Kunden beim Verbessern der Verfügbarkeit ihrer geschäftskritischen Anwendungen; dazu wird der Datenverkehr auf mehrere Anwendungsserverinstanzen verteilt und ausschließlich an ordnungsgemäß funktionierende Instanzen weitergeleitet. 

## Übersicht über die Features
Der IBM Cloud Load Balancer-Service bietet die folgenden Features:

* Öffentliche Lastausgleichsfunktion (im Internet)
	* Über vollständig qualifizierten Domänennamen öffentlich zugänglicher Service
	* Back-End-Serverinstanzen für private Teilnetze
* Basislastausgleich
	* Verteilung des Datenverkehrs auf der Basis einer Anwendungsportinformtion der Ebene 4 (Layer-4)
	* Unterstützung für HTTP-, HTTPS- und TCP-basierte Anwendungen 
	* Vielzahl an Lastausgleichsmethoden, zum Beispiel 'Round Robin' (RR), 'Weighted Round Robin' (WRR) und 'Least Connections'
	* Lastausgleich zwischen virtuellem Server und Bare-Metal-Recheninstanzen, die sich lokal im Rechenzentrum befinden
* Statusprüfungen für Server
	* Periodische Überwachung des Serverstatus, um sicherzustellen, dass der Datenverkehr nur an ordnungsgemäß funktionierende Server weitergeleitet wird 
	* Statusprüfungen der Ebene 4 (Layer-4) für TCP-Ports und Statusprüfungen der Ebene 7 (Layer-7) für HTTP-Port 
* SSL-Auslagerung
	* Terminierung des eingehenden SSL-Verkehrs (HTTPS) mit ungeschützter HTTP-Kommunikation mit Back-End-Servern
* Erweiterte Verwaltung des Datenverkehrs
	* Clientattraktivität (Sitzungspersistenz)
	* Maximale Verbindungen pro virtuellem Port
* Einfache Verwaltung durch intuitive grafische Schnittstelle und API
* Integrierte Zuverlässigkeit 
* Nutzungsorientierte Preisgestaltung 
