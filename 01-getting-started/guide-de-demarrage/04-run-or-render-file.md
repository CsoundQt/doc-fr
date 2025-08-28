# 4. Exécuter ou Rendre dans un fichier

CsoundQt offre différentes façons d’exécuter/rendre du code Csound.

1. Quand vous cliquez sur le bouton **Exécuter** (ou _Contrôle > lancer Csound_), votre code courant sera exécuté en temps réel. Ce qui signifie que les sorties audio seront écrites sur la carte son (dac = digital-to-analog-converter), et non dans un fichier audio. Vous pouvez alors influencer les performances de votre code, par exemple à l’aide des widgets, ou bien du MIDI.

2. Quand vous cliquez sur le bouton _lancer dans un shell_, le code est également exécuté en temps réel, mais comme un sous-processus dans un terminal externe. La principale différence avec la première option consiste en ce qu’aucun code spécifique à CsoundQT ne fonctionnera. En particulier, les widgets n’auront aucun effet ici.

3. Quand le bouton _Restituer dans un fichier_ est cliqué, le code est rendu et le résultat est écrit dans un fichier audio. Vous n’entendrez rien en temps réel. Le nom de fichier est produit à partir des réglages définis dans _Configuration > Exécuter > Offline Rendering > Output File_ (quand coché).

4. Quand le bouton _Enregistrer_ est cliqué, le code est exécuté de la même manière qu’en _1._ – mais un enregistrement de la performance en temps réel est également écrit dans un fichier. Le fichiers sera écrit dans le même dossier que le fichier csd, et héritera du même nom. Il est également possible d’activer/désactiver l’enregistrement plusieurs fois au cours de la performance : CsoundQt écrira des fichiers séparés à chaque fois que l’enregistrement est activé.