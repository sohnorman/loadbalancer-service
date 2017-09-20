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

# Déchargement SSL

A chaque connexion HTTP entrante, le service d'équilibrage de charge met fin à la connexion SSL et établit une communication HTTP en texte en clair avec le serveur de back end. Les serveurs de back end sont alors déchargés des tâches de chiffrement/déchiffrement et d'établissement de liaison SSL, de sorte qu'ils peuvent utiliser l'intégralité de leur cycle d'unité centrale à des fins de traitement du trafic d'application. Un certificat SSL est nécessaire pour que l'équilibreur de charge procède aux tâches de déchargement SSL. Vous pouvez utiliser un certificat SSL préexistant ou en acheter un nouveau, et utiliser le [magasin de certificats Bluemix/Softlayer](https://control.softlayer.com/security/sslcerts) à des fins de gestion. 

**Remarque :** Le service d'équilibrage de charge prend en charge la version TLS 1.2 avec déchargement SSL. Il n'est pas compatible avec SSLv3 en raison de ses vulnérabilités. La liste de chiffrements SSL n'est pas personnalisable pour le moment. 
