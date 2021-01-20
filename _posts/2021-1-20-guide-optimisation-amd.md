---
layout: post
title: Guide d'optimisation pour les processeurs AMD (Outdated depuis Windows 2004 / Ryzen 5000)
---

AMD, contrairement à Intel, fait le choix de proposer des processeurs au public déjà très performants en sortie d'usine. Petit à petit, les outils qu'utilise AMD deviennent meilleurs, mais ne restent cependant pas parfait. Plusieurs bonnes pratiques doivent être prises en compte (peut importe la génération du processeur AMD, même si les processeurs Zen 2 / Ryzen 3000 sont plus sensibles à cette différence). Voici quelques outils supplémentaires qui vous permettrons d'optimiser votre machine, sans forcément avoir recours à l'overclocking (et pouvoir savoir si l'overclocking est une bonne idée ou non pour votre machine Ryzen).

I) La base
==================================================================================================================

Avant de parler des bases, petit détour autour du BIOS des cartes mères AMD. AMD propose le support de **plusieurs générations de processeurs sur la même carte mère**. Tout n'est pas parfait, car plus la liste des processeurs est grande, plus le BIOS est lourd. Ceraines cartes mères ne possèdent donc pas l'espace suffisant ; certains BIOS de dernière génération **n'acceptent donc pas les processeurs plus anciens**, ou alors seront privés de certaines fonctionnalités. On va donc dans un premier temps essayer de **mettre à jour son BIOS**, en prenant le temps de vérifier que son processeur est toujours compatible avec celui-ci.

Pour cela, tout dépend du constructeur de la carte mère. Généralement, on se rend sur la page du produit de sa carte mère, puis on cherche l'onglet pour télécharger l'image BIOS. Deux solutions sont possibles :

- Vous téléchargez l'image BIOS brute. Si besoin, extraire le contenu si il s'agit d'une archive (zip, rar, tar, gz). Vous placez ensuite le fichier sur une clé USB formattée en FAT32 (pour éviter les problèmes de compatibilité). Dans le BIOS, une option sera indiquée pour mettre à jour ce dernier (se référer au manuel de sa carte mère, disponible en ligne).

- Vous téléchargez un exécutable (le cas pour Asus en outre sur certains modèles), qu'il suffit d'exécuter, puis redémarrer la machine pour mettre à jour le système.

Petit guide réalisé par Topachat pour permettre d'upgrade son BIOS : <https://youtu.be/HB8my058LQ0>

Une fois le **bios mit à jour**, il est fortement recommandé d'utiliser **la dernière version de Windows**, qui est clairement plus optimisée pour les processeurs AMD (peut être moins le cas pour Intel). Pour connaître sa version de Windows, on peut faire un **WINDOWS + R** et taper **winver**.

**Note** : AMD fonctionne sur des versions du microcode, l'AGESA. Ces microcodes apportent généralement beaucoup d'optimisations, pour améliorer les fréquences, les températures voir la stabilité globale du processeur. Dans le cas d'un changement d'AGESA (généralement indiqué sur le changelog), tu devras peut être refaire ton overclocking, qui sera *normalement* plus stable.

I) Le BIOS
==================================================================================================================

Les processeurs Ryzen possèdent un BIOS souvent très complet, bourré d'options qui ne sont clairement pas intuitives. J'ai réalisé un guide qui permet d'en savoir un peut plus. **Avant tout** : si vous suivez ce guide c'est seulement à but informatif, il est inutile de tout vouloir désactiver quand c'est inutile, vous ne gagnerez absolument aucune performance en procédant de cette manière.Je vais reprendre ici les options qui sont **optimales** pour un processeur Ryzen. Si ces options ne sont pas disponibles dans le BIOS, pas de panique :)

Voici les options à régler dans le BIOS en fonction de vos choix (recommandations de @1usmus) :

- **Global C-state Control** ===> en rapport avec les C-state, **laisser activé**.
- **Power Supply Idle Control** ====> défnir en tant que **"Low Current Idle"**.
- **CPPC** ===> **laisser activé**.
- **CPPC Preferred Cores** ===> **laisser activé**.
- **AMD Cool'n'Quiet** ===> **laisser activé**.
- **PPC Adjustment** ===> régler sur **P-State 0**.
- **PBO** (*Precision Boost Overdrive*) ===> **désactiver** (voire note)

**Note** : PBO est l'outil d'overclocking automatique d'AMD. Il est très variable en fonction des cartes mères, nous en reviendrons dans la catégorie d'overclocking.

