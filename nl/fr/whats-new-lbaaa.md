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


# Nouveautés

Découvrez les fonctions nouvelles et mises à jour dans le service Equilibreur de charge IBM Cloud

## Avril 2018
### Mise à l'échelle horizontale
Désormais, le service Equilibreur de charge IBM Cloud augmente automatiquement lorsque la charge  augmente (et diminue à mesure que la charge diminue). Au moment de sa création, l'équilibreur de charge est doté de deux dispositifs, mais le nombre de ces derniers peut augmenter et aller jusqu'à 16 (au moment de la rédaction du présent document) à mesure que notre système de surveillance détecte une augmentation de la charge. Les adresses IP de chacun des dispositifs actifs sont ajoutées en tant qu'enregistrements A DNS au nom de domaine complet de l'équilibreur de charge.

### Equilibreur de charge interne
Une version interne très demandée de notre service Equilibreur de charge IBM Cloud est désormais disponible. Cet équilibreur de charge n'est pas exposé au public, mais peut tout de même être utilisé pour équilibrer la charge des applications dans leurs réseaux privés IBM Cloud (dans un déploiement à plusieurs niveaux, par exemple, comme illustré dans la figure). Il est sécurisé et cohérent avec les versions précédentes du service Equilibreur de charge IBM Cloud côté public.  

![Equilibreur de charge interne](./images/InternalLB.png)

### Métriques de surveillance
Vous pouvez désormais optimiser le service IBM Cloud Monitoring pour surveiller les métriques de performance suivantes associées à votre équilibreur de charge et à votre application :

* Débit
* Taux de connexion
* Connexions actives

![Métriques de surveillance](./images/Metrics.png)

Des échantillons pouvant avoir jusqu'à deux semaines d'existence sont collectés et affichés par l'interface utilisateur Web de l'équilibreur de charge. Les données peuvent également être affichées sur le portail du service IBM Cloud Monitoring. Si vous avez besoin de données de plus de deux semaines, selon la quantité d'autres métriques cloud que vous êtes susceptibles d'envoyer à votre instance IBM Cloud Monitoring, vous devrez peut-être effectuer une mise à niveau de votre plan de surveillance. 

Pour cette fonction, vous devez impérativement lier vos comptes IBM Cloud IaaS et PaaS en exécutant [quelques étapes simples](https://console.bluemix.net/docs/account/linking_accounts.html#unifyingaccounts). 

### Personnalisation des suites de chiffrement
Vous pouvez désormais personnaliser les suites de chiffrement utilisées lors de la configuration de l'équilibreur de charge pour exécuter l'arrêt SSL. 

Lorsque vous activez l'arrêt SSL sur le service Equilibreur de charge IBM Cloud (en sélectionnant HTTPS comme protocole frontal), un ensemble de suites de chiffrement par défaut soigneusement sélectionné et conforme aux meilleures pratiques est activé. Nous suivons de près les éventuelles vulnérabilités pouvant survenir et nous mettons à jour cette liste de suites de chiffrement en conséquence. Si vous ajoutez à cela des mises à jour de sécurité apportées de manière transparente aux composants logiciels et matériels, vous obtenez la garantie que nous mettons tout en oeuvre pour que vos applications soient tout le temps sécurisées. 
