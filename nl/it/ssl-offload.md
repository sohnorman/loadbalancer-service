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

# Offload SSL

Per tutte le connessioni HTTPS in entrata, il servizio del programma di bilanciamento del carico termina la connessione SSL e stabilisce la comunicazione HTTP di testo semplice con il server di backend. I server di backend sono quindi scaricati dall'elaborare gli handshake SSL con uso intensivo di CPU e le attività di crittografia/decrittografia, per cui possono utilizzare i loro cicli di CPU per elaborare il traffico dell'applicazione. Un certificato SSL è obbligatorio al programma di bilanciamento del carico per eseguire le attività offload SSL. Puoi utilizzare un certificato SSL preesistente o acquistarne uno nuovo e gestirlo con [IBM Cloud Certificate Store ](https://control.softlayer.com/security/sslcerts). 

**NOTA:** il servizio del programma di bilanciamento del carico supporta TLS versione 1.2 con offload SSL. Non supporta SSLv3 a causa delle sua vulnerabilità. L'elenco dei cipher SSL non può essere personalizzato in questo momento. 
