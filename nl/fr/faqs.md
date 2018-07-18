---

copyright:
  years: 2017
lastupdated: "2018-03-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Foire aux questions

La présente section apporte des réponses aux questions les plus fréquemment posées au sujet du service Equilibreur de charge IBM Cloud. 

## Combien d'options d'équilibrage de charge sont disponibles dans {{site.data.keyword.BluSoftlayer_notm}} ?

Pour une comparaison détaillée des offres Equilibreur de charge d'IBM, voir [Découverte des équilibreurs de charge](https://dev-console.bluemix.net/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers).

## Puis-je utiliser un nom DNS différent pour mon équilibreur de charge ?

Bien que le nom DNS affecté automatiquement à l'équilibreur de charge ne soit pas personnalisable, vous avez la possibilité d'ajouter un enregistrement CNAME (nom canonique) qui fasse pointer le nom DNS de votre choix vers le nom DNS affecté automatiquement. Supposons que votre numéro de compte soit 123456, que votre équilibreur de charge soit déployé dans le centre de données "dal09" sous le nom "myapp" et que le nom DNS affecté automatiquement à l'équilibreur de charge soit "myapp-123456-dal09.lb.bluemix.net". Si vous souhaitez utiliser le nom DNS "www.myapp.com", vous pouvez ajouter un enregistrement CNAME (via le fournisseur DNS utilisé pour gérer myapp.com) qui fasse pointer "www.myapp.com" sur le nom DNS d'équilibreur de charge "myapp-12345-dal09.lb.bluemix.net".

## Quel est le nombre maximal de ports virtuels que je peux définir avec mon service Equilibreur de charge ?

Lors de la création d'un service Equilibreur de charge, vous pouvez définir jusqu'à deux ports virtuels. Vous pouvez définir des ports virtuels supplémentaires une fois le service créé. La limite autorisée est alors de 10 ports virtuels. 

## Quel est le nombre maximal d'instances de calcul que je peux associer à mon équilibreur de charge ?

50.

## Quels sont les paramètres par défaut et les valeurs autorisées pour les différents paramètres de contrôle de santé ?

Vous trouverez ci-dessous la liste des paramètres par défaut et des valeurs autorisées :

* **Intervalle de contrôle de santé :** La valeur par défaut est 5 secondes et la plage autorisée est comprise entre 2 et 60 secondes
* **Délai de réponse du contrôle de santé :** La valeur par défaut est 2 secondes et la plage autorisée est comprise entre 1 et 59 secondes
* **Nombre maximal de tentatives :** La valeur par défaut est 2 et tentatives la plage autorisée est comprise entre 1 et 10 tentatives

**Remarque :** La valeur du délai de réponse du contrôle de santé doit toujours être inférieure à la valeur d'intervalle de contrôle de santé. 

## Puis-je utiliser des instances de calcul situées dans des centres de données distants avec ce service ? 

Il est recommandé d'installer votre service Equilibreur de charge et vos instances de calcul en local dans le même centre de données. L'interface graphique du service Equilibreur de charge n'affiche pas les instances de calcul des autres centres de données distants. Cependant, les instances de calcul des autres centres de données d'une même ville (à savoir, les centres de données dont le nom commence par les mêmes 3 premières lettres, telles que DALxx). Vous pouvez tout de même utiliser l'API pour ajouter des instances de calcul de n'importe quel autre centre de données distant. 

## Quelle est la version TLS compatible avec le déchargement SSL ?

Le service Equilibreur de charge IBM Cloud prend en charge la version TLS 1.2 avec terminaison SSL. 

La liste ci-dessous répertorie les différents chiffrements pris en charge (par ordre de priorité) :  

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

## Combien d'instances de service Load Balancer maximum puis-je créer dans mon compte ? 

Actuellement, vous pouvez créer jusqu'à 20 instances de service. Si vous avez besoin de plus d'instances, contactez le support IBM. 

## Le service Equilibreur de charge IBM Cloud peut-il être utilisé avec VMWare ? 

Les machines virtuelles VMWare auxquelles des adresses privées portables SoftLayer sont affectées peuvent être spécifiées en tant que serveurs de back end pour l'équilibreur de charge. Cette fonctionnalité est actuellement disponible uniquement à l'aide de l'API et non via l'interface graphique (GUI) Web. Les adresses IP privées portables qui sont ajoutées à l'aide de l'API apparaissent comme étant "inconnues" dans l'interface graphique, car elles ne sont pas affectées par SoftLayer. Notez que ce type de configuration peut être utilisé avec d'autres hyperviseurs, tels que Xen et KVM.

Les machines virtuelles VMWare auxquelles des adresses autres que SoftLayer (par exemple, des réseaux VMware NSX) sont affectées ne peuvent pas être ajoutées directement en tant que serveurs de back end à l'équilibreur de charge. Toutefois, selon votre configuration, il peut être possible de configurer un intermédiaire, tel qu'une passerelle NSX, doté d'une adresse privée SoftLayer en tant que serveur de back end pour l'équilibreur de charge (avec les serveurs réels associés virtuellement (VM) aux réseaux gérés par VMware NSX).

## Si je choisis d'utiliser un VLAN public sous mon compte pour déployer mon équilibreur de charge et qu'un pare-feu est déployé sur mon VLAN public, quelles sont les exigences requises sur le pare-feu pour pouvoir utiliser le service Equilibreur de charge ?

Le port TCP 56501 est utilisé à des fins de gestion. Assurez-vous que le trafic vers ce port, et vers les ports de l'application, n'est pas bloqué par votre pare-feu, faute de quoi la mise à disposition de l'équilibreur de charge risque d'échouer.

## Que dois-je faire lorsque l'erreur "Ce compte SoftLayer n'est lié à aucun compte Bluemix" s'affiche ?

Assurez-vous que votre compte SoftLayer est lié à votre compte Bluemix. Pour obtenir davantage instructions, voir [Liaison Softlayer](https://console.bluemix.net/docs/account/softlayerlink.html#switching-to-ibmid). 
