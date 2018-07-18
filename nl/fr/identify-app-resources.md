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

# Identifier vos ressources d'application

Identifiez les ressources de votre application, par exemple, les pools d'origines et les mécanismes de contrôle de santé. 
 
1. Accédez à la section **Pools d'origines** et cliquez sur **Créer un pool** afin de définir un nouveau pool d'origines.  

   Les pools d'origines sont des ressources serveur qui fournissent des applications à vos clients.  
   
2. Affectez un nom à votre pool d'origines et sélectionnez le mécanisme de contrôle de santé défini précédemment. Ajoutez votre serveur d'applications comme origine. Vous pouvez ajouter une ou plusieurs origines en cliquant sur **Ajouter une origine**. 

   **Remarque :** si vos serveurs d'applications sont installés derrière un équilibreur de charge local, par exemple, un service Equilibreur de charge IBM Cloud, ajoutez le nom de domaine complet ou l'adresse IP de votre équilibreur de charge comme origine au lieu d'ajouter vos serveurs individuels.  
   
3. Cliquez sur **Mettre à disposition une ressource** pour finaliser la création de votre pool d'origines.   

   <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>
   
   Au départ, le pool d'origines est à l'état **Défaillant**. Il passe à l'état **Sain** après un contrôle de santé réussi réalisé par le système. Vous devrez peut-être actualiser votre navigateur pour voir le changement d'état.  
   
   <img src="images/Reliability9.png" alt="drawing" style="width: 300px;"/>
   
   **Remarque :** si votre pool d'origines comporte plusieurs origines, utilisez le paramètre Seuil d'origine saine pour spécifier le nombre minimal d'origines qui doivent être saines pour que le pool puisse être déclaré comme étant sain.  
   
4. Définissez autant de pools d'origines que de parcs d'applications dont vous disposez. Ces parcs peuvent se trouver dans la même région ou dans des régions différentes.
Dans notre exemple, nous allons créer deux pools d'origines représentant un parc d'applications situé sur les côtes Ouest et Est des Etats-Unis.  

   <img src="images/Reliability10.png" alt="drawing" style="width: 300px;"/>