Pour avoir moi même réalisé plusieurs guides vous invitant à tout vider dans votre BIOS (on fait tous des conneries), en réalité cela n'est pas utile du tout, vous risquez plus de casser votre machine qu'autre chose. En dehors de ces options et quelques autres nécéssaires à l'overclocking de la ram (voir guide), ne touchez à rien d'autre.

II) Le profil d'alimentation
==================================================================================================================

Contrairement à Intel, le profil d'alimentation sur AMD joue un rôle plus important. Trois options sont disponibles : utiliser le profil de Windows, des chipsets AMD ou alors un profil sur mesure, ici celui de @1usmus. Windows comme AMD ont travaillé sur des profils d'alimentation, mais ils sont toujours en retrait sur les dernières versions de Windows. On va ici se reposer sur ce test pour continuer (Windows 2004, Ryzen 3600, X570) : <https://www.hardwaretimes.com/amd-ryzen-3000-boost-fix-benchmarked-1usmus-vs-official-agesa-boost-fix>

On va tout d'abord télécharger le profil (en l'ocurrence il y a deux profils) d'alimentation depuis Guru3D à ce lien : <https://www.techpowerup.com/download/1usmus-custom-power-plan-ryzen-3000-zen-2/>

Pour extraire l'archive, on arrête d'utiliser cette daube de winrar et on passe sur le gratuit 7zip : <https://www.7-zip.org> . Une fois **tout** le contenu extrait, on se retrouve avec trois fichiers :

- 1usmus Ryzen Power Plan pre-1909.pow
- 1usmus Ryzen Universal Power Plan.pow
- Install(.bat)

On a juste exécuter le Install(.bat) ( pas en tant que Administrateur !). Pour fermer le terminal, il suffit d'appuyer sur Entrée, et une fenêtre s'ouvre, on accès à tous les modes d'alimentation. Pour choisir le bon :

- 1usmus Ryzen Power Plan (pre 1909-e) : pour les processeurs AMD Ryzen 3000 / Zen 2 pour toutes les versions de Windows : <https://docs.google.com/spreadsheets/d/1ppUmxWwdRU77nmqwLXmUAGuxLfemZK6AbJlKP2aCn0U/edit#gid=0>
- 1usmus Ryzen Universal : pour les processeurs AMD Ryzen 1000 / 2000 / Zen / Zen + (Ryzen 3200G et 3400G inclus)

On a juste à cocher le bon et on a plus rien d'autres à faire !

III) Overclocking (optionnel)
==================================================================================================================

Comme dit précédemment, AMD utilise des technologies d'overclocking automatique, de gestion de la fréquence bien plus poussés et complexe que chez Intel. La première technologie intéressante est le **XFR**. Elle a été introduite par la première génération de processeur AMD Ryzen, et permet de dépasser la fréquence maximale prévue sur **deux coeurs ou moins**. Cette option est uniquement disponible sous les processeurs AMD avec un **X** (Ryzen 1600X, 1800X..). Par la suite, AMD fait naître **XFR 2**, une nouvelle version qui supporte maintenant de dépasser les fréquences maximales mais cette fois **sur tous les coeurs**. Cependant, les deux technologies de XFR supportent les contraintes de température et consommation, c'est à dire que le TDP maximal du processeur ne sera jamais dépassé, et la température limite non plus. Dans les faits, XFR / XFR 2 amène entre 50 et 75 MHz, en fonction du système de refroidissement (cette valeur peut évidemment varier).

AMD, lors de l'annonce de la troisième génération de processeur AMD Ryzen, a décidé de mettre au point un système de boost qui permettrait de **dépasser les limites de températures et de consommation** : PBO, *Precision Boost Overdrive*, naît. Au début, sans se cacher la face, c'est une catastrophe, une sortie prématurée d'un système qui n'était pas stable, dont les tensions étaient parfois trop élevées. Durant les mois qui suivent, AMD a grandement amélioré le système de PBO, avec de nombreux microcodes (on se souvient des AGESA). Cependant, les constructeurs de cartes mères sont libres de choisir un AGESA. C'est pour cela que PBO, en dehors d'être un système qui n'est pas aujourd'hui parfait, **fonctionnera plus ou moins bien en fonction des configurations**. **PBO n'est pas un outil d'overclocking automatique** (quand il utilise les paramètres par défaut sans XFR tout du moins). Il s'occupe seulement de maintenir le processeur aux fréquences boost le plus longtemps possible, contrairement au XFR qui lui dépasse les fréquences de boost. Il est bien évidemment possible de coupler le XFR à PBO. Ici par de règle unique, il faut tester par soi même avec PBO et l'overclocking manuel.

