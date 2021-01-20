---
layout: post
title: Guide d'overclocking
---

Dans ce guide, je vais essayer d'expliquer comment overclocker sa machine proprement et tirer le maximum des performances sans pour autant endommager le système. Je ne peux évidemment pas être responsable si des problèmes pourraient arriver sur votre machine, même si en suivant ce guide méticuleusement tout devrait très bien se passer. Passons aux pré-requis pour pouvoir overclocker.

I) Prérequis
==================================================================================================================

L'overclocking existe principalement sous trois forme, par le processeur (CPU), la mémoire vive (RAM) et la carte graphique (GPU). Chaque matériel peut supporter la totalité ou une partie de ces overclocking. Je vais me baser sur les générations récentes, ce qui concernera la plupart d'entre vous. Voici un tableau résumant les possibilités d'overclocking en fonction du matériel.

**Note** : pour l'**ensemble** des overclockings il est important de posséder une alimentation correcte. La consommation peut largement augmenter dans certains cas, il est donc primordial d'avoir une alimentation confortable pour overclocker. Je conseille au minimum une alimentation avec 150W de plus (sur le rail 12V) que la consommation "normale" de la machine. Pour calculer la consommation de sa machine on utilise [Seasonic Wattage Calculator](https://seasonic.com/wattage-calculator) qui est induscutablement le meilleur estimateur de consommation en ligne.

### **Pour l'overclocking du processeur (CPU)**

| Marque de processeur | Processeurs compatibles pour l'overclocking | Chipsets compatibles pour l'overclocking
| ------ | ------ | ------ |
| AMD | Tous les processeurs **Ryzen** (voir **Note 1**) | B350,X370,B450,X470,B550,X570
| Intel | Tous les processeurs **K** (voir **Note 2**) | Z470,Z390,Z370,Z270,X299,Z170 (voir **Note 3**)

**Note 1** : les processeurs AMD récents A10/12 peuvent être overclockés mais ne reposent pas sur l'architecture Ryzen (merci @r11xp)

**Note 2** : il *était* possible d'overclocker un processeur non-k chez Intel mais aujourd'hui c'est beaucoup plus compliqué, les séries 6000 étaient principalement concernés (merci @OldSKol)

**Note 3** : le chipset n'est pas le seul critère important lors de la selection d'une carte mère. Il faut vieiller au fait qu'elle supporte convenablement le processeur, qu'elle est correctement refroidie, évolutive, avec un BIOS décent etc.

### **Pour l'overclocking de la mémoire vive (RAM)**

| Marque de processeur | Chipsets compatibles pour l'overclocking de la mémoire vive (RAM)
| ------ | ------ |
| AMD | A320,B350,X370,B450,X470,B550,X570 (voir **Note 4**)
| Intel | Z390,Z370,Z270,X299,Z170 (voir **Note 5**)

**Note 4**: mieux vaut vérifier à l'avance si son BIOS le permet. Il est fortement recommandé de choisir une carte mère avec un chipset B/X si on souhaite overclocker confortablement la mémoire.

**Note 5** : il est possible d'overclocker sur d'autres chipsets que les séries X/Z, mais la vitesse de la mémoire sera limitée par le contrôleur interne, généralement 2666 MHz, ce qui rend donc l'overclocking absolument pas intéressant. On préfère dans le même cas un chipset X/Z pour overclocker confortablement.

### **Pour l'overclocking de la carte graphique**

Pas de pré-requis particulier, c'est possible d'overclocker la carte graphique (GPU) sur n'importe quelle carte mère. Grâce aux normes de rétro-compatibilité, on peut aussi affirmer que toutes les cartes graphiques sont compatibles avec toutes les cartes mères (avec au moins un port PCI Express).

## Autres prérequis conseillés

Lors de l'achat de la configuration, ou de la mise à niveau d'une configuration existante, on essaye absolument d'avoir **un bon flux d'air** global, éventuellement améliorer le refroidissement par défaut pour le processeur. On peut également envisager de changer la pâte thermique de ses composants pour un "retour à neuf" en terme de performances.

Je ne déconseille pas d'overclocker sur des ventilateurs "stock". La réponse est simple : même sur le refroidissement d'origine, voir n'importe quel refroidissement, il y a toujours moyen d'augmenter la fréquence, et surtout optimiser les températures pour avoir un système optimal. L'overclocking avec un refroidissement par défaut ne sera pas évidemment pas le même qu'avec un refroidissement supplémentaire (vivement conseillé si on souhaite profiter au maximum de son système, et pas se détruire les oreilles).

II) Overclocking Processeur
==================================================================================================================

