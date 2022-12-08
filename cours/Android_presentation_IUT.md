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
* Des récepteurs d'intentions (BroadcastReceiver): récupération d'informations générales, arrivée d'un sms, batterie faible, ...

## Interactions: présentation générale

* Les intentions [https://developer.android.com/guide/components/intents-filters.html](Intent)
    * Permet d’échanger des informations entre composants
    * Démarrage d’un composant en lui envoyant des données
    * Récupération de résultats depuis un composant
    * Recherche d’un composant en fonction d’un type d’action à réaliser
* Les filtres d'intentions (`<intent-filter>`)
    * Permet à un composant d'indiquer ce qu'il sait faire
    * Permet au système de sélectionner les composants susceptibles de répondre à une demande de savoir-faire d’une application

## Le fichier AndroidManifest.xml

Il s’agit d’une description globale de l'application [https://developer.android.com/guide/topics/manifest/manifest-intro.html](contenant):
* La liste des composants de l’application.
* Le niveau minimum de l'API requise.
* La liste des caractéristiques physiques nécessaires: gestion de la visibilité sur Google Play
* La liste des autres API nécessaires (Google Map… )

Ce fichier est généré automatiquement par Android Studio (l'IDE utilisé pour développer sous Android)

Exemple de fichier `AndroidManifest.xml` :
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android=http://schemas.android.com/apk/res/android package="fr.me.com" >
    <application android:allowBackup="true" android:icon="@mipmap/ic_launcher" android:label="@string/app_name" android:theme="@style/AppTheme" >
        <activity android:name=".MainActivity" android:label="@string/app_name" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```
---
---

---

# Références principales

* https://developer.android.com/index.html