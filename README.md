# notes-devfest-nantes-2018
Ce projet contient les notes que j'ai pris durant le DevFest 2018 à Nantes.

<p align="center">
  <img height="250" src="/static/DevFest_banner.png">
</p>

## Jour 1

### :a: Ready for Angular version 8?
Présentation des dernières features de angular 8 comme par exemple le nouveau system de build, le Material CDK de angular Material,et le nouveau moteur de rendu.  
  - **BAZEL** est le nouveau système de build d'angular. Il est plus rapide, scalable et polyglotte (mutli-langage).
  - **Schematics** est une extension du CLI, il permet de réaliser des template personnalisé et réutilisable.
  - **Material CDK**: le component dev kit de material est disponible et permet d'utiliser la partie contrôleur de AngularMaterial sans la couche graphique
  - **IVY** est le nouveau moteur de rendu d'Angular il permet un debugging plus simple, de plus petits scripts une fois compilé, et une compilation plus rapide. Ivy est rétro compatible avec l'ancien moteur  
<p align="center">
  <img height="250" src="/static/IVY_size.png">
</p>

### :cloud: Les nouveautés "serverless" de Google Cloud
Découverte des nouveautés "serverless" de Google. L'App Engine et Cloud Functions, ou comment créer une application en se focalisant sur son code et de laisser la tache de scaling à Google.  

Le paiement se base sur la consommation et n'a donc pas de prix fixe.  

Nouveautés de l'app engine runtime : node 8, python 3.7, PHP 7.2, go 1.11, Java 8.Nouveautée des cloud fonction : python 3.7, node 8, variables d'environnement, security contrôle : VPC, IAM, cloud SQL direct connect, scaling controls  
Possibilité d'utiliser de n'importe quel framework/librairie.  
Nouveautés des cloud fonction : python 3.7, node 8, variables d'environnement, security contrôle : VPC, IAM, cloud SQL direct connect, scaling controls  
Possibilité d'utiliser des containers pour exécuter des programmes qui ne sont pas disponibles au runtime sur le Google cloud par exemple Rudy ou blender(logiciel de rendu 3D).   

Cette présentation était basée sur une application nommée [*Sharing pictures*](https://pic-a-daily.appspot.com/) dont voici l'architecture  
<p align="center">
  <img height="350" src="/static/demo_app_serverless.png">
</p>

### :mag: Deliver search-friendly JavaScript-powered websites
Problématique, comment référencer son application alors que 90% de son contenu est chargé par du JS.

Rappel sur le fonctionnement d'un moteur de recherche :
  - **Crawling** : parcours des urls disponibles sur le site web, piloté par le robots.txt
  - **Indexing** : codes HTTP, indexation du contenu des pages, parcours des liens pour crawler à nouveau

Une page index.html d'une application JS contient généralement qu'une balise ```<app></app>```, les données sont chargées en JS

La solution proposée est le : Google bot.  
L'indexation se passe en deux temps, d'abords l'url de base puis le contenu généré grace au JS

Notes : Veiller à bien utiliser les bon code de retours HTTP, par exemple le 404 en cas de contenu non trouvé

### :desktop_computer: Machine Learning & JS : Take your PWA to the next level
Comment pousser sa PWA (progressive web app) au niveau supérieur grâce au machine learning. Découverte des solutions disponibles pour intégrer le machine learning dans son navigateur.  

Pourquoi faire du Machine learning dans son navigateur ?  
  - Meilleur accès et distribution
  - Données personnel non partagées
  - Model distribué
  - Pas d'installation requise
 
 Voici les performances de tensorflow.js, tensorflow.js utilise le GPU (WebGL) pour faire ces calculs  
<p align="center">
  <img height="250" src="/static/perfs_tensor_flow.js.png">
</p>

## Jour 2
### :deciduous_tree: Git Dammit!
Talk sur les problèmes les plus souvent rencontrés sur Git, problèmes expliqué avec des cas d'usages et illustrés par des démos.

Nouvelle metric : le TDM : T'a deux minutes? (j'ai une probleme avec GIT)  

Les bonnes pratiques sont : 
  - On tire une branche
  - On fait un ou plusieurs commits
  - On soumet sa branche à une revue de code

Quelque commandes en vrac :
  - Corriger le commit précédent
  ```$ git commit --amend```
  - Corriger un commit n'étend pas le précédent  
  ```git commit -fixup A``` A est le SHA-1 du commit à corriger  
  ```git rebase -i A~ --autosquash```  
  ```git force push``` 
  - Supprimer un commit
  ```git reset HEAD~ --soft``` : On garde les modifs, indexées  
  ```git reset HEAD~ --mixed``` : On garde toujours les modifs mais non indexées  
  ```git reset HEAD~ --hard``` : On supprime toutes les modifs  
  - Revenir sur la branche precendante  
  ```git checkout -``` : Comme "cd -" en shell  

[Lien de la présentation](https://mghignet.github.io/git-dammit-talk/ )

### :memo: How do we use Vue.js in GitLab?
retour d'expérience des développeurs de chez gitlab sur leur utilisation de vueJS.

Pourquoi gitlab à choisi vueJS?  
  - ils ne possédaient pas npm et Webpack sur leur stack Frontend  
  - pas le temps de réécrire le code existant  
  - c'est un framework *progressif*  
  - plus petit et plus rapide  
  - Facile à apprendre  
  - Bon éco-system et une bonne communauté  
  - Open Source  
Les développeurs de chez gitlab font cohabiter leur code legacy (jquerry/JS pure) avec le nouveau code de vueJS.
### :building_construction: Vanilla JS 2018
Présentation du projet 'bac à sable' Vanilla JS 2018, un projet devant répondre à quelques contraintes :
  - pas de source externe  
  - un maximum de nouvelles normes  
  - minimum 2 navigateurs peuvent supporter le projet  
  
 
### :alien: Détectez et trackez les aliens qui se cachent dans vos dépendances
44% des applis contiennent des vulnérabilités, pas par leur code mais dans les librairies open-source qu'elles utilisent.  
démo sur comment créer un pipeline de Continuous Security dans Jenkins au moyen de OWASP DependencyCheck qui détecte les vulnérabilités comment les traquer grâce à OWASP DependencyTrack.

**Démo** : Découverte d'une faille dans Spring Data REST permettant de créer un explorateur de fichiers se trouvant sur le serveur par le biais de son navigateur.  

Utilisation de Jenkins avec le plugin OWASP DependencyCheck pour analyser les failles de sécurité dans les dépendances du projet et corrections de la faille. Les rapports peuvent etre envoyé dans slack/teams ou visible dans OWASP DependencyTrack.