Tout comme les autres overclock, le manuel de la carte mère (dispo en ligne) est dans chaque cas très complet et vous y trouverez tout ce qui est formulé ici. Si votre configuration est éligible à l'overclocking du processeur, nous allons commencer très simplement à regarder les limites de notre refroidissement. Pour cela, directement dans le BIOS de la carte mère nous allons fixer la fréquence par défaut du processeur (la fréquence de base, pas la fréquence de boost, exemple : le Ryzen 2600 possède une fréquence de base de 3.4 GHz, et le i7 8700K possède une fréquence de base de 3.7 GHz). Une fois la fréquence fixée, nous allons nous renseigner à la valeur VCore, le voltage du processeur. Nous allons aller de palier de 0.05v à partir de 1.25V, jusqu'à 1.4V maximum peut importe la référence de votre processeur (donc 1.25V, 1.30V, 1.35V, 1.40V). Certains diront que 1.4V c'est trop, que la limite est 1.35V, d'autres diront qu'on peut pousser à 1.45V sur certaines références... fondamentalement et depuis quelques années beaucoup de processeurs overclockés tournent à ce voltage, et aucun problème n'est à déplorer. Il ne faut pas se reposer sur la théorie mais constater les faits et remarquer que 1.4V est la limite correcte pour une utilisation amatrice d'un processeur (c'est à dire jouer, streamer, éventuellement faire du montage/graphisme 3D pendant plusieurs heures).

Une fonctionnalité très importante, bien qu'elle ne soit pas inclue dans toutes les cartes mères, c'est le **LLC**. C'est une fonctionnalité qui permet de se rapprocher le plus possible de la tension appliquée dans le BIOS quand le processeur est en charge. En fonction de la marque de la carte mère, ce critère change plus ou moins de plus intense au plus souple. Quand ce paramètre est poussé à fond, la carte mère aura tendance à dépasser le voltage indiqué dans le BIOS, tendis que lorsqu'il sera inactif ou a un degré faible, la carte mère aura tendance à afficher une tension inférieure à celle affichée dans le BIOS. [Plus d'explications ici](https://overclocking.com/tuto-overclocking-z390-maximus-xi/4/). **Attention** : certaines cartes mères n'ayant pas de LLC ne sont pas **du tout** propices à l'overclocking. Dans mon propre cas, ma Asrock B450 K4 me propose un drop de 0.1V peut importe la tension appliquée à mon processeur, ce qui me limite donc à une tension de 1.3V (ou un peu plus).

**Note** : les processeurs Zen 2 (ou Ryzen 3000) fonctionnent **mieux** avec un voltage inférieur à 1.4V. Là où certains diront que c'est dangereux, c'est aussi contre productif. L'overclocking des Ryzen 3000 peut avoir un avantage, mais en manuel on préfère tourner aux alentours de 1.35V/1.375V en fonction de votre modèle de processeur ([source](https://www.youtube.com/watch?v=jmPVr8M-9yI)). PBO est l'outil d'overclocking manuel d'AMD, il n'est pas parfait et parfois peut personnalisable. Dans ce cas, il faut comparer les résultats avec PBO et avec un overclocking manuel.

**Note** : les processeurs sont concus en fonction de critères de selections très exigeants (comme capable de tourner 24h/24 à une utilisation totale, effectuer des calculs complexes sans ommetre aucune erreur). Ces critères **ne sont pas valables pour nous**, et c'est bien pour cela que l'overclocking est possible : on se permet d'augmenter les performances du processeur car notre utilisation n'en dépend pas de la même manière. Nous reparlerons juste après de Prime95 qui prend en compte les tâches AVX, où il est important de connaître la différence entre un overclocking supportant l'AVX et le supportant pas, ou mal.

Une fois le BIOS réglé avec la fréquence de base du processeur couplé à un voltage de **1.25V** pour commencer, nous allons appliquer les changements et redémarrer sous Windows. Une fois dessus on télécharge le fichier suivant : <https://www.mersenne.org/download/> (la version *Windows: 64-bit*). On aura également besoin de ce logiciel pour surveiller les températures du processeur : <https://www.alcpu.com/CoreTemp/>. *ATTENTION* : l'utilisation d'un autre logiciel de monitoring pour surveiller ses températures n'est peut être pas la meilleure idée. En effet, pour ne citer que HWInfo et HWMonitor, certains peuvent avoir des bugs et des différences notables avec la réalité. Core temp est recommandé, c'est le plus fiable pour le moment, peut importe le processeur.

Encore une fois, la température limite d'un processeur peut être remit en cause des centaines de fois. Attention, Prime95 va représenter un usage beaucoup plus important que la réalité (beaucoup plus énergivore que un rendu quelconque et encore plus d'un jeu). Les températures sous Prime95 ne seront donc jamais atteintent dans un usage normal, on va donc se permettre de dire que si notre machine ne dépasse pas 80°C sous Prime95 pendant 10-15min, on peut se permettre de monter le voltage. **Si la température dépasse 80°C**, on diminuera donc le voltage progressivement jusqu'à trouver la limite pour notre configuration. Par exemple, mon Ryzen 2600 atteint 1.3925V en restant en dessous de 80°C. Une fois le voltage limite trouvé, on pourra par la suite le modifier, et en l'occurence le baisser jusqu'à que notre overclocking soit instable (ce que nous verrons après). Si votre processeur ne dépasse pas 80°C même à 1.4V attention : le voltage n'est pas "dangereux" que quand il augmente la consommation et donc la température du processeur. Les transistors, composants électroniques qui contrôlent les oscillations électriques peuvent mal supporter cette monter en tension (=voltage). La tension joue beaucoup sur la température, mais ce n'est pas le seul critère. La fréquence peut aussi jouer son rôle (beaucoup plus faible par contre). En poussant la fréquence après avoir établi le voltage maximum pour une température de 80°C, nous ne devrions pas dépasser 80°C sous Prime, le **grand** maximum à ne pas dépasser.

