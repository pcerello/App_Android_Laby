# Introduction à la programmation Android

* *auteurs* : Stéphane Fossé (auteur principal), Arnaud Pêcher
* *date*: 29/11/2022

---

# Présentation

Android est un système d'exploitation à destination des dispositifs mobiles (téléphones, tablettes, téléviseurs, montres, lunettes, voitures, casques de réalité virtuelles ...).

Ses principales caractéristiques sont :
* Open Source1 (licence Apache), gratuit, flexible, basé sur un noyau linux.
* Inclusion des applications de base (téléphone, sms, carnet d'adresse, navigateur, etc.)
* Un ensemble important d'API (OpenGL, media, etc …)
* Un SDK basé sur un sous-ensemble de JAVA (autres langages disponibles : C, C++, …)
* Une machine virtuelle spécifique qui exécute la majorité des applications

Historiquement, Android a été créé en 2005 par la société Android, puis rachetée en 2007 par Google.

Sa part de marché en 2016 était de 80% ( 18% pour IOS)

---

# Les contraintes de la programmation mobile

* Hétérogénéité du matériel, Processeurs …
* Puissance et mémoire limitées
* Interface tactile
* Taille de l’écran
* Connectivité à internet (disponibilité, rapidité, ...)
* Développement (souvent) extérieur au périphérique

---

# Architecture d'un projet sous Android Strudio

---

## Structuration globale

* dossier `Java`: code source (Java) du projet
* dossier `res`: ressources du projet
    * sous-dossier `layout`: mises en page des écrans de l'application et menus
    * sous-dossier `mipmap`: icônes
    * sous-dossier `values`: données constantes

## Composants: présentation générale

* Les activités [https://developer.android.com/guide/components/activities.html](Activity): écran avec une interface utilisateur et un contexte
* Les services [https://developer.android.com/guide/components/services.html](Service): composant sans écran, qui tourne en fond de tâche (lecteur de musique, téléchargement, ...)
* Les fournisseurs de contenu [https://developer.android.com/guide/topics/providers/content-providers.html](ContentProvider): Entrée/Sortie sur des données gérées par le système ou par une autre application
* Des récepteurs d'intentions (BroadcastReceiver) Récupération d'informations générales, arrivée d'un sms, batterie faible, ...

## Interactions: présentation générale



---

# Références principales

* https://developer.android.com/index.html