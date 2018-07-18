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

# Commencer la configuration de l'équilibreur de charge global
Commencez à configurer votre équilibreur de charge global.

1. Sous la section **Fiabilité**, sélectionnez **Equilibreur de charge global**. 
    
    <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>

2. Faites défiler l'écran jusqu'à la section Contrôles de santé.  

   **Remarque :** cette configuration est facultative. Si vous ne définissez pas de contrôles de santé personnalisés, le système utilisera “/” comme chemin de contrôle de santé par défaut.  

3. Cliquez sur le bouton **Créer un contrôle de santé** pour définir un contrôle de santé personnalisé.    

   Indiquez le chemin sur lequel vous souhaitez effectuer vos contrôles de santé. Vous pouvez utiliser des protocoles HTTP ou HTTPS pour vos contrôles de santé.  
   
4. Sous **Options avancées**, vous pouvez personnaliser d'autres paramètres, tels que l'intervalle de contrôle de santé, le nombre de tentatives, la méthode de demande et le corps de réponse.  
   
   <img src="images/Reliability6.png" alt="drawing" style="width: 300px;"/>
   
5. Cliquez sur **Mettre à disposition une ressource** pour terminer votre configuration de contrôle de santé.  
