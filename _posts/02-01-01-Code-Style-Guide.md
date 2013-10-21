# Štýl formátovania kódu  {#code_style_guide_title}

PHP komunita je veľká a rôznorodá, vďaka čomu vzniká veľké množstvo knižníc, frameworkov a komponentov. Je bežné, že PHP vývojári, vyberú niekoľko takýchto komponentov a skombinujú ich v rámci jedného projektu. Aby sme uľahčili PHP vývojárom možnosť spájať rôzne komponenty, je dôležité, aby náš PHP kód čo najviac zodpovedal zabehnutým konvenciám a štýlu formátovania.

[Framework Interop Group][fig] predložila a schválila sériu štýlových odporúčaní, známe ako [PSR-0][psr0], 
[PSR-1][psr1] a [PSR-2][psr2]. Tieto odporúčania sú série pravidiel, ktoré používajú projekty ako Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, a pod. Môžete ich použiť pre vaše vlastné projekty, ale môžete tiež pokračovať s používaním vlastného osobitého štýlu.

Ideálne by ste mali písať PHP kód, ktorý zodpovedá známemu štandardu. Tým môže byť kombinácia PSR, alebo jeden zo štandardov kódu vytvorený PEARom alebo Zendom. Vďaka tomu ostatní delevoperi môžu jednoducho čítať a pracovať s vašim kódom a aplikácie, ktoré používajú tieto komponenty sú konzistentnejšie, aj keď pracujú s veľkým množstvom kódu tretích strán.

* [Čítaj viac o PSR-0 (EN)][psr0]
* [Čítaj viac o PSR-1 (EN)][psr1]
* [Čítaj viac o PSR-2 (EN)][psr2]
* [Čítaj viac o PEAR Coding Standards (EN)][pear-cs]
* [Čítaj viac o Zend Coding Standards (EN)][zend-cs]

Na kontrolu kódu voči akémukoľvek z týchto štandardov môžete použiť [PHP_CodeSniffer][phpcs]. Pre okamžitú odozvu pri programovaní môžete použiť pluginy pre textové editory ako napr. [Sublime Text 2][st-cs].

Problémy s formátovaním kódu nemusíte riešiť ručne, môžete použiť [PHP Coding Standards Fixer][phpcsfixer] od Fabiena Potenciera na automatickú úpravu formátovania vášho kódu, tak aby zodpovedal štandardom.

Angličtina je preferovaná pre všetky názvy symbolov a infraštruktúru kódu. Komentáre môžu byť napísané v akomkoľvek jazyku jednoducho čitateľnom všetkými aktuálnymi aj budúcimi používateľmi kódu.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