<p align="center">
  <img src="https://i.imgur.com/vHSPd4a.png" />
</p>

**Maintenant comment ça marche Prime95 ?** Juste après l'avoir ouvert, ou dans *Options* => *Torture Test*, on arrive sur cette fenêtre :

<p align="center">
  <img src="https://i.imgur.com/BSCi2gW.png" />
</p>

Maintenant problème, **AVX ou pas ?**. L'AVX a été introduit par Intel avec la génération Sandy Bridge (Core i 2000) en 2011. Il s'agit d'un jeu d'instruction, ou un language machine. Ce jeu d'instruction n'est pas utilisé par l'ensemble des logiciels, et c'est là que le choix va se faire. Si vous possédez une utilisation dépendante de l'AVX, alors **lancez Prime95 par défaut**. Si ce n'est pas le cas, **cochez *Disable AVX2 (fused multiply-add)* et *Disable AVX*** (qu'il est possible de selectionner après avoir coché *Disable AVX2 (fused multiply-add)*. Comment savoir si nos logiciels (jeux y compris donc) utilisent l'AVX ? Globalement, les logiciels de traitement d'image, de compressions pour ne citer que la suite Adobe, 7zip, Excel... utilisent l'AVX. Pour les jeux, globalement l'AVX n'est pas le jeu d'instruction le plus présent (bien que présent dans Crew2 de mémoire). Dans toutes les situations, il faut savoir si notre utilisation dépend ou pas de l'AVX. Avoir un système non stable en AVX pourra nous permettre de monter bien plus haut en performances, et rester "stable" dans **notre** utilisation.

**Note** : de plus en plus de logiciels deviennent dépendant à l'AVX, si on souhaite avoir une machine le plus stable possible en 2020, il est quand même recommandé de prendre en compte l'AVX (merci @Niuulh et @bl4ckdot).

**Note** : certaines cartes mères permettent de désactiver le support de l'AVX, en particulier les cartes mères Asus (source : <https://forum.overclocking.com/threads/i9-9900k-5ghz.51/>)

<p align="center">
  <img src="https://i.imgur.com/5d78zXe.png" />
</p>

Pour arrêter le "stress", il suffit d'aller dans *Test* puis *Stop*. Voilà ! Vous savez maintenant utiliser Prime95 pour faire chauffer votre processeur pour après en connaître les limites. Core temp ne demande lui pas de guide, il suffit de le lancer pour observer les températures par coeur, la tension du VCore est également indiquée.

### En résumé pour trouver le voltage idéal

* On fixe la **fréquence de base** de son processeur
* On fixe le **voltage CPU / VCore à 1.25V**, on trouve le **bon niveau** du LLC en fonction de sa configuration.
* On augmente ou baisse le voltage pour trouver la tension maximale **sans dépasser 80°C** avec Prime95 pendant 10-15min.

Voilà, vous avez votre voltage / tension / VCore maximal, et on va donc devoir passer à l'augmentation logique de la fréquence du processeur. Avant de tenter l'impossible, on essaye de se renseigner un minimum de quoi est capable le processeur en overclocking, en regardant plusieurs tests, en demandant l'avis à la communauté. On évite de regarder les premiers tests du processeurs, ils ne sont sûrement pas à jours et les processeurs testés sont souvent OP, c'est à dire bien meilleurs que la moyenne.

Généralement, pour donner un minimum de bases, on estime qu'un processeur Zen (Ryzen 1000) peut atteindre 4 GHz pour 1.4V, un processeur Zen+ (Ryzen 2000) 4.2 GHz pour 1.4V, et Zen 2 (Ryzen 3000) peut atteindre 4.3 GHz pour 1.4V. Ces valeurs peuvent évidemment bouger, tout les processeurs ne sont pas identiques. Pour Intel on aborde souvent le "5 GHz Ready", c'est à tester encore une fois.

**Note** : les processeurs de série G chez AMD ont **une génération de retard**. Les Ryzen 2200G et 2400G sont donc de la génération Zen, et les Ryzen 3200G et 3400G de Zen+.

Pour commencer proprement à dire **l'overclocking** (littéralement le sur-cadençage de la fréquence) en augmentant la fréquence de **100 MHz par 100 MHz**. On pourra par la suite affiner sa fréquence en fonction de la carte mère, qui permet ou non de passer de crans de 50, 25, 10 MHz voir moins. jusqu'à ne plus être stable. Au même titre que pour sa tension, on vérifie la stabilité de son processeur en effectuant Prime95 environ 10-15min, **avec ou sans AVX en fonction de l'utilisation**. Par ailleurs, si avec notre voltage idéal on ne dépasse pas 80°C sous Prime95 après une courte session de 10-15min, on peut se permettre de dépasser 80°C **uniquement en augmentant la fréquence** sous Prime95. Comme indiqué au dessus, la fréquence joue également un rôle sur la température, mais beaucoup plus faiblement.

Dans le cas ou Prime ne sera pas suffisant, essayez une fois la session d'overclocking terminée de réaliser vos tâches favorites, mais normalement cela sera parfaitement suffisant, autant sur un processeur AMD qu'Intel. Tout réside après dans l'**optimisation**, en reprenant un tableau d'exemple :

| Tension | Fréquence
| ------ | ------ |
| 1.4V | 4.5 GHz
| 1.375V | 4.47 GHz
| 1.35V | 4.45 GHz
| 1.325V | 4.4 GHz
| 1.3V | 4.2 GHz
| 1.25V | 4.0 GHz

Comme on le voit, à partir de **1.325V**, la fréquence n'augmente plus de manière exponentielle (= de manière continue). Il n'est donc pas vraiment intéressant dans ce cas de monter la tension à plus de **1.325V** car la fréquence n'augmente que très peu (et donc) les performances stagnent. C'est **un exemple typique d'un processeur Ryzen 3000**. A vous maintenant de réaliser ce genre de tableau pour voir quelle configuration est la plus optimale pour vous.

C'est tout pour l'overclocking du processeur, on peut aller également plus loin, mais la **fréquence**, le **VCore**, l'**AVX** et le **LLC** sont des valeures acceptables pour avoir un overclocking intéressant sur sa machine. Si on souhaite allez plus loin, je vous conseille fortement le discord d'[overclocking.com](https://discord.gg/RAMT9CW).

II) Overclocking Mémoire vive (RAM)
==================================================================================================================

En cours (réservé)

II) Overclocking Carte graphique
==================================================================================================================

En cours (réservé)
