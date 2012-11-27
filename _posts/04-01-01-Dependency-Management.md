# Spravovanie závislostí {#dependency_management_title}

Existujú tony PHP knižníc, frameworkov a komponentov z ktorých si môžete vyberať. Váš projekt ich bude pravdepodobne používať hneď niekoľko - nazývame ich projektové závislosti. Až donedávna pre PHP neexistoval jednoduchý sposob ako spravovať tieto závislosti. Aj v prípade, keď ste si ich spravovali sami ste sa stále museli trápiť s autoloadermi. Teraž sa už nemusíte.

V súčasnosti máme k dispozícii dva významné systémy na správu balíčkov pre PHP - Composer a PEAR. Pýtate sa, ktorý je ten správny pre Vás? Odpoveď je obidva.

* Ak spravujete závislosti pre jeden projekt, použite **Composer**
* Ak spravujete závislosti pre PHP ako také vo Vašom systéme, použite **PEAR**

Vo všeobecnosti, balíčky Composer-u budu dostupné iba pre projekty, ktoré explicitne určíte, zatial čo balíčky PEAR-u budú dostupné pre všetky Vaše PHP projekty. Aj ked na prvý pohľad sa môže PEAR javiť ako jednoduchšia voľba, niekedy má viac výhod použitie projektovo špecifického prístupu na spravovanie závislostí. 
