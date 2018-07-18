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

# Identifica le tue risorse dell'applicazione

Identifica le risorse della tua applicazione, come i pool di origine e i meccanismi di controllo dell'integrità. 
 
1. Passa alla sezione **Origin Pools** e fai clic su **Create pool** per definire un nuovo pool di origine. 

   I pool di origine sono risorse server che forniscono le applicazioni ai tuoi client. 
   
2. Assegna un nome al tuo pool di origine e seleziona il meccanismo di controllo di integrità definito precedentemente. Aggiungi il tuo server dell'applicazione come tua origine. Puoi aggiungere più di un'origine facendo clic su **Add Origin**. 

   **NOTA:** se i tuoi server dell'applicazione si trovano dietro a un programma di bilanciamento del carico locale come un IBM Cloud Load Balancer, aggiungi il FQDN o l'IP virtuale del tuo programma di bilanciamento del carico come la tua origine invece di aggiungere i tuoi server individuali. 
   
3. Fai clic su **Provision Resource** per completare la creazione del tuo pool di origine.  

   <img src="images/Reliability6.png" alt="disegno" style="width: 300px;"/>
   
   Il pool di origine sarà inizialmente visualizzato come **Unhealthy**. Il suo stato sarà modificato con **Healthy** dopo un controllo di integrità corretto dal sistema. Potresti dover aggiornare il tuo browser per visualizzare la modifica dello stato. 
   
   <img src="images/Reliability9.png" alt="disegno" style="width: 300px;"/>
   
   **NOTA:** se hai più origini all'interno del tuo pool di origine, utilizza la soglia di origine di integrità per specificare il numero minimo di origini che devono essere integre prima di dichiarare il pool integro. 
   
4. Definisci tanti pool di origine quanto è il numero di farm dell'applicazione di cui disponi. Questi farm possono essere all'interno delle stesse o di differenti
regioni geografiche. Nel nostro esempio, creeremo due pool di origine che rappresentano un farm dell'applicazione negli Stati Uniti costa ovest e est. 

   <img src="images/Reliability10.png" alt="disegno" style="width: 300px;"/>
