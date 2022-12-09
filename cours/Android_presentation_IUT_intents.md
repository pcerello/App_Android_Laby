# Les intentions

**Sommaire**

* [Les intentions](#les-intentions)
    * [Les intentions explicites](#les-intentions-explicites)
    * [Les intentions implicites](#les-intentions-implicites)
    * [Récupération](#récupération)
    * [Intention avec résultats (émetteur)](#intention-avec-résultats-émetteur)
    * [Intention avec résultats (récepteur)](#intention-avec-résultats-récepteur)
* [Les données](#les-données)
* [Les extras](#les-extras)
* [Les filtres : intent filters](#les-filtres--intent-filters)

---

# Les intentions

Un « intent » est une classe représentant un message échangé entre une activité et
* Une autre activité
* Un service
* Un diffuseur d'événements.

Deux types de messages sont possibles:
* Explicite : on nomme le composant à démarrer
* Implicite : on demande au système de trouver un composant adéquat, en fonction d'une action à effectuer. L’utilisateur devra choisir.

---

## Les intentions explicites

Il s’agit d’un message adressé à un composant connu. On doit ainsi spécifier le nom de la classe correspondante.

On utilise généralement ce type d’appel aux composants appartenant à la même application …

On utilise la méthode `startActivity(intent)`.

```java
Intent = new Intent() ;
Intent.setClassName(this, SecondActivity.class) ;
startActivity(intent) ;
```

---

## Les intentions implicites

Il s’agit d’un message à destination d'un composant inconnu
* Le système se charge de trouver le composant adéquat et le lance
* En cas de possibilités multiples, il affiche les choix à l'utilisateur

```java
Intent intention = new Intent (…) ;
startService(intention) ;
```

---

## Récupération

Coté récepteur (dans la méthode `onCreate()` de l’activité appelée):

```java
public void onCreate (Bundle savedInstanceState) {
    Intent intention = getIntent () ;
}
```

---

## Intention avec résultats (émetteur)

```java
void maFonction(...) {
    Intent intention = new Intent (…) ;
    startActivityForResult(Intent intention, int requestCode) ; 
}

// methode appelee lorsque l'activité appelée a terminé
protected void onActivityResult (int requestCode, int resultCode, Intent data){ 
    …
}
```

`requestcode` : Code créé par le développeur pour identifier de manière unique son intention (>0)

```java
public static final int CODE = 4 ;
```

`resultCode`: code de retour d'exécution de l'intent
```java
Activity.RESULT_OK
Actvity.RESULT_CANCELED
```

intention `data`: données transmises en retour par l'activité appelée

---

## Intention avec résultats (récepteur)

```java
public void onCreate (Bundle savedInstanceState){
    // récupérer l'intent
    Intent intention = getIntent () ;
    // extraire les données et les traiter
    // créer l'intent résultat
    Intent resultat = new Intent();
    // ajout des résultats
    setResult(RESULT_OK, resultat);
    finish();
}
```

Il y a de nombreuses constantes prédéfinies dans la classe `Intent` :
* `ACTION_MAIN` : démarre l'activité comme point d'entrée principal
* `ACTION_VIEW` : affiche les données fournies à l'utilisateur
* `ACTION_EDIT` : permet l'édition des données fournies par l'utilisateur
* `ACTION_SEND` : permet l'envoi des données (mail, réseau social, ...)

---

## Les données

Les données sont formatées à l'aide des URI (Uniform Ressource Identifier)
* Chaîne de caractères représentant un endroit ou une ressource
* Syntaxe normalisée : `<Schéma> : <information> [? <requêtes> ][ # <fragment> ]`

Nature de l'information (schéma) : http, https, content, geo, file tel , voicemail, sms,smsto, mms, mmsto

L'information dépend du schéma:
```
tel:06000007
geo:123.456,12.3456
http://www.google.fr
```

Exemple:

```java
Intent intention = new Intent() ;
Uri sms = Uri.parse("sms:06000007") ;
Intention = intention.setData(sms) ;
```

---

## Les extras

Les extras permettent d'insérer des données dans l'intention.

La structure des extra est : 
```java
Intent.putExtra(String cle, type valeur) ;
```

Pour récupérer l’extra : 

```java
type get{type}Extra(String cle, type vdefaut) ;
```

Exemple:

```java
public class mainActivity extends Activity {
    public final static String MARQUE = " MARQUE" ;
    public final static String PUISS = "PUISS" ;
    …I
    
        Intent intention = new Intent(this, otherActivity.class) ;
        String marque = "Citroen" ;
        int puissance = 6 ;
        intention.putExtra(mainActivity.MARQUE, marque) ;
        intention.putExtra(mainActivity.PUISS, puissance) ;
        startActivity(intention) ;
    …}

```

```java
public class otherActivity extends Activity{
    …I
        Intent intention = getIntent() ;
        int p = intention.getIntExtra(mainActivity.PUISSANCE, 0) ;
        String m = intention.getStringExtra(mainActivity.MARQUE) ;
    …}
```

---

# Les filtres : intent filters

Le système doit connaître les types d'intents que peut recevoir chaque composant. Il est donc nécessaire de préciser pour chaque composant les intents possibles.

Les intent filters sont précisés dans le fichier `manifest.xml` pour chaque composant d'un application.

Leur syntaxe est :

```xml
<composant ...>
    <intent-filter>
        <action android:name="..." />
        <category android:name="..." />
        <data android:mimeType="..." />
    </intent-filter>
</composant>
```

Le composant principal d'une application doit apparaître dans la liste des applications pouvant être lancées :
```xml
<intent-filter>
    <action android:name="android.intent.action.MAIN" />
    <category android:name="android.intent.category.LAUNCHER" />
</intent-filter>

```
