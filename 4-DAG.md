---
layout: post
title: DAG
---

## Microtransactions : 

L’une des promesses de la blockchain a été de permettre les microtransactions. ie des transactions beaucoup plus fréquentes et de très faible valeur. A ce jour, la technologie a échoué à délivrer cette promesse.  
Les frais de transactions pour la blockchain Bitcoin sont de l’ordre de quelques dizaines de centimes, et bien que cela soit un très faible prix à payer pour effectuer de larges transactions. Il n’est pas logique de payer des dizaines de centimes pour envoyer 5 centimes. 
Les microtransactions sont aussi inefficace à cause des limitation de la blockchain actuelle abordées dans la section précédente, à savoir faible vitesse de transaction et problème de scalabilité.  
De manière générale, les transactions sur Bitcoin et Ethereum sont lentes surtout en comparaison avec Visa que la blockchain prétend vouloir remplacer. 
￼
![blockchain](/Images/Picture11.png/)

## DAG

![blockchain](/Images/Picture23.png/)

La technologie <strong>DAG</strong> ou <strong>Tangle</strong> est une technologie concurrente qui se donne comme objectif de résoudre ces problèmes. Dag est un sigle qui veut dire : directed acyclic graph. C’est donc un graphe dirigé sans boucle. Chaque arête est dirigée depuis les noeuds précédents (haut à gauche) aux noeuds suivants (en bas à droite). Ce type de graphe est très utilisé en ordonnancement de projet et en organigrammes. 

￼
Dans la technologie DAG, le graphe lui même sert de registre. Et chaque utilisateur doit valider 2 transactions précédentes pour ajouter sa transaction. Ceci veut dire que chaque utilisateur est un mineur dans le sens où chaque utilisateur doit valider des transactions pour utiliser le réseau, mais pas dans le sens de valider des transactions pour gagner de l’argent. 
Si un utilisateur veut soumettre sa transaction H, il doit d’abord valider 2 transactions précédentes E et G et attendre qu’un autre utilisateur valide sa propre transaction. La selection des 2 transactions à valider pour un utilisateur se fait aléatoirement par l’algorithme de Markov Chain Monte Carlo. Si les utilisateurs pouvaient choisir quelles transactions précédentes valider, ils pourraient choisir leur propre transactions et commettre une fraude. 

￼![blockchain](/Images/Picture12.png/)

La conséquence d’avoir chaque utilisateur en role de mineur est que la vitesse du réseau augmente avec l’augmentation du nombre d’utilisateur, contrairement à la blockchain. 

![blockchain](/Images/screenshot3.png/)
￼
## Blockchain vs DAG
Voici un tableau comparatif entre Blokchain et Tangle :

<table>
  <thead>
    <tr>
      <th>Blockchain</th>
      <th>Tangle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Frais</td>
      <td>Pas de Frais</td>
    </tr>
    <tr>
      <td>Mineurs</td>
      <td>Pas de Mineurs (tout le monde est un validateur)</td>
    </tr>
        <tr>
      <td>Blocs</td>
      <td>Pas de Blocs</td>
    </tr>
        <tr>
      <td>Hard/Soft Fork</td>
      <td>Pas de possiblité de Fork</td>
    </tr>
        <tr>
      <td>Utilise un algo de consensus</td>
      <td>Utilise un algo de consensus</td>
    </tr>
        <tr>
      <td>Utilise Hashcash pour le proof of Work des mineurs (Tout le réseau de mineur essaie de résoudre le problème)</td>
      <td>Utilise Hashcash pour soumettre des transaction (Chaque utlisateur résoud un problème pour éviter les attaques DoS) </td>
    </tr>
  </tbody>
</table>

Tangle utilise <strong>Hashcash</strong> pour éviter le flood. Hashcash a été développé en 1999 pour combattre les spams de serveurs et les attaques DoS. L’idée est que chaque machine doit effectuer un calcul avant de pouvoir soumettre une requête.  Ceci est le même algorithme utilisé pour le mining dans Bitcoin et la blockchain. 
Mais contrairement au Proof of Work dans la blockchain, nécessitant 10 minutes à <em>tout</em> le réseau pour résoudre. Le problème Hashcash dans Tangle est assez simple pour être résolu par un objet connecté. De manière à rendre la soumission d'une seule transaction, et compliqué d'en soumettre beaucoup.   
On voit alors que Tangle est particulièrement adapté à l’IoT. Dans un marché avec des milliards de devices connectées, les frais “élevés” de la blockchain et les problèmes de scalabilité font que la technologie n’est actuellement pas adapté. DAG prétend résoudre ces problèmes et être adaptée à ces cas d’utilisation. 

### Exemples : 
* Drones pour la livraison : Si on imagine un système de drones connectés qui ont pour objectif de livrer des colis. Chaque drone peut calculer le cout d’une livraison d’un point A à un point B, et décider de livrer lui même ou déléguer à un autre drone avec un coût moindre. 
* Voitures connectées : Paiement automatique du parking, de la recharge de batterie, du péage autoroute, possibilité de louer la voiture sans intermédiaire
* Smart city et smart grids : Vendre de l’excès d’énergie solaire aux voisins de manière automatique. 

Exemples d’entreprises travaillant sur la technologie DAG : 

* <strong>Iota</strong> : Objectif d’offrir des transactions gratuites entre plusieurs machines IoT, et de permettre les transactions sans intervention humaine.  
* <strong>Nano</strong> : Cryptomonnaie permettant des transactions sans frais et microtransactions en utilisant une architecture block-lattice (chaque utilisateur possède sa propre blockchain). 


