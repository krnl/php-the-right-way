---
isChild: true
---

## Príkazový riadok (CLI) {#command_line_interface_title}

PHP bolo vytvorené primárne na písanie webových aplikácii, ale je tiež užitočné na skriptovanie programov pre príkazový riadok (CLI). PHP programy pre príkazový riadok vám môžu pomôcť automatizovať bežné úlohy ako testovanie, deployment, a spravovanie aplikácií.

Sila konzolových PHP programov spočíva v tom, že kód vašej aplikácie môžete používať priamo, bez nutnosti vytvorenia bezpečného webového rozhrania. Davajte si ale pozor, aby ste CLI PHP skripty neumiestnili na verejne prístupné miesto!

Vyskúšajte spustiť PHP z vášho príkazového riadku:

{% highlight bash %}
> php -i
{% endhighlight %}

Prepínač `-i` vypíše vašu konfiguráciu PHP, podobne ako [`phpinfo`][phpinfo] funkcia.

Prepínač `-a` poskytuje interaktívny shell, podobný IRB v Ruby alebo interaktívnemu shellu Pythonu. Existujú aj množstvo ďalších užitočných [prepínačov][cli-options].

Napíšme si jednoduchý "Hello, $name" CLI program. Vytvorte si súbor `hello.php` s nasledujúcim obsahom.

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP vytvára dve špeciálne premenné na základe argumentov s akými je váš skript spustený. [`$argc`][argc] je celočíselná pemenná obsahujúca *počet* argumentov a [`$argv`][argv] je pole obsahujúce *hodnotu* každého z argumentov. Prvým argumentom je vždy názov súboru vášho PHP skriptu, v tomto prípade `hello.php`.

Funkcia `exit()` je volaná s nenulovým argumentom, aby sme shellu dali vedieť, že príkaz nebol úspeše vykonaný. Bežne používané návratové hodnoty môžete nájsť [tu (EN)][exit-codes].

Náš skript z príkazového riadku spustíme následovne:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Čítaj o používaní PHP z príkazového riadku (EN)][php-cli]
 * [čítaj o nastavení Windowsu pre spúštanie PHP z príkazového riadku (EN)][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
