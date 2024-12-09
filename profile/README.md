# Sigment

accedez à sigment directement depuis le lien suivant : http://5.250.177.82:8080

## Qu'est ce que Sigment ?

Le projet Sigment vise à transformer la mobilité douce en outil de redécouverte et de lien social.

Le projet Sigment ne se limite pas à une plateforme régionale pour les institutions : c’est une démarche globale et innovante qui révolutionne le tourisme.
Ce que Sigment propose :
-  Préservation durable : Grâce à l’IA, détectez les signes de dégradation des lieux touristiques pour protéger durablement les sites sensibles.
- Gestion intelligente des flux : Identifiez les périodes d’affluence et découvrez des alternatives pour des visites plus sereines.
- Découverte enrichie : Explorez une carte interactive mettant en avant les sites naturels, culturels et événements locaux.
- Aventure immersive : Transformez vos explorations en jeu ! Gagnez des badges pour chaque découverte, accédez à des récits historiques et plongez dans des expériences en réalité augmentée.
- Recommandations personnalisées : Bénéficiez de suggestions d’itinéraires et de points d’intérêt basées sur vos goûts et celles d'autres voyageurs.
- Accessibilité pour tous : Profitez de parcours adaptés, qu’il s’agisse de boucles thématiques, voies sécurisées ou parcours dédiés aux personnes à mobilité réduite. Des audioguides et descriptions détaillées simplifient vos visites.

Notre promesse : Avec Sigment, participez à un tourisme intelligent et durable en Normandie. Vos données personnelles sont une clé pour co-construire une expérience qui allie préservation et innovation. 

## l'architecture de l'environnnement de Sigment 

Le projet Sigment est un projet multi applications basées sur une API, cette dernière prend en charge plétores de endpoint servant à la manipulation du jeu de données nécéssaire au fonctionnemnts des différentes applications frontend accessibles depuis notre landing page (index.html du repository front_shared : https://github.com/MPIA24/front_shared)
La première de ces application est une gaming app, déclinable en version application mobile ou web app (responsive app) et ceux avec un seul et unique compte (car toutes les données transitent par la même API). aujourd'hui cette gaming app propose une carte offrant la possibilité d'afficher les différents points d'intérets touristiques en Normandie ainsi que différents itinéraires. la gaming app propose également la fonctionnalité de visite des batiments et itinéraires ainsi que l'obtention de badges associés. enfin la gaming app propose la mise en avant de certains evennements temporaire et permettant l'obtention de badges exclusifs.
Demain nous prevoyons que cette gaming app offre bien plus de fonctionnalités, en voici une liste non exhaustive : 

- map a visibilité évolutive (un peu comme dans un jeu RPG ou l'on doit découvrir la map petit à petit)
- affichage détaillé sur l'accessibilité des POIs (accès PMR)
- proposition d'élaboration d'itinéraires passant non plus seulement par des POI mais également par des points gastronomiques et d'hébergements
- affichage des avatars des autres utilisateurs sur la map
- personnalisation poussé des avatars, cosmétiques associé déblocable via les badges débloqués.
- proposition de visite guidé par storytelling sur thème particuliers
- visite immersive a distance (via de la reconstruction de monuments en 3D ainsi que la génération de speech via IA)

cette gaming app est une application qui se devra d'etre gratuite, l'interet étant ici de récupérer des données d'utilisations pertinentes pour afficher sur la deuxieme partie de Sigment, le dashboard.

Le dassboard est davantage destiné aux institutions et entreprises du secteurs (bien qu'accessible de tous via une connexion classique). actuellement la game app ne renvoi que de simples données de passage sur les différents POI sans permettre de croiser d'autres données. de ce fait le dashboard ne propose d'afficher que deux cartes statistiques, la première étant une carte statique des différents POI en normandie recensé. la seconde, un peu plus pertinent met en relation ces POI et le nombre de visites effctués dans la game app permettant d'avoir un aperçu de fréquentation en temps réel des différents POI de Normandie. Demain nous prévoyons d'exploiter pleinement les données récupérées de la front app afin de pouvoir recolter et traiter des données en temps réelle d'utilisation pertinentes. Nous prevoyons notement de proposer un systeme de verification des visites des POI par une photographie du lieu, cela permettra de regrouper une base de photographie des POI conséquente qui permettra a minima deux choses, premièrement, la génération de modèle 3D des POI et alentours mais également un suivi assité par IA de l'état de conservation des POI (permetant plus facilement un ajustement des entretiens de ces derniers). il s'agit la d'une simple utilisation de la données récoltés mais Sigment se veut etre un application communautaire, faites par tous et pour tous, les données seront donc mises à dispositions de tous (format open data) avec des accès au endpoint de lecture de l'API ouverts notemment.

## Installer sigment sur votre machine et commencer à l'utiliser 

Attention, pour installer et utiliser sigment corectement vous aurais besoin de php 8.2 (minimum), composer, sqlite3 (décoché dans le php.ini) ainsi que git pour l'import facilité. 

### 1. cloner l'API et la lancer en serveur local : 

Tout d'abord lancez VScode, ou votre éditeur de texte favoris, et lancez également un terminal (bash, zsh, powershell etc...) puis effectuer la commande suivante : 

```bash

git clone https://github.com/MPIA24/segment_API.git

```
placez vous maintenant dans le bon dossier avec la commande suivante : 

```bash

cd segment_API/

```

puis lancer la commande suivante pour installer les dépendances php nécéssaire à l'execution du script

```bash

composer i

```

une fois les dépendances finis de télécharger, lancez simplement l'api avec la commande suivante : 

```bash

php artisan serve

```

félicitation, si tout c'est bien passé votre serveur php tourne et votre API accepte donc les requetes http depuis le port 8000.

### 2. cloner l'app front 

maintenant que votre API est fonctionnelle, il est temps de lancer votre client (ou frontend). Pour ce faire vous n'aurais besoin que d'une seule extension depuis vs code, le live server (si vous souhaitez passer par une autre solution, c'est possible, néamoins il faudra aller modifier les fichiers de configuration dans l'API pour qu'elle puisse permettre à un autre port que le 5500 du live server d'accéder aux requetes). Si cette condition est requise, vous n'avez qu'une seule commande à effectuer afin de cloner le répo github de la front_shared sur votre machine : 

```bash

git clone https://github.com/MPIA24/front_shared

```

une fois cela fait, rendez vous sur votre vs code et une fois dans le bon dossier (front_shared) lancez simplement votre live server et ouvrez votre navigateur à l'adresse suivante : http://127.0.0.1:5500

vous devriez maintenant voir s'afficher notre landing page, elle vous donnera accès a toutes nos pages mais également à nos deux applications front !
