---
layout: post
title: Blockchain 1.0
---

>Milton Friedman, prix Nobel en sciences économiques a prédit en 1999 le besoin d’une “monnaie virtuelle fiable”, 
cad une e-monnaie indépendante de tout gouvernement et de toute banque qui permettra d’échanger de la valeur entre deux inconnus via Internet. 

10 années plus tard, une cryptomonnaie fait son apparition et se dénomme <strong> Bitcoin </strong>. Elle promet des transactions entre utilisateurs de manière directe et sans intermédiaire. La technologie sous-jacente -blockchain- est expliquée dans un article (WhitePaper) par un certain Satoshi Nakamoto, et le logiciel correspondant est publié en open source. 
Dans la suite nous utiliserons les termes Blockchain 1.0 et Bitcoin de manière interchangeable.
Le Bitcoin étant en fin de compte la première implémentation d’une blockchain 1.0

## Qu'est ce que la Blockchain ? 

En deux mots, la blockchain désigne un <strong>registre distribué</strong>. 
Un peu comme le registre d’une banque où celle-ci garde une copie des soldes de tout les comptes ainsi que leurs transactions,
la blockchain est un registre contenant toutes les transactions ayant été effectué et ce depuis la toute première transaction, à la différence près que ce registre est décentralisé. Cad que celui-ci est public et chaque utilisateur en possède une copie. 

A un niveau très simple, le registre est constitué de lignes du type ci-dessus, avec le numéro de compte de l’expéditeur et du destinataire, et la quantité d’argent envoyée. Si par exemple Alice veut envoyer 5 bitcoins à Bob, elle dévoile son intention de faire cette transaction au reste du réseau, et chaque noeud ajoute la transaction à son registre. 
C’est donc la communauté qui gère le registre, et n’importe qui peut en faire l’audit car les transactions de tout le monde sont visibles par tout le monde. On peut voir comment à un niveau d’explication très basique un système de ce genre permet de se passer d’une entité centrale comme une banque pour effectuer des transactions. Et rien que cela, -la possibilité d’offrir des transactions comme le fait une banque mais sans les limitations qui viennent avec la banque- fait que la monnaie d’échange Bitcoin possède de la valeur pour les utilisateurs. Et plus il y’a d’utilisateurs ayant confiance que cette monnaie possède de la valeur, plus la valeur de cette monnaie augmente. 

Ceci est une première explication simple de ce qu’est la blockchain 1.0, mais comment vérifie-t-on que le propriétaire veut bien faire effectuer la transaction et non pas un imposteur ? 
On utilise pour cela de la cryptographie, chaque utilisateur possède une clé privée. Cette clé privée est associée à une clé publique connue de tout le monde. 
Pour déclarer une transaction, l’utilisateur génère une signature pour prouver qu’il est le possesseur du compte grâce à la clé privée et le message de la transaction “Alice —> Bob 5.0 BTC”. Cette signature a la même utilité que la signature sur un chèque bancaire. 
Le reste des noeuds du réseau peuvent vérifier que la signature a bien été générée par le propriétaire Alice ET pour le message “Alice —> Bob 5.0 BTC” grâce à la clé publique. Grâce à des méthodes de cryptographie on peut vérifier que la signature a bien été générée par le propriétaire, seul possesseur de la clé privé, sans pour autant connaitre cette clé privée.
De plus la signature est spécifique à cette transaction “Alice —> Bob 5.0 BTC”, et ne peut être copiée par quelqu’un d’autre pour une autre transaction. ceci assure aussi que la transaction n’est pas modifiée par des gens malintentionnés quand elle est transmise de noeud en noeud. Puisque n’importe quel changement à la transaction rendra la signature invalide. 
La seconde vérification qui est effectuée est de voir si l’utilisateur envoyant l’argent possède bien une quantité suffisante sur son compte, un parcours des transactions passées dans la blockchain permet de vérifier cela. 

