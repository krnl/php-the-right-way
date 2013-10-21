---
title: Databázy
---

# Databázy {#databases_title}

Na perzistentné ukladanie infromácií budete v PHP kóde často používať databázu. Existuje niekoľko možností ako sa pripojiť a pracovať s databázou. Odporúčaná možnosť _pred PHP 5.1.0_ bola použiť natívne rozhrania ako [mysql][mysql], [mysqli][mysqli], [pgsql][pgsql], a pod.

Natívne rozhrania sú dobré ak vo vašej aplikácií používate iba jedinú databázu, ale ak napríklad používate MySQL a trochu MSSQL, alebo sa potrebujete pripojiť na Oracle databázu, nebudete môcť použiť rovnaké rozhrania. Budete sa musieť naučiť úplne nové API pre každú databázu.

Mysql rozšírenie pre PHP už nie je aktívne vyvíjané a jeho oficiálny stav od PHP 5.4.0 je "dlhodobo zastarané". To znamená, že bude odstránené v priebehu nasledujúcich vydaní, teda v PHP 5.6 (resp. vo verzii ktorá prijde po 5.5) môže zmiznúť. Ak používate `mysql_connect()` a `mysql_query()` vo vašej aplikácii, budete musieť skôr či neskôr kód prepísať. Najlepšia možnosť je nahradiť používanie mysql s mysqli alebo PDO v predstihu, skôr ako do toho budete dotlačený. _Ak začínate písať aplikáciu od nuly nemali by ste v žiadnom prípade používať mysql rozšírenie - použite [MySQLi rozšírenie][mysqli] alebo PDO.

* [PHP: Choosing an API for MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO je knižnica, ktorá poskytuje abstrakčnú vrstvu pre pripájanie k databázam - v PHP od 5.1.0 - ktorá poskytuje spoločné rozhranie pre komunikáciu s mnohými rozličnými databázami. PDO neprekladá vaše SQL dopyty ani neemuluje chýbajúce funkcie. Slúži čisto len na pripájanie k rôznym typom databáz s rovnakým API.

Dôležitejšie je, že `PDO` umožňuje bezpečné vkladanie cudzích vstupov (napr. ID) do vašich SQL dopytov, bez obáv o SQL injection útoky.
Toto je možné vďaka PDO statementom a viazaným parametrom.

Predpokladajme, že PHP skript dostane numerické ID ako GET parameter. Toto ID bude použité na načítanie záznamu používateľa z databázy. `Zlý` spôsob ako to urobiť:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- ZLE!
{% endhighlight %}

Toto je hrozný kód. Vkladáte neošetrený GET prameter do SQL dopytu. Predstavte si, že heker pošle vlastný `id` parameter volaním URL `http://domain.com/?id=1%3BDELETE+FROM+users`. Toto nastavi premennú `$_GET['id']` na `1;DELETE FROM users`, čo zmaže všetkých vašich používateľov! Namiesto toho by ste mali ošetriť ID vstup pomocou PDO viazaných parametrov.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Automaticky osetrí PDO
$stmt->execute();
{% endhighlight %}

Toto je správny kód. Požíva viazané parametre v PDO statemente. Tento spôsob ošetrí cudzí ID vstup predtým ako je použitý v databáze, prevencia potencionálnych SQL injection útokov.

* [Čítaj viac o PDO][1]

Mali by ste tiež vedieť, že databázové pripojenia vyčerpávajú systémové zdroje, čomu sa dá predísť explicitným uzatváraním pripojení. Pri používaní PDO môžete pripojenie implicitne uzatvoriť zrušením objektu, zmazaním všetkých referencií, napr. nastavením na NULL. Ak toto explicitne neurobíte, PHP automaticky uzatvorí pripojenie, keď váš skript skončí (ak nepoužívate perzistentné pripojenia).


* [Čítaj viac o PDO pripojeniach][5]

## Abstrakčné vrstvy

Mnoho frameworkov poskytuje vlastné abstrakčné vrstvy, ktoré môžu, ale nemusia byť postavené nad PDO. Tieto vrstvy často emulujú funkcie, ktoré jednotlivým databázam chýbajú, obalovaním vašich dopytov do PHP metód, poskytujúc kompletnú databázovú abstrakciu.
Toto samozrejme trochu spomaľuje vykonávanie, ale ak pracujete na prenositeľnej aplikácii, ktorá musí pracovať s MySQL, PostgreSQL a SQLite, malé spomalenie môže byť, kvôli čistote kódu, prijatelné.

Niektoré abstrakčné vrstvy používajú menné priestory podľa PSR-0 štandardu, teda môžu byť použité v akejkoľvek aplikácii:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/en/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
