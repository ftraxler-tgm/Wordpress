# Wordpress


## Installation
[Installation von Wordpress](install.md)

## Bootstrap Theme entwicklen
Nach folgender Anleitung vorgehen um ein einfaches Bootstrap Theme zu erstellen.
[Wordpress-Bootstrap](http://blog.teamtreehouse.com/responsive-wordpress-bootstrap-theme-tutorial)
Man kann aber auch das gesamte Zip herunterladen und in den **wp-content/themes/** Ordner ziehen.
Das Zip ist unter folgendem Link verfügbar. [Wordpress-Zip](https://3wga6448744j404mpt11pbx4-wpengine.netdna-ssl.com/wp-content/uploads/2012/10/wpbootstrap.zip)

Sehr hilfreich war der Debug Methode welchen man im **wp-config.php** File einschalten kann unter:
```php
define( 'WP_DEBUG', true );
```


## NavBar erstellen
Dafür habe ich mir aus einem anderen Theme die **navwalker.php** Datei geholt.
Damit dieses auch geladen wird müssen wir dem **functions.php** File folgendes hinzufügen.
```php
require_once('wp_bootstrap_navwalker.php');

// Theme Support
  function wpb_theme_setup(){
    // Nav Menus
    register_nav_menus(array(
      'primary' => __('Primary Menu')
    ));
}

add_action('after_setup_theme','wpb_theme_setup');

```