Tout ceci se fait dans un environnement où il n’y a aucune confiance entre les utilisateurs. Et comme on peut s’y attendre dans un environnement sans confiance, quelques individus essayerons de tricher le système. Toutes les tentatives de fraudes se ramènent plus ou moins à ce qu’on appelle un Double Spending. L’idée c’est qu’un utilisateur essaie de dépenser son argent deux fois. 
De par la nature d’un réseau, si un utilisateur envoie deux transactions valides (cad avec une signature valide) en même temps, elle peuvent arriver dans un ordre différent dans des noeuds différents de réseau. 
Imaginons que Alice possède 5 BTC sur son compte, qu’elle décide d’acheter un objet de Bob, elle lui envoie donc les 5 BTC “Alice —> Bob 5.0 BTC”, mais en même temps envoie une transaction “Alice —> Alice2 5.0 BTC” à elle même. Seule l’une de ces deux transactions peut être acceptée, car si l’une est enregistrée sur le registre il n’y a plus de fonds pour executer l’autre. Il se peut donc que la moitié du réseau reçoit la transaction vers Bob en premier et décide donc que la transaction d’Alice vers elle même est invalide car les fonds ont déjà été utilisés pour l’envoi à Bob. Bob peut faire partie de cette moitié de réseau et va envoyer l’objet à Alice car il considère qu’il a reçu l’argent. Mais en même temps l’autre moitié du réseau a reçu la transaction “Alice —> Alice2 5.0 BTC” en premier et considère que la transaction vers Bob est invalide car les fonds ont déjà été utilisés par Alice pour un envoi vers elle-même. 

Comment fait-on dans cette situation ? 

On a déjà un consensus pour savoir si une transaction est valide ou non (expliqué plus haut). Mais il faut aussi établir un consensus sur l’ordre de réception des transactions. C’est de là que nait l’idée de bloc. 
Un bloc est un ensemble de transactions réunies ensemble. L’idée est qu’au lieu d’enregistrer les transactions une par une au risque d’avoir des conflits sur l’ordre de leur réception. On enregistre les transactions dans un bloc, et on décide de laisser du temps entre deux blocs successifs (par exemple 10 minutes par blocs pour le Bitcoin)
Dans un bloc il est impossible que les 2 transactions “Alice —> Alice2 5.0 BTC” et “Alice —> Bob 5.0 BTC” coexistent puisqu’elles sont contradictoires, on ne peut dépenser de l’argent deux fois dans 2 transactions différentes. 
Les blocs résolvent donc le problème de succession des transactions et du double spending. Puisque une et seulement une seule de nos 2 transactions peut exister dans le bloc, il n y’a pas de différend entre les noeuds du réseau. 
—> Si le réseau choisit d’inclure la transaction “Alice —> Alice2 5.0 BTC” alors Bob n’aura pas reçu son argent et n’enverra pas l’objet vendu. 
—> Si le réseau choisit d’inclure la transaction “Alice —> Bob 5.0 BTC” alors Bob peut être confiant qu’il a bien reçu l’argent et qu’il n’y a pas d’autres noeuds qui considèrent le contraire. 
Le registre n’est donc plus une succession de transactions, mais plutôt une succession de Blocs. D’où le nom Blockchain

La dernière question est : Qui construit les blocs ? Comment décide-t-on du prochain bloc dans la blockchain ? 

Quelques utilisateurs appelés mineurs se donnent la tache de construire les blocs en échange d’une récompense. A tout instant t , il existe un ensemble de transactions non confirmées appelé transaction pool. Ces transactions attendent d’être incluses dans un bloc pour qu’elles soient validées. Un mineur choisit parmi ces transactions pour construire son bloc.
Les transactions font inclure parfois des frais pour les mineurs pour les encourager à les sélectionner, donc naturellement les mineurs sélectionnent les transactions avec les plus grands frais et si leur bloc est choisi, ils gagnent tout les frais de transactions, en plus des nouveau Bitcoins sont créés spécialement pour les mineurs pour les récompenser de leur travail. 
Mais construire un bloc est la partie facile. Puisque plusieurs mineurs construisent chacun leur propre bloc. Comment faire pour décider quel bloc sera le suivant dans la blockchain ? 
Le système créé pour cela est similaire à une loterie. C’est le mineur qui gagne la loterie qui gagne le droit d’inclure son bloc et gagne -beaucoup- d’argent dans le processus. Tout les autre blocs des autres mineurs sont ignorés, ils doivent recommencer avec des nouveaux blocs ne contenant pas les transactions qui viennent d’être validées dans le bloc qui vient de gagner, et espérer gagner la prochaine loterie dans 10 minutes. 
En même temps, tout les autres noeuds (mineurs ou non) font inclure le nouveau bloc créé dans leur registre. 

