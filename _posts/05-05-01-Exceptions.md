---
isChild: true
---

## Výnimky (Exceptions) {#exceptions_title}

Výnimky sú bežnou súčasťou najpopulárnejších programovacích jazykov, no často sú PHP programátormi prehliadané. Jazyky ako Ruby sú plné výnimiek, vždy keď nastane nejaka výnimočná situácia, ako zlyhanie HTTP požiadavky, alebo zlihanie dopytu na databázu, alebo neexistujúci súbor, Ruby (alebo použité gemy) používajú výnimky, vďaka čomu sa hneď dozviete, že niekde nastala chyba.

PHP samé o sebe zanedbáva používanie výnimiek, napr. volanie na `file_get_contents()` vráti iba `FALSE` a varovanie. Mnoho starších PHP frameworkov ako CodeIgniter iba vráti false, zapíše správu o chybe do logu a možno vám dovolí použiť metódu ako `$this->upload->get_error()` ak sa chcete dozvedieť, kde nastala chyba. Problémom je, že musíte pre nájdenie chyby a hľadať v dokumentácii akú metódu musíte zavolať pre konkrétnu triedu.

Ďalším problémom je, keď triedy automaticky vyhadzujú chybu na obrazovku a ukončujú priebeh skriptu. Týmto riešením znemožňujete inému vývojárovi dynamicky spracovať chybu. Mali by sme použiť výnimky, aby sme vývojárovi oznámili chybu, ktorú potom môže spracovať, napr.:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // Validácia nebola úspešná
}
catch(Fuel\Email\SendingFailedException $e)
{
    // Email sa nepodarilo odoslať
}
{% endhighlight %}

### SPL výnimky

Generická `Exception` trieda poskytuje vývojárovi veľmi málo kontextu pre debuggovanie, tento problém môžeme odstrániť vytvorením špecializovaných typov výnimiek pomocou rozširovania `Exception` triedy dedením:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

To znamená, že môžete pridať viac catch blokov a spracovať rôzne výnimky rôznym spôsobom. Toto môže viesť k vytvoreniu veľkého počtu vlastných výnimiek, niektorým z nich sa môžeme vyhnúť používaním SPL výnimiek, dostupných v [SPL rozšírení][splext].

Napríklad ak používate magickú metódu `__call()` a je zavolaná neplatná metóda, namiesto použitia štandardnej výnimky, ktorá nehovorí o tom aká chyba nastala, alebo vytvoreniu špeciálnej výnimky iba pre tento prípad, môžete jednoducho použiť výnimku pre nesprávne volanie funkcie, ktorá je súčasťou SPL - `throw new BadFunctionCallException;`.

* [Čítaj viac o výnimkách (EN)][exceptions]
* [Čítaj viac o SPL výnimkách (EN)][splexe]
* [Vrstvenie výnimiek v PHP][nesting-exceptions-in-php]
* [Najlepšie praktiky pri používaní výnimiek v PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/en/language.exceptions.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
