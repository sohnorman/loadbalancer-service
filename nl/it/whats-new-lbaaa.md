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


# Novità

Scopri ulteriori informazioni su funzioni nuove e aggiornate in IBM Cloud Load Balancer.

## Aprile 2018
### Scalabilità orizzontale
IBM Cloud Load Balancer viene ora aumentato automaticamente quando il carico cresce (e diminuito quando decresce). Quando viene creato il programma di bilanciamento del carico, viene avviato con due applicazioni, ma il numero di applicazioni può essere portato fino a 16 in questo momento, perché il nostro sistema di monitoraggio rileva un aumento del carico. Gli indirizzi IP di ogni applicazione attiva vengono aggiunti come A-Record DNS al nome di dominio completo (FQDN) del programma di bilanciamento del carico.

### Programma di bilanciamento del carico interno 
È ora disponibile una versione “Interna” molto richiesta del nostro IBM Cloud Load Balancer. Questo programma di bilanciamento del carico non è esposto pubblicamente, ma può ancora essere utilizzato per bilanciare il carico delle applicazioni nella loro rete privata IBM Cloud (in una distribuzione a più livelli, per istanza, come mostrato nella figura). È sia sicuro che coerente con le versioni precedenti di IBM Cloud Load Balancer sul lato pubblico 

![Programma di bilanciamento del carico interno](./images/InternalLB.png)

### Metriche di monitoraggio
Puoi ora utilizzare il servizio “IBM Cloud Monitoring” per monitorare le seguenti metriche delle prestazioni associate al tuo programma di bilanciamento del carico e alla tua applicazione:

* Velocità effettiva
* Frequenza di connessione
* Connessioni attive 

![Metriche di monitoraggio](./images/Metrics.png)

Vengono raccolte e visualizzate fino a due settimane di esempi dalla IU web del programma di bilanciamento del carico. I dati possono essere visualizzati anche nel portale del servizio IBM Cloud Monitoring. Se hai bisogno dei dati per più di due settimane, a seconda del volume delle altre metriche cloud che potresti dover inviare alla tua istanza di monitoraggio cloud, potresti aver bisogno di aggiornare il tuo piano di monitoraggio.

Questa funzione richiede che i tuoi account IBM Cloud IaaS e PaaS siano collegati, con alcuni [semplici passi](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts). 

### Personalizzazione della suite di cifratura 
Puoi ora personalizzare le suite di cifratura che vengono utilizzate quando il programma di bilanciamento del carico viene configurato per eseguire la terminazione SSL.

Quando abiliti la terminazione SSL su IBM Cloud Load Balancer (selezionando HTTPS come protocollo di frontend), abilitiamo una serie di suite di cifratura predefinita attentamente selezionata che è conforme alle migliori procedure di sicurezza. Manteniamo sotto stretto controllo ogni nuova vulnerabilità che può venire rilevata e aggiorniamo l'elenco di conseguenza. Questo, insieme agli aggiornamenti di sicurezza continui dei componenti software e hardware, consente di mantenere le tue applicazioni sempre sicure.
