---
isChild: true
---

## Menné priestory {#namespaces_title}

Ako bolo spomenuté vyššie, PHP komunitu tvorí množstvo vývojárov tvoriacich množstvo kódu. To znamená, že PHP kód jednej knižnice môže používať rovnaký názov triedy ako iná knižnica. Ak sú obe knižnice použité v rovnakom mennom priestore, vzniká kolízia a tá spôsobuje problémy.

_Menné priestory_ riešia tento problém. Ako je popísané v PHP manuále, menné priestory môžeme prirovnať k adresárom operačného systému - dva súbory s rovnakým názvom môžu existovať v rozdielnych adresároch. Podobne, dve PHP triedy s rovnakým názvom môžu existovať v rozdielnych PHP menných priestoroch. Je to tak jednoduché.

Je dôležité používať menné priestory vo vašom kóde, tak aby ho mohli použiť ostatní vývojári bez strachu z kolízie s inými knižnicami.

Jeden z odporúčaných postupov ako používať menné priestory je popísaný v štandarde [PSR-0][psr0], ktorého cieľom je poskytovať štandardný spôsob ako pomenovať súbory, triedy a menné priestory, umožňujúc kompatibilnejší kód.

* [Čítaj viac o menných priestoroch (EN)][namespaces]
* [Čítaj viac o PSR-0 (EN)][psr0]
