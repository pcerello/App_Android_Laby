# Les permissions

Les [permissions](https://developer.android.com/guide/topics/security/permissions.html) permettent de restreindre ce qu'une application a le droit de faire, de protéger les données présentes sur le périphérique.

Par défaut, impossibilité d'impacter une autre application, le système ou les données utilisateur car chaque application est lancée dans son propre espace.

Il est donc nécessaire de préciser les permissions demandant une validation par l'utilisateur.

On a deux groupes de permissions
* Normales, sans risque pour l’utilisateur, qui sont attribuées directement par l’application
* Dangereuses (lire les contacts…) qui nécessitent une validation de l'utilisateur.

Les permission se définissent dans le fichier manifest.xml en utilisant la balise `<uses-permission>`.

Exemple:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="fr.SF " >
    <uses-permission android:name="android.permission.RECEIVE_SMS" />
</manifest>
```

À noter que depuis la version 6.0, il est possible de gérer les permissions de façon programmatique à l’exécution de façon individuelle, plutôt qu’à l’installation de façon complète (l’utilisateur peut refuser certaines permissions et faire tourner l’application sans que toutes les permissions ne soient acceptées: [documentation](https://developer.android.com/training/permissions/requesting.html)).