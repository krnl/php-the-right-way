---
isChild: true
---

## Menné priestory (Namespaces) {#namespaces_title}

Ako už bolo spomenuté vyššie, PHP komunitu tvorí veľké množstvo vývojárov, ktorí tvoria veľké množstvo kódu. To znamená, že kód jednej PHP knižnice môže používať taký istý názov triedy aký používa iná knižnica. Ak sú obidve knižnice použité v rovnakom mennom priestore, kolidujú a spôsobia problémy.

_Menné priestory_ tento problém riešia. Ako je napísané v PHP manuáli, menné priestory môžu byť prirovnané k adresárom v operačných systémoch. Dva súbory s rovnakým menom môžu koexistovať v samostatných adresároch. Podobne, dve PHP triedy s rovnakým menom môžu koexistovať v samostatných menných priestoroch.

Je dôležité, aby ste vo Vašom kóde používali menné priestory, vďaka čomu môže byť použitý inými vývojármi bez strachu z kolízie s inými knižnicami.

Jeden z odporúčaných spôsobov ako používať menné priestory je načrtnutý v [PSR-0][psr0], ktorého cieľom je poskytnúť štandardné konvencie pre súbory, triedy a menné priestory, ktoré umožnia tzv. "plug-and-play" kód.

* [Viac informácií o Menných priestoroch (EN)][namespaces]
* [Viac informácií o PSR-0][psr0]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
