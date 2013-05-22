---
isChild: true
---

## Dátum a čas {#date_and_time_title}

PHP obsahuje triedu DateTime, ktorá uľahčuje čítanie, zapisovanie, porovnávanie alebo počítanie dátumov a času. V PHP je okrem DateTime mnoho ďalších funkcií na prácu s dátumom a časom, ale táto trieda poskytuje pekné objektovo-orientované rozhranie pre bežné prípady použitia. Vie pracovať aj s časovými pásmami, ale tejto funkcii sa nebudeme venovať.

DateTime začnete používať skonvertovaním obyčajného reťazca s dátumom a časom na objekt pomocou metódy `createFromFormat()` alebo môžete použiť `new \DateTime` pre získanie aktuálneho dátumu a času. Metóda `format()` skonvertuje DateTime späť na reťazec pre výstup.
{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Začiatočný dátum: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Počítanie s DateTime je možné pomocou triedy DateInterval. DateTime poskytuje metódy `add()` (pripočítanie) a `sub()` (odpočítanie), ktoré očakávajú DateInterval ako argument. Nepíšte kód, ktorý predpokladá rovnaký počet sekúnd každý deň, kvôli letnému času a zmenám časových pásiem tento predpoklad nie je správny. Preto je lepšie používať dátumové intervaly. Pre vypočítanie rozdielu slúži metóda `diff()`, ktorá vráti nový DateInterval, ktorý je veľmi jednoduché zobraziť.
{% highlight php %}
<?php
// vytvor kópiu $start a pridaj jeden mesiac a 6 dní
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Rozdiel: ' . $diff->format('%m mesiac, %d dní (celkom: %a dní)') . "\n";
// Rozdiel: 1 mesiac, 6 dní (celkom: 37 dní)
{% endhighlight %}

DateTime objekty môžete štandardne porovnávať:
{% highlight php %}
<?php
if ($start < $end) {
    echo "Začiatok je pred koncom!\n";
}
{% endhighlight %}

Posledný príklad demonštruje použitie triedy DatePeriod. Používa sa na iteráciu cez periodicky sa opakujúce udalosti. Ako vstup berie dva DateTime objekty, začiatok a koniec a interval pre ktorý vráti všetky opakovania udalosti.
{% highlight php %}
<?php
// vypíš všetky štvrtky medzi $start a $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // vypíš každý dátum v tejto perióde
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [Čítaj viac o DateTime][datetime]
* [Čítaj viac o formátovaní dátumov][dateformat] (akceptované formáty dátumov)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
