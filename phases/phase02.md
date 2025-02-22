# Phase 02 : projet

* *auteurs* : Arnaud Pêcher
* *date*: 03/01/2023

---

Pendant cette seconde phase, vous allez réaliser une application Android complète.

---

## Spécifications

* réalisation par binôme
* le nom du projet doit être `Nom1Nom2`
* une démo est disponible: [LabyPOC.apk](../demo/LabyPOC.apk)

---

## Sujet : application labyrinthe

Il s'agit de réaliser une application permettant de se déplacer dans un labyrinthe: le code effectué pendant le [projet de reprise](https://moodle1.u-bordeaux.fr/course/view.php?id=8869) pourra être réutilisé. L'incorporation des monstres est optionnelle.



### Partie principale

Concrètement, l'application devra
* avoir une activité (ou fragment) permettant de sélectionner un labyrinthe parmis plusieurs;
    * les labyrinthes seront inclus dans l'application sous la forme de fichiers texte au même format que pour le projet de reprise;
    * il est possible de réutiliser les labyrinthes fournis dans le projet de reprise.
* avoir une activité (ou fragment) affichant le plan général du labyrinthe avec la position du héro sur celui-ci, ainsi que l'entrée et la sortie;
* avoir une activité (ou fragment) prenant le charge le jeu proprement dit en affichant les salles autour du héros et en permettant au héros de se déplacer dans le labyrinthe.

Des messages informeront l'utilisateur 
* du chargement réussi d'un labyrinthe;
* du début d'une partie;
* de la réussite (arrivée dans la salle de la sortie) .

### Partie optionnelle 

Vous avez toute lattitude pour rajouter des fonctionnalités. 

Voici quelques propositions en vrac:
* [facile] gestion des scores et des meilleurs scores (le score diminue à chaque consultation de la carte globale et à chaque déplacement);
* [facile] prise en charge des paramètres du projet;
* [facile] salles avec des trésors ou des pièges;
* [moyen] plusieurs niveaux avec passage d'un niveau à l'autre avec des escaliers dans la carte;
* [moyen] incorporation de monstres (voire la réalisation d'un pacman);
* [difficile] affichage fluide des déplacements fluides (scrolling);
* [difficile] affichage en 3d dans la vue permmettant de se déplacer;
* [difficile] mode multi-joueur avec un serveur externe.

---

## Modalités de remise

* une archive du projet au format zip à remettre sur Moodle:
    * nom de fichier de l'archive: `Nom1Nom2.zip`
    * nom du dossier (du projet AndroidStudio): `Nom1Nom2/`
    * après extraction, le dossier du projet doit pouvoir être ouvert sous AndroidStudio sans erreur 
* date limite: **lundi 13/03/2023** 
