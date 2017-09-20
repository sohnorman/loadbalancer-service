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

# A propos de

Le service IBM Bluemix Load Balancer aide les clients à améliorer la disponibilité des applications critiques pour l'activité de leur entreprise en répartissant le trafic entre plusieurs instances de serveur et en réacheminant le trafic vers des instances viables seulement.

## Présentation des fonctionnalités
Le service IBM Bluemix Load Balancer offre les fonctionnalités suivantes :

* Equilibreur de charge public (Internet)
	* Service publiquement accessible via son nom de domaine complet
	* Instances de serveur de back end sur des sous-réseaux privés
* Equilibrage de charge de base
	* Répartition du trafic basée sur les informations du port d'application à 4 couches
	* Support des applications HTTP, HTTPS et TCP  
	* Large choix de méthodes d'équilibrage de charge, par exemple Round Robin (RR), Round Robin pondéré ou Connexions minimum
	* Equilibrage de charge entre le serveur virtuel et les instances de calcul bare metal se trouvant dans un centre de données
* Diagnostics d'intégrité du serveur
	* Surveillance périodique de la santé du serveur afin de garantir le transfert du trafic vers des serveurs sains uniquement 
	* Diagnostics d'intégrité à 4 couches pour les ports TCP et 7 couches pour les ports HTTP 
* Déchargement SSL 
	* Arrêt du trafic SSL entrant (HTTPS) avec communication HTTP en texte en clair avec les serveurs de back end
* Gestion de trafic avancée
	* Adhésion client (persistance de session)
	* Nombre de connexions maximum par port virtuel
* Gestion aisée grâce à une interface graphique et une interface de programmation intuitives
* Fiabilité intégrée 
* Tarification basée sur l'utilisation 
