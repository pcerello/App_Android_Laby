# Les menus

## Menu d'une application

[Documentation](https://developer.android.com/guide/topics/ui/menus.html)

Exemple:

```xml
<?xml version="1.0" encoding="utf-8"?>
    <menu xmlns:android="http://schemas.android.com/apk/res/android">
        <item android:id="@+id/file" android:title="@string/file" >
            <!-- "file" submenu -->
            <menu>
                <item android:id="@+id/create_new" android:title="@string/create_new" />
                <item android:id="@+id/open" android:title="@string/open" />
            </menu>
        </item>
    </menu>
```

et dans l'activité :

```java
@Override
public boolean onCreateOptionsMenu(Menu menu) {
    MenuInflater inflater = getMenuInflater();
    inflater.inflate(R.menu.game_menu, menu);
    return true;
}
```

---

## Menu contextuel

Procédure:

1. Enregistrer le `View` auquel le menu contextuel devrait être associé en
appelant `registerForContextMenu()` et transmettre le `View` dans la méthode `oncreate`
2. Implémenter la méthode `onContextItemSelected`

cf la [documentation](https://developer.android.com/guide/topics/ui/menus.html).

Exemple:

```java
@Override
public boolean onContextItemSelected(MenuItem item) {
    AdapterContextMenuInfo info = (AdapterContextMenuInfo) item.getMenuInfo();
    switch (item.getItemId()) {
        case R.id.edit:
            editNote(info.id);
            return true;
        case R.id.delete:
            deleteNote(info.id);
            return true;
        default:
            return super.onContextItemSelected(item);
    }
}
```