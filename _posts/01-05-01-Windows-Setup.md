---
isChild: true
---

## PHP na Windows-e {#windows_setup_title}

PHP je dostupné pre Windows niekoľkými spôsobmi. Môžete si [stiahnuť spustiteľnú verziu][php-downloads] a donedávna bol dostupný aj '.msi' inštalátor, ktorý už nie je podporovaný a posledná verzia je PHP 5.3.0.

Na učenie sa a lokálny vývoj možete použiť zabudovaný webserver v PHP 5.4, ktorý nemusíte konfigurovať. Ak chete "všetko v jednom", vrátane plnohodnotného web serveru a MySQL, nástroje ako [Web Platform Installer][wpi], 
[Zend Server CE][zsce], [XAMPP][xampp] a [WAMP][wamp] vám pomôžu rýchlo pripraviť prostredie pre vývoj na Windowse. Tieto nástroje však môžu byť trochu iné ako produkčné, preto dávajte pozor na rozdiely v prostredí ak pracujete na Windowse a nasadzujete do produkcie na Linuxe.

Ak potrebujete produkčný sytém s Windowsom, IIS7 vám poskytne najväčšiu stabilitu a najlepší výkon. Môžete použiť [phpmanager][phpmanager] (plugin pre IIS7) na zjednodušenie konfigurácie a manažovania PHP. IIS7 obsahuje zabudované FastCGI pripravené na použitie, stači zaregistrovať PHP ako obsluhovaciu aplikáciu. Pre podporu a viac informácií je [vyhradená časť na iis.net (EN)][php-iis] pre PHP.

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
