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

# Foire aux questions

La présente section apporte des réponses aux questions les plus fréquemment posées au sujet du service IBM Bluemix Load Balancer.

## Quel est le nombre maximal de ports virtuels que je peux définir avec mon service d'équilibrage de charge ?

Lors de la création d'un service d'équilibrage de charge, vous pouvez définir jusqu'à deux ports virtuels. Vous pouvez définir des ports virtuels supplémentaires une fois le service créé. La limite autorisée est alors de 10 ports virtuels. 

## Quel est le nombre maximal d'instances de calcul que je peux associer à mon équilibreur de charge ?

50.

## Puis-je créer un équilibrage de charge privé interne accessible uniquement pas des clients internes ?  

Pas pour le moment. Le service hébergé sur l'équilibreur de charge IBM Bluemix sera associé à un nom de domaine complet accessible depuis l'internet public. 

## Quels sont les paramètres par défaut et les valeurs autorisées pour les différents paramètres de diagnostic d'intégrité ?

Vous trouverez ci-dessous la liste des paramètres par défaut et des valeurs autorisées :

* **Intervalle de diagnostic d'intégrité :** La valeur par défaut est 5 secondes et la plage autorisée est comprise entre 2 et 60 secondes
* **Délai de réponse du diagnostic d'intégrité :** La valeur par défaut est 2 secondes et la plage autorisée est comprise entre 1 et 59 secondes
* **Nombre max. de tentatives :** La valeur par défaut est 2 tentatives et la plage autorisée est comprise entre 1 et 10 tentatives

**Remarque :** La valeur du délai de réponse du diagnostic d'intégrité doit toujours être inférieure à la valeur d'intervalle de diagnostic d'intégrité. 

## Puis-je utiliser des instances de calcul situées dans des centres de données distants avec ce service ? 

Il est recommandé que votre service d'équilibrage de charge et vos instances de calcul soient installés en local dans le même centre de données. L'interface graphique du service d'équilibrage de charge n'affiche pas les instances de calcul des autres centres de données distants. Cependant, les instances de calcul des autres centres de données d'une même ville (à savoir, les centres de données dont le nom commence par les mêmes 3 premières lettres, tel que `DALxx`) sont affichées. Vous pouvez tout de même utiliser l'interface de programmation pour ajouter des instances de calcul de n'importe quel autre centre de données distant. 

## Quelle est la version TLS compatible avec le déchargement SSL ? Quels sont les chiffrements pris en charge ?

Le service Bluemix Load Balancer prend en charge la version TLS 1.2 avec terminaison SSL. 

La liste ci-dessous répertorie les différents chiffrements pris en charge (par ordre de priorité) :  

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

## Puis-je personnaliser ma liste de chiffrements SSL ?

Pas pour le moment. 

## Combien d'instances de service Load Balancer maximum puis-je créer dans mon compte ? 

Actuellement, vous pouvez créer jusqu'à 20 instances de service. Si vous avez besoin de plus d'instances, contactez le support IBM. 


