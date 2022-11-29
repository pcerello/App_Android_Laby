# Phase 01 : environnements de travail et 3d de l'application

* *auteurs* : Stéphane Fossé, Arnaud Pêcher
* *date*: 29/11/2022

---

Ce document décrit les principales étapes à réaliser pendant cette phase.

---

# Déroulement

Liste des exercices:

## Introduction: Création d’une application, Compilation et lancement de l’application

* Exercice 1 : refactoring
* Exercice 2 : string.xml 
* Exercice 3 : internationalisation
* Exercice 4 : icône
* Exercice 5 : test du cycle de vie

## Principales notions d'une application Android

* Exercice 6 : layout et événements
* Exercice 7 : les intentions explicites
* Exercice 8 : les intentions explicites(partie 2)
* Exercice 9 : les intentions implicites
* Exercice 10 : les intentions implicites (parie 2)
* Exercice 11 : Les menus et images
* Exercice 12 : menu contextuels

---

# Exercices

## Introduction: Création d’une application, Compilation et lancement de l’application

### Exercice 5 : test du cycle de vie

Vous allez à présent ajouter à votre application (Activite Principale.java) différentes méthodes du cycle de vie de l’activité et tester leur appel.
Ajoutez un affichage dans la console lorsque la méthode `onCreate()` est appelée ; vous pouvez utiliser pour ce faire un appel à `System.out.println`. Vérifiez qu’au lancement de votre application, cet affichage est bien généré ;
Ajoutez la méthode `onStart()` suivante et de même insérez-y un affichage dans la console permettant de vérifier l’appel de cette méthode.

```java
protected void onStart() {
    super.onStart();
}
```

Compilez et testez ;
Vous pouvez générer automatiquement ces fonctions en utilisant `code->override methods`
Faites de même avec les méthodes `onStop()`, `onRestart()`, `onResume()` et `onPause()` ;
Tester vos méthodes J en utilisant l’émulateur.

---

## Principales notions d'une application Android

### Exercice 6 : layout et événements

Créez un nouveau projet Android « calculatrice »
Modifiez l’activité pour utiliser un layout linéaire vertical.
Réalisez l'interface graphique de la calculette « 4 opérations » directement dans le fichier XML
Associez aux boutons les actions sans implémenter pour le moment les fonctions.
Implémentez maintenant les fonctions pour finir votre application.

### Exercice 7 : les intentions explicites

Créez un nouveau projet Android, puis complétez celui-ci avec les étapes suivantes :
* L’activité principale dispose d'une zone de saisie et d'un bouton d'envoi. Vous testerez cette activité en faisant afficher dans la console le texte présent dans la zone de saisie lors de l'appui sur le bouton d'envoi ;
* Une nouvelle activité dans le même package avec une zone d'affichage dont le contenu initial sera le texte « en attente » (dans le fichier string.xml)

Modifiez les deux activités pour que l'activité principale, lors de l'appui sur le bouton, envoie via une intention le texte saisi à la seconde activité qui l'affichera.

### Exercice 8 : les intentions explicites (partie 2)

Créez un nouveau projet composé de 3 activités :
* L’activité principale présente à l'utilisateur deux parties contenant respectivement :
    * Pour la partie supérieure, des champs correspondant à un nom, un prénom et un numéro de téléphone, ainsi qu'un bouton modifier ;
    * Pour la partie inférieure, une adresse sous la forme des champs numéro, nom de rue, code postal et ville, ainsi qu'un bouton Modifier.
* Une seconde activité, déclenchée par appui du bouton Modifier de la partie supérieure, permettant à l'utilisateur de modifier la valeur des différents champs concernant son identité. Deux boutons seront présents, l'un permettant de valider les modifications saisies (renvoyées à l'activité principale) et l'autre permettant d'annuler ces modifications et de revenir à l'activité principale ;
* Une troisième activité, fonctionnant de manière similaire, sur les informations concernant l'adresse de l'utilisateur.

### Exercice 9 : les intentions implicites

[...]

### Exercice 10 : les intentions implicites (partie 2)

Modifiez votre application de telle sorte qu’elle comporte :
* un champ de saisie permettant de récupérer le numéro de téléphone à utiliser pour les sms, mms et appels ;
* Un champ de saisie pour l’url à ouvrir ;
* Deux champs de saisie pour les coordonnées géographiques (latitude et longitude) d’un lieu à visualiser.

Testez votre application.

### Exercice 11 : Les menus et images

L'objectif de cet exercice est d’écrire une application permettant de charger une image stockée sur le périphérique et de l'afficher.

L’interface sera simplement constituée d’un bouton (pour permettre le chargement) et de l’image.

Dans un premier temps, créez l’interface graphique. Le widget à utiliser pour l’image est ImageView.

Compléter le code de l’application pour gérer l’appui sur le bouton de chargement, en faisant afficher un message dans la console.

Complétez l’application pour qu’elle émette une intention dont l’action sera ACTION GET CONTENT et le type celui correspondant à une image, qu’elle récupère l’image retournée et l’affiche dans le widget correspondant.
* La classe à utiliser pour l’image est ImageView ;
* Pour pouvoir charger une image, votre application doit sans doute disposer d’une permission

Lorsque le chargement de vos images fonctionne, ajoutez des boutons à votre application, permettant d’effectuer
* Un miroir horizontal de l’image
* Un miroir vertical de l’image

### Exercice 12 : menus contextuels

Modifiez votre application de chargement d’images en lui ajoutant un menu qui reprenne les deux opérations de miroirs horizontal et vertical. Lorsque ce menu sera opérationnel, vous supprimerez les deux boutons de l’interface.

Ajoutez un menu contextuel au composant d’affichage de l’image, pour que les deux opérations suivantes puissent être appliquées à l’image :
* Inverser les couleurs de l’image ;
* Transformer l’image en niveaux de gris

---

# Remise
