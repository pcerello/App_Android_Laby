# Architecture d'un projet sous Android Studio

**Sommaire**

* [Structuration globale](#structuration-globale)
* [Composants: présentation générale](#composants-présentation-générale)
* [Interactions: présentation générale](#interactions-présentation-générale)
* [Le fichier AndroidManifest.xml](#le-fichier-androidmanifestxml)
* [Les ressources](#les-ressources) 
    * [strings.xml et internationalisation](#stringsxml-et-internationalisation)
    * [La classe R : utilisation des ressources en Java](#la-classe-r--utilisation-des-ressources-en-java)
    * [Utilisation des ressources en XML](#utilisation-des-ressources-en-xml)

---

## Structuration globale

* dossier `Java`: code source (Java) du projet
* dossier `res`: ressources du projet
    * sous-dossier `layout`: mises en page des écrans de l'application et menus
    * sous-dossier `mipmap`: icônes
    * sous-dossier `values`: données constantes

---

## Composants: présentation générale

* Les activités [Activity](https://developer.android.com/guide/components/activities.html): écran avec une interface utilisateur et un contexte
* Les services [Service](https://developer.android.com/guide/components/services.html): composant sans écran, qui tourne en fond de tâche (lecteur de musique, téléchargement, ...)
* Les fournisseurs de contenu [ContentProvider](https://developer.android.com/guide/topics/providers/content-providers.html): Entrée/Sortie sur des données gérées par le système ou par une autre application
* Des récepteurs d'intentions [BroadcastReceiver](https://developer.android.com/reference/android/content/BroadcastReceiver): récupération d'informations générales, arrivée d'un sms, batterie faible, ...

---

## Interactions: présentation générale

* Les intentions [Intent](https://developer.android.com/guide/components/intents-filters.html)
    * Permet d’échanger des informations entre composants
    * Démarrage d’un composant en lui envoyant des données
    * Récupération de résultats depuis un composant
    * Recherche d’un composant en fonction d’un type d’action à réaliser
* Les filtres d'intentions [intent-filter](https://developer.android.com/guide/components/intents-filters)
    * Permet à un composant d'indiquer ce qu'il sait faire
    * Permet au système de sélectionner les composants susceptibles de répondre à une demande de savoir-faire d’une application

---

## Le fichier [AndroidManifest.xml](https://developer.android.com/guide/topics/manifest/manifest-intro.html):

Il s’agit d’une description globale de l'application contenant
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

## Les ressources 

Ce sont toutes les données (autres que le code) utilisées par l'application: [documentation](https://developer.android.com/guide/topics/resources/index.html). Elles sont rangées dans le dossier `res`, puis incluses dans l'exécutable (fichier `apk`) lors de la compilation:
* `res/drawable` et `res/mipmap` (images en différentes résolutions)
* `Layout` (description en XML des interfaces)
* `Menus` (description en XML des menus)
* `Values` (définitions en XML des constantes utilisées par l'application : chaînes, tableaux, valeurs numériques

---

### strings.xml et internationalisation

Fichier ressources, contenant toutes les chaînes constantes [(documentation)](https://developer.android.com/guide/topics/resources/localization.html).

Exemple
```xml
<resources>
    <string name="app_name">MyApplication</string>
    <string name="hello_world">Hello world!</string>
    <string name="action_settings">Settings</string>
</resources>
```

L’internationalisation est assez simple: il s’agit de disposer de plusieurs versions des textes, libellés, utilisés par l'application.
Le choix sera alors automatique en fonction de la configuration du périphérique

En pratique, il faut :
* dupliquer le fichier `strings.xml` : une version par langue supportée
* stocker chaque version dans un dossier spécifique `values-xx` (ex. `values-en`, `values-fr` …)

Ceci est grandement facilité par l’IDE Android Studio (cf [TP](../phases/phase01.md)).

---

### La classe R : utilisation des ressources en Java

Cette classe est générée automatiquement lors de la compilation de l’application, et permet l'accès aux ressources depuis du code java  [(documentation)](https://developer.android.com/guide/topics/resources/accessing-resources.html).

Elle contient des classes internes dont les noms correspondent aux différents types de ressources (`drawable`, `layout`, …) ainsi que des propriétés permettant de représenter l'ensemble des ressources de l'application.

Utilisation en  `Java` : `R.type.identificateur`

Exemple: pour le fichier de ressources suivant,
```xml
<resources>
    <string name="app_name">MyApplication</string>
    <string name="hello_world">Hello world!</string>
<string name="action_settings">Settings</string>
</resources>
```

la ressource `hello_world` a pour référence `R.string.hello_world` en Java.

---

### Utilisation des ressources en XML

La forme générale d’utilisation des ressources dans les fichiers `xml` est : `@type/identificateur`

Dans l'exemple précédent, la ressource `hello_world` a pour référence XML `@string/hello_world`.
