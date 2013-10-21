---
isChild: true
---

## Konfiguračné súbory {#configuration_files_title}

Pri vytváraní konfiguračných súborov pre Vaše aplikácie je dobré postupovať podľa jedného z nasledujúcich postupov:

- Odporúča aby ste ukladali Vaše konfiguračné súbory na mieste, kde nie sú priamo prístupné cez súborový systém "zvonku".
- Ak je nevyhnutné, aby ste mali konfiguračné súbory uložené v document roote, pomenujte súbory s príponou `.php`. Tým zaručíte to, že ak sa aj niekto pokúsi o prístup ku konfiguračnému súboru priamou cestou, napr. zadaním URL do prehliadača, jeho obsah nebude vypísaný.
- Informácie v konfiguračných súboroch by mali byť adekvátne chránené - buď šifrovaním, alebo skupinovými/užívateľskými oprávneniami súborového systému.