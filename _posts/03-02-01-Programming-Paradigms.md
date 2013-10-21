---
isChild: true
---

## Paradigmy programovanie v PHP {#programming_paradigms_title}

PHP je flexibilný, dynamick=y jazyk, ktorý podporuje niekoľsko rôznych programovacích techník. PHP sa stále vyvíja a rozširuje svoje možnosti, vo verzii PHP 5.0 (2004) bol pridaný objektový model, vo verzii PHP 5.3 (2009) anonymné funkcie a menné priestory a vo verzii PHP 5.4 (2012) traity.

### Objektovo-orientované programovanie

PHP obsahuje kompletný model objektovo-orientovaného programovania, podporuje triedy, abstraktné triedy, rozhrania, dedičnosť, konštruktory, klonovanie, výnimky a ďalšie.

* [Čítaj viac o objektovo-orientovanom PHP (EN)][oop]
* [Čítaj viac o traitoch (EN)][traits]

### Funkcionálne programovanie

PHP podporuje funkcie prvej triedy, čo znamená, že funkcie môžu byť priradené do premenných. Používateľské aj vstavané funkcie môžu byť uložené v premennej a volané dynamicky. Funkcie môžu byť predávané ako argumenty iným funkciám (tzv. High-order funkcie) a funkcie môžu vracať iné funkcie.

Rekurzia, pri ktorej funkcia volá samu seba, je podporovaná, ale väčšina PHP kódu sa sústreďuje na iteráciu.

PHP 5.4 pridalo možnosť používať anonymné funkcie s kontextom objektu a vylepšilo podporu pre používanie anonymných funkcií ako náhradu za obyčajné volanie funkcie takmer vo všetkých prípadoch.

* Čítaj viac o [funkcionálnom programovani v PHP](/pages/Functional-Programming.html)
* [Čítaj viac o anonymných funkciách][anonymous-functions]
* [Čítaj viac o triede Closure][closure-class]
* [Viac detailov v Closures RFC][closures-rfc]
* [Čítaj viac o Callables][callables]
* [Čítaj viac o dynamickom volaní funkcií s `call_user_func_array`][call-user-func-array]

### Meta-programovanie

PHP podporuje rôzne formy meta-programovania, pomocou mechanizmov ako Reflection API a magické metódy. Dostupné sú rôzne magické metódy, ako `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, a pod., ktoré dovoľujú vývojárom meniť správanie sa tried. Ruby vývojárom často chýba `method_missing`, ktorá je však dostupná ako `__call()` a `__callStatic()`.

* [Čítaj viac o magických metódach][magic-methods]
* [Čítaj viac o Reflection][reflection]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[overloading]: http://php.net/manual/en/language.oop5.overloading.php
[oop]: http://www.php.net/manual/en/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/en/functions.anonymous.php
[closure-class]: http://php.net/manual/en/class.closure.php
[callables]: http://php.net/manual/en/language.types.callable.php
[magic-methods]: http://php.net/manual/en/language.oop5.magic.php
[reflection]: http://www.php.net/manual/en/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/en/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
