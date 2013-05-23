---
isChild: true
---

## Composer a Packagist {#composer_and_packagist_title}

Composer je výborný správca závislostí pre PHP. Stačí zapísať zoznam závislostí vášho projektu v súbore `composer.json` a pomocou niekoľkých jednoduchých príkazov Composer automaticky stiahne závislosti vášho projektu a nastaví pre vás autoloader.

Existuje už mnoho PHP knižníc, ktoré sú kompatibilné s Composerom, pripravené pre použitie vo vašom projekte. Zoznam týchto "balíkov" nájdete na [Packagiste][1], oficiálnom repozitáre pre PHP knižnice kompatibilné s Composerom.

### Ako nainštalovať Composer

Composer môžete nainštalovať lokálne (do aktuálneho adresára, no tento sopôsob nie je odporúčaný) alebo globálne (napr. do /usr/local/bin). Predpokladajme, že chcete nainštalovať Composer lokálne. V kmeňovom adresári vášho projektu spustite:

    curl -s https://getcomposer.org/installer | php

Tento príkaz stiahne `composer.phar` (binárny PHP archív). Môžete ho spustiť s `php` pre manažovanie závislostí vášho projektu. **Pozor:** ak spúšťate kód priamo z internetu, prečítajte si najprv kód online, aby ste sa uistili, že je bezpečný.

### Ako nainštalovať Composer (manuálne)

Manuálna inštalácia Composeru je pokročilý spôsob inštalácie, každopádne existujú dôvody prečo vývojár môže preferovať túto metódu oproti použitiu interaktívnej inštalácie. Interaktívna inštalácia skontroluje vašu inštaláciu PHP, aby bolo isté, že:

- používate dostatočne novú verziu PHP
- `.phar` súbory sa dajú spustiť
- máte dostatočné prístupové práva pre rôzne adresáre
- niektoré problematické rozšírenia nie sú načítané
- niektoré `php.ini` nastavenia nie sú nastavené

Manuálna inštalácia nevykonáva žiadne s týchto kontrol. Takto získate Composer manuálne:

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Cesta `$HOME/local/bin` (alebo adresár podľa vášho výberu) by mal byť v env premennej `$PATH`. Vďaka tomu bude dostupný príkaz `composer`.

Ak nájdete v dokumentácii príkazy ako `php composer.phar install`, môžete ich nahradiť za:

    composer install

### Ako definovať a inštalovať závislosti

Composer udržuje prehľad o závislostiach vášho projektu v súbore nazvanom `composer.json`. Môžete ho spravovať manuálne, alebo použiť samotný Composer. Príkaz `php composer.phar require` pridá novú závislosť projektu, ak súbor `composer.json` neexistuje, bude vytvorený. Tu je príklad ako pridať [Twig][2] ako závislosť vášho projektu. Spustite z kmeňového adresára vášho projektu, kde ste stiahli `composer.phar`:

	php composer.phar require twig/twig:~1.8

Alternatívne príkaz `php composer.phar init` vás prevedie vytváraním kompletného `composer.json` pre váš projekt. Ak ste už vytvorili váš `composer.json`, môžete použiť Composer na stiahnutie a nainštalovanie závislostí do adresára `vendors/`. Toto tiež platí o projektoch, ktoré ste stiahli a už poskytujú `composer.json`:

    php composer.phar install

Následne pridajte tento riadok do hlavného PHP súboru vašej aplikácie, vďaka tomu PHP použije Composer autoloader pre načítanie závislostí vášho projektu.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Teraz môžete používať závislosti vášho projektu, ktoré budú automaticky načítané.

### Akutalizácia vašich závislostí

Composer vytvára súbor nazvaný `composer.lock` v ktorom ukladá presné verzie každého balíku, ktorý stiahol keď ste prvý krát supstili `php composer.phar install`. Ak zdieľate váš projekt s ďalšími kódermi a súbor `composer.lock` je súčasťou, po spustení `php composer.phar install`, budú mať rovnaké verzie ako vy. Pre aktualizáciu vašich závislostí spustite `php composer.phar update`.

Toto je najužitočnejšie, keď definujete verzie vašich závislostí flexibilne. Napríklad, závislosť na verzii ~1.8 znamená "hocičo novšie ako 1.8.0, ale staršie ako 2.0.x-dev". Môžete tiež použiť `*` wildcard ako napr. `1.8.*`. Príkaz Composeru `php composer.phar update` aktualizuje všetky vaše závislosti na najnovšiu verziu, ktorá zodpovedá definovanému obmedzeniu.

### Kontrola vašich závislostí voči bezpečnostným problémom

[Security Advisories Checker][3] je webová služba a nástroj pre príkazový riadok, ktorý prehliadne váš `composer.lock` súbor a povie vám, ak je potrebné aktualizovať niektoré z vašich rozšírení.

* [Čítaj viac o Composeri][4]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://security.sensiolabs.org/
[4]: http://getcomposer.org/doc/00-intro.md
