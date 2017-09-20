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

# SSL-Auslagerung

Für alle eingehenden HTTPS-Verbindungen wird die SSL-Verbindung vom Service für die Lastausgleichsfunktion terminiert und eine unverschlüsselte HTTP-Kommunikation mit dem Back-End-Server aufgebaut. So werden CPU-intensive SSL-Handshakes und Tasks zur Verschlüsselung und Entschlüsselung von den Back-End-Servern ausgelagert, damit diese ihre gesamten CPU-Zyklen für die Verarbeitung des Anwendungsdatenverkehrs nutzen können. Ein SSL-Zertifikat ist erforderlich, damit von der Lastausgleichsfunktion SSL-Auslagerungstasks durchgeführt werden können. Sie können ein bereits vorhandenes SSL-Zertifikat verwenden oder ein neues kaufen und dieses über den [Bluemix/Softlayer-Zertifikatsspeicher](https://control.softlayer.com/security/sslcerts) verwalten.  

**HINWEIS:** Vom Service für die Lastausgleichsfunktion wird TLS Version 1.2 mit SSL-Auslagerung unterstützt. SSL Version 3 wird aufgrund der Sicherheitslücken nicht unterstützt. Derzeit kann die SSL-Verschlüsselungsliste nicht angepasst werden.  
