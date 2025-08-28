# 1. Installation
## 1.1 Installez d’abord Csound

Allez à la page [téléchargement de Csound](https://csound.com/download.html), choisissez l’installeur pour votre système, et installez Csound.

> NOTE : Dans certains installeurs CsoundQt, une version de base de Csound est inclue. Regardez si vous voyez quelque chose comme "+Csound" dans le nom, par exemple "_CsoundQt-1.1.3+Csound-6.18.1-Wind64.zip_".

## 1.2 Mac
1. Téléchargez **CsoundQt-[Version Number]-MacOs.dmg** depuis la [CsoundQT release page](https://github.com/CsoundQt/CsoundQt/releases). _NOTE : Choisissez la version simple (sans "pythonqt") pour une installation normale_.
2. Ouvrez le _.dmg_ et faites glisser l’application verte CsoundQt dans le dossier des applications.

## 1.3 Windows
1. Téléchargez **CsoundQt-[Version Number]-Win64.zip** depuis la [CsoundQT release page](https://github.com/CsoundQt/CsoundQt/releases).
2. Dézippez le fichier
3. Rendez-vous dans le dossier _bin_.
4. Sélectionnez et copiez le contenu complet de ce dossier _bin_.
5. Allez à _C: -> Program Files -> Csound6_x64 -> bin_ et collez-y tous les fichiers copiés.
6. Envoyez "CsoundQt-d-html-cs6.exe" comme raccourcis sur votre bureau si vous voulez.

## 1.4 Linux
Les binaires CsoundQt sont présents dans la plupart des gestionnaires de paquets.

Ces binaires peuvent être construits sans support pour _RtMidi_ et/ou _PythonQt_. Si vous voulez travailler avec, vous devrez **construire CsoundQt vous-même**. Les instruction pour ce faire peuvent être trouvées sur <https://github.com/CsoundQt/CsoundQt/wiki> et dans le fichier [BUILDING.md](https://github.com/CsoundQt/CsoundQt/blob/master/BUILDING.md).