# Onglet Advanced

![alt text](../02-images-configuration/02-onglet-advanced.png)

Les deux première options sont importantes pour la configuration d’une performance en directe car la latence dépend d’eux en grande partie.

## Taille du tampon (-b)

Ceci définit la taille du tampon logiciel en échantillons/samples (correspond au drapeau -b).

Si vous ne cochez pas cette option, CsoundQt utilisera les réglages par défaut. Comme indiqué dans le [manuel Csound](https://csound.com/docs/manual/CommandFlags.html), ces réglages sont définis à 256 samples sur Linux, 1024 sur MacOS X, et 4096 sur Windows.

Si vous cochez et entrez une valeur personnalisée, voici quelques conseils :

- Utilisez toujours une valeur puissance de deux.
- Généralement, la taille du bloc [ksmps](http://csound.github.io/docs/manual/ksmps.html) vaut 1/4 ou 1/2 de la taille du tampon logiciel. Si vous utilisez les entrées et sortie en direct / live, il est plus efficace de configurer la taille du tampon logiciel comme un entier multiple de _ksmps_ ("full duplex audio").

- Parce que ça réduit la latence, utilisez de plus petites valeurs (par exemple 128) pour les performances en direct / live (en particulier avec des entrée en direct). Utilisez de plus grandes valeurs (par exemple 1024) dans les autres cas, par exemple pour jouer des fichiers audio.

## Taille du tampon HW (-B)

Ceci définit la taille du tampon matériel en échantillons/samples (correspond au drapeau -B).

Si vous ne cochez pas cette option, CsoundQt utilisera les réglages par défaut. Comme indiqué dans le [manuel Csound](https://csound.com/docs/manual/CommandFlags.html), ces réglages sont définis à 256 samples sur Linux, 1024 sur MacOS X, et 4096 sur Windows.

Si vous cochez et entrez une valeur personnalisée, voici quelques conseils :

- Utilisez toujours un entier multiple de la taille du tampon logiciel. Un rapport courant est : Taille du tampon matériel = 4 * Taille du tampon logiciel.
- Le rapport entre la taille du tampon logiciel et la taille du tampon matériel dépend du module audio<sup>1</sup>.

<sup>1</sup>Dans l’explication de Victor Lazzarini (email à Joachim Heintz du 19 mars 2013) :
1. Pour portaudio, -B n’est utilisé que pour suggérer une latence au backend, alors que -b est utilisé pour définir la taille actuelle du tampon.
2. Pour coreaudio, -B est utilisé pour la taille du tampon circulaire interne, et -b est utilisé pour la taille du tampon IO actuel.
3. Pour Jack, -B est utilisé pour déterminer le nombre de tampons utilisés en conjonction avec -b. num = (N + M + 1) / M. -b est la taille de chaque tampon.
4. Pour alsa, -B est la taille de la taille du tampon, -b est la taille de la période (un tampon est divisé en périodes).
5. Pour Pulse, -b est la taille actuelle du tampon passé au périphérique, -B n’est pas utilisé.  
En d’autres termes, -B n’est pas très significatif en 1, et pas utilisé en 5, mais a un rôle à jouer dans 2, 3 et 4, ce qui est fonctionnellement similaire.

## Multicore

Vous pouvez essayer d’augmenter ceci au cas où vous atteignez les limites en calcul temps réel. Ça peut aider… ou pas. Cela dépend beaucoup de votre code.

## Sample-accurate / Précision à l’échantillon

Active le mode sample-accurate. Dans ce mode, le rendu n’est pas quantifié par rapport aux cycles de performance, mais commence à l’échantillon spécifié correspondant au moment du début d’un évènement.

## Realtime / Temps réel

Mode priorité au temps réel. Dans ce mode, toute initialisation (chargement de tampons, etc) est fait en tache de fond. L’instrument planifié commence son exécution quand les taches de fond sont terminées. Ce qui peut aider à éliminer les interruptions (mais peut avoir un effet négatif sur la précision de la planification). **NB: En mode temps réel, toutes les impression sont faites sur stderr**. Afin de voir l’effet des opcodes d’impression, ouvrez CsoundQt depuis la ligne de commande. Toutes les impression seront visibles sur le terminal.

## Vérifier la syntaxe avant d’exécuter

Dans certains cas, csound peut planter (et CsoundQT avec lui) avant que la moindre information de débogage soit lisible dans la console CsoundQt (pendant la compilation). Dans ces cas, activez cette option pour vérifier la syntaxe avant d’exécuter csound avec une communication complète avec les widgets, etc.

## Démon / Daemon

N’arrête pas si l’orchestre du csd n’est pas donné, est vide ou ne compile pas.  
NB : à utiliser avec précautions. Dans le cas d’erreur de syntaxe, Csound maintiendra l’exécution dans un état parfois indéfini, provoquant de plantages et éventuellement entrainant la chute de CsoundQt.  
NB2 : En l’absence de partition/score ou de tout évènement dans les balise \<CsScore>, Csound passe en mode daemon par défaut.

## Use Limiter / Additional flags / Jack Client Name

Ces option se comprennent d’elles-même.