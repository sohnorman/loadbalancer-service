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

# FAQ

Questa sezione contiene le risposte ad alcune domande frequenti sul servizio IBM Bluemix Load Balancer.

## Qual'è il numero massimo di porte virtuali che posso definire con il mio servizio del programma di bilanciamento del carico?

Mentre si tenta di creare un nuovo servizio del programma di bilanciamento del carico, puoi definire fino a due porte virtuali. Puoi definire ulteriori porte dopo aver creato il servizio. Il numero massimo di porte virtuali è 10. 

## Qual'è il numero massimo di istanze di calcolo che posso associare al mio programma di bilanciamento del carico?

50.

## Posso creare un programma di bilanciamento del carico privato e soltanto interno a cui è possibile accedere soltanto dai client interni?  

Non in questo momento. Il servizio ospitato sul programma di bilanciamento del carico IBM Bluemix sarà assegnato a tutti i nomi dominio completi accessibili pubblicamente da internet. 

## Quali sono le impostazioni predefinite e i valori consentiti per i vari parametri del controllo di integrità?

Le impostazioni predefinite e i valori consentiti sono elencati di seguito:

* **Intervallo controllo di integrità:** il valore predefinito è 5 secondi, l'intervallo è 2 – 60 secondi
* **Timeout risposta controllo di integrità:** il valore predefinito è 2 secondi, l'intervallo è 1 – 59 secondi
* **Numero massimo nuovi tentativi:** il valore predefinito è 2 nuovi tentativi, l'intervallo è compreso tra 1 e 10

**Nota:** il valore del timeout della risposta del controllo di integrità deve sempre essere inferiore al valore dell'intervallo del controllo di integrità. 

## Posso utilizzare le istanze di calcolo che risiedono nei data center remoti con questo servizio? 

Ti raccomandiamo che il tuo servizio del programma di bilanciamento del carico e le tue istanze di calcolo risiedano localmente nello stesso data center. La GUI (graphical interface) del servizio del programma di bilanciamento del carico non visualizzerà le istanze di calcolo da altri data center remoti. Tuttavia, la GUI includerà le istanze di calcolo da altri data center nella stessa città (ad esempio, i data center i cui nomi condividono le prime tre lettere come `DALxx`). Puoi comunque utilizzare l'interfaccia API per aggiungere le istanze di calcolo da qualsiasi data center remoto. 

## Quale versione TLS è supportata con l'offload SSL? Quali cipher sono supportati?

Il servizio Bluemix Load Balancer supporta TLS 1.2 con terminazione SSL. 

Il seguente elenco mostra i cipher supportati (elencati in ordine di precedenza):  

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

## Posso personalizzare il mio elenco di cipher SSL?

Non in questo momento.

## Qual'è il numero massimo di istanze del servizio Load Balancer che posso creare nel mio account? 

Al momento, puoi creare fino a 20 istanze del servizio. Se hai bisogno di più istanze, contatta il supporto IBM. 


