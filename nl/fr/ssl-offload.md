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

# Déchargement SSL

A chaque connexion HTTP entrante, le service Equilibreur de charge met fin à la connexion SSL et établit une communication HTTP en texte en clair avec le serveur de back end. Les tâches de chiffrement/déchiffrement et d'établissement de liaison SSL sont déchargées des serveurs de back end, de sorte qu'ils peuvent utiliser l'intégralité de leur cycle d'unité centrale à des fins de traitement du trafic d'application.  

Un certificat SSL est nécessaire pour que l'équilibreur de charge procède aux tâches de déchargement SSL. Vous pouvez utiliser un certificat SSL préexistant ou en acheter un nouveau, et utiliser le [magasin de certificats IBM Cloud](https://control.softlayer.com/security/sslcerts) à des fins de gestion. 

# Suites de chiffrement SSL
Le service Equilibreur de charge prend en charge la version TLS 1.2 avec déchargement SSL.

Les suites de chiffrement SSL suivantes sont prises en charge par votre équilibreur de charge :

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

Si au moins un port d'application frontale HTTPS (protocoles) est configuré votre équilibreur de charge, par défaut, toutes les suites de chiffrement SSL prédéfinies ci-dessus seront activées pour votre équilibreur de charge. Vous pouvez choisir d'activer d'autres suites de chiffrement SSL pour votre équilibreur de charge, si besoin. 
