---

copyright:
  years: 2017
lastupdated: "2018-04-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Guide d'initiation
Pour commencer à utiliser le service Equilibreur de charge IBM Cloud, vous aurez besoin des deux éléments essentiels suivants :

* Un compte IBM : [IBMid](https://www.ibm.com/account/us-en/signup/register.html).
* Un serveur IBM (il peut s'agir d'un serveur [Bare Metal](https://console.bluemix.net/docs/bare-metal/about.html#getting-started-with-bare-metal-servers) oud'une [instance de serveur virtuel](https://console.bluemix.net/docs/vsi/vsi_index.html#getting-started-with-virtual-servers)).
 
Si vous avez besoin d'aide pour obtenir un compte **IBMid**, contactez votre [commercial IBM](https://www.ibm.com/cloud-computing/bluemix/contact-us). 

Si vous disposez d'un compte IBM Cloud Infrastructure (SoftLayer), vous pouvez [lier votre compte](https://console.bluemix.net/docs/account/softlayerlink.html#unifyingaccounts) à votre IBMid. 

## Commande d'un équilibreur de charge

Pour commander un service Equilibreur de charge IBM Cloud, sélectionnez **Réseau > Equilibreurs de charge > Equilibreur de charge IBM Cloud** dans le  [catalogue IBM Cloud](https://console.bluemix.net/catalog/infrastructure/load-balancer-group). Connectez-vous ou créez un nouveau compte, puis suivez la procédure ci-dessous :

1. Sélectionnez votre centre de données et examinez le plan de service. Cliquez sur **Suivant**.
2. Sélectionnez le sous-réseau sur lequel déployer votre équilibreur de charge. L'une des interfaces réseau de votre instance de service Equilibreur de charge se trouvera sur ce sous-réseau. Assurez-vous que vos serveurs d'applications sont installés sur ce sous-réseau et sont accessibles à partir de celui-ci. Si nécessaire, activez la superposition VLAN. Cliquez sur **Suivant**.
3. Définissez les paramètres de service de base, tels que le nom, la description, les ports et protocoles d'applications de front end et de back end, ainsi que la méthode d'équilibrage de charge. Vous pouvez configurer jusqu'à deux protocoles lors de la procédure initiale de création du service. Vous pouvez définir jusqu'à dix protocoles une fois le service créé. Vous devez également utiliser un seul port de front end. Cliquez sur **Suivant**.
4. Ajustez les paramètres de contrôle de santé si besoin, ou utilisez les paramètres par défaut. Cliquez sur **Suivant**.
5. Associez une ou plusieurs instances de serveurs derrière votre équilibreur de charge. Seules les instances de serveur locales sur votre centre de données seront affichées. Cliquez sur **Suivant**.
6. Consultez la page de synthèse et cliquez sur **Créer**. 


La page de synthèse affiche l'instance du service d'équilibreur de charge que vous venez de créer. Examinez la zone **Statut**. Le statut `Hors ligne` indique que l'équilibreur de charge n'est pas en service. Aucune nouvelle configuration ne peut être effectuée et aucun service Equilibreur de charge ne peut être fourni tant que le statut n'est pas `En ligne`. Vous devrez peut-être actualiser la page voir afficher le statut en cours.
 
Lorsque vous cliquez sur le nom du service sur cette page, la page de présentation du service s'ouvre. Accédez aux onglets **Protocoles**, **Contrôles de santé** et **Instances de serveur** pour modifier votre configuration existante.