Petit résumé pour ceux qui n'ont pas suivi :

- Processeurs Ryzen 1000 (Zen) et Ryzen 2000 (Zen +) : XFR permet d'augmenter la fréquence des coeurs sur les versions X **sans** dépasser les limites de température et de consommation.
- Processeur Ryzen 3000 (Zen 2) : PBO permet d'augmenter la fréquence des coeurs **en dépassant les limites de température et de consommation**.

A prendre en compte : les cartes mères **B350/B450**, **X370/X470** sont **compatibles** avec PBO, bien que cette technologie soit arrivée après leur commercialisation.

Le principal avantage de PBO, bien que cela soit très dépendant des cartes mères, c'est pouvoir, en temps réel, modifier l'état de charge du processeur (jouer avec les tensions fréquences). Dans un overclocking manuel, il n'est pas possible de gérer la fréquence et le voltage en fonction de l'utilisation du nombre de coeur (bien que ça soit quand même possibles sur certains modèles de cartes mères généralement hors de prix). PBO n'étant pas parfait, **à vous de tester si cela est bénéfique ou non**.

### Dans le cas où on utilise PBO (+ XFR)

Pour utiliser PBO, il faut déjà avoir un processeur Ryzen 3000, sinon vous n'êtes pas éligible. Dans le BIOS (même si c'est possible depuis Ryzen Master), on active XFR et PBO. Ensuite, il est possible de **personnaliser PBO**, en fonction des limitations supportées par la carte mère. Dans le cas où on personnalise PBO, il serait éventuellement **possible** de dépasser les limites maximales de fréquence. Encore une fois ça dépend des cartes mères, mais 3 critères sont présents :

- Package Power Tracking (ou PPT) : la consommation maximale, en Watt, du socket dépendant de l'alimentation du processeur.
- Thermal Design Current (ou TDC) : la consommation maximale, en Ampère, qui peut être délivré au régulateur de tension de la carte mère (les VRMs).
- Electrical Design Current (ou EDC) : la consommation maximale, en Ampère, qui peut être délivré au régulateur de tension de la carte mère (les VRMs) pendant un très court instant.

PBO va jouer avec ces trois informations en fonction de la **température du processeur**. A ce moment, deux options sont possibles : augmenter la limite de température supportée par PBO (si c'est disponible), pour éviter de toucher aux PPT, TDC et EDC ; ou alors fixer les limites PPT, TDC et EDC en fonction des températures du processeur : PBO ne sera donc plus capable de réguler ces informations, ce qui peut donc faire chauffer votre processeur au délà des normes de sécurité.

Valeurs par défaut de PBO pour PPT, TDC et EDC ([source](https://www.gamersnexus.net/guides/3491-explaining-precision-boost-overdrive-benchmarks-auto-oc)):

- PPT : 142W pour les cartes mères accueillant les processeurs jusqu'à 105W, et 88W pour les cartes mères accueillant les processeurs jusqu'à 65W.
- TDC : 95A pour les cartes mères accueillant les processeurs jusqu'à 105W, et 60A pour les cartes mères accueillant les processeurs jusqu'à 65W.
- EDC : 140A pour les cartes mères accueillant les processeurs jusqu'à 105W, et 90A pour les cartes mères accueillant les processeurs jusqu'à 65W.

Quelques valeures sûres pour les processeurs suivants (merci @Heavenlot) (dans l'ordre PPT TDC EDC) :

- 3900X > 160 105 160
- 3800X > 145 95 145
- 3700X > 105 70 105
- 3600X > 140 90 140
- 3600 > 105 70 105.

Vous pouvez donc augmenter **sensiblement** ces valeurs pour permettre un meilleur gain en fréquence. Les températures sont évidemment à surveiller dans ce cas.

### Dans le cas où on overclock manuellement le processeur

Dans ce cas là, beaucoup moins complexe : on fixe une fréquence au processeur, une tension pour le VCore et un niveau de LLC ([voir guide d'overclocking](https://wanrim.github.io/overclocking)). On peut également ajuster les états de charge C-State dans le bios (qui dépendent donc d'un couple fréquence / voltage). Dans ce cas, si PBO fonctionne bien, l'overclocking du processeur sera **normalement** moins performant.

Dans la réalité, seules les bonnes cartes mères X570 peuvent vraiment offrir des performances avec PBO intéressantes par rapport à de l'overclocking manuel, même en tâche monocoeur.