Le système de loterie est en fait un problème de calcul (Proof of Work). Il faut deviner une certaine chaine de caractère qui permet de résoudre un problème cryptographique. Ce problème dépend du bloc précédent dans la chaine. Donc il ne peut être résolu au préalable, ce qui permet d’éviter les fraudes (cherchez Attaque des 51% si cela vous intéresse). 
Plus un mineur possède une grande capacité de calcul plus il augmente ses chances de résoudre le problème. Et le premier à résoudre le problème broadcast la solution au reste du réseau. Il faut savoir que le problème est extrêmement difficile à résoudre, mais il est facile à vérifier qu’une solution est correcte (fraction de seconde). 
Résoudre le problème nécessitera des années à un ordinateur normal. Mais étant donné la capacité de calcul cumulée de tout les mineurs, la solution est trouvée en 10 minutes en moyenne. 
Le premier à trouver la solution broadcast celle-ci au reste du réseau, qui peut donc arrêter sa recherche de solution, et désigne le mineur ayant trouvé la solution comme vainqueur. Le bloc de ce mineur est sélectionné par consensus. 
Et un nouveau problème qui dépend du bloc fraichement adopté doit être résolu pour sélectionner le prochain bloc. 
Si la puissance de calcul du réseau devient très grande, on augmente automatiquement la difficulté du problème pour que celui-ci soit résolu en 10 minutes en moyenne. 
Le temps de 10 minutes est un compromis entre sécurité (plus le temps de validation est grand plus le réseau est sécurisé) et convenance (on ne veut pas attendre une heure pour que les transactions soient validées)

Tout cela étant dit. Quels sont les avantages du Bitcoin et de la Blockchain ? 
Voici quelques avantages 

Transactions irréversibles (Pas de rétrofacturation)
Moins de paperasse 
Déflationiste (les banques centrales fixent annuellement un taux d’inflation pour les monnaie fiduciaires, ce qui fait que leur valeur décroit dans le temps. Un taux d’inflation de 3% chaque année signifie que l’argent perd 50% de sa valeur en 23 ans. Les cryptomonnaies basées sur la blockchain s’apprécient avec l’adoption)
Transactions rapides et peu chères
Pas d’intermédiaire ou Partie tierce (Les utilisateurs des banques doivent avoir confiance que leur banque restera honnête et ne décidera pas un jour de s’enfuir avec leur argent) 
Impossible à Controller par le gouvernement  (inflation/ Crise économique : Dans le cas de crises économiques où un gouvernement échoue à maitriser les taux d’inflation et où la monnaie locale se déprécie considérablement, les cryptomonnaies sont un bon moyen de se protéger - Voir crise au Venezuela pour plus d’informations)
Impossible à voler 
Complétement Transparent 
Audit Facile
24h/24 et 7j/7 (Il est très couteux en temps et en argent de faire de l’envoi de l’argent à l’étranger par le biais des banques, à cela s’ajoute les limitations des horaires de travail, des jours fériés et des week-ends. Les décalages horaires entre pays et les week-end différents (oui, certains pays ont des week-end le Jeudi/Vendredi, ou bien les Vendredi/Samedi) 
Démocratie (les cryptomonnaies utilisent un système de vote pour effectuer des changements, souvent cela se traduit par des forks)
Tolérance aux attaques (impossible à détruire car complétement décentralisé) 

Voici encore une autre liste de différence entre Bitcoin et Paypal: 

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Upvotes</th>
      <th>Downvotes</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Totals</td>
      <td>21</td>
      <td>23</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Alice</td>
      <td>10</td>
      <td>11</td>
    </tr>
    <tr>
      <td>Bob</td>
      <td>4</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Charlie</td>
      <td>7</td>
      <td>9</td>
    </tr>
  </tbody>
</table>

Mais la différence principale n’est pas là. Malgré les nombreux avantages que possède le Bitcoin grâce à sa technologie Blockchain. L’idée révolutionnaire réside dans le consensus. Non seulement cette monnaie fonctionne bien dans un environnement où les acteurs ne se font pas confiance. La technologie a été pensée pour un environnement sans confiance. 
Ce n’est aucune des qualités ci-dessus qui rend compte de l’innovation derrière la technologie blockchain. Mais bien le fait de mettre en accord plusieurs individus qui ne se connaissent pas. On devine rapidement que les cas d’utilisation se sont pas limités au simple transfert de monnaie (même si ce service est extrêmement précieux, comme en témoigne le succès de Paypal). 
Enter : Blockchain 2.0 
