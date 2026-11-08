# Forensics — analyse de fichiers et de métadonnées

La forensics numérique consiste à examiner des fichiers et des traces pour comprendre leur origine, leur contenu et leurs éventuelles modifications. Les outils ci-dessous sont utiles pour des fichiers dont vous êtes propriétaire ou dans le cadre d’une enquête autorisée.

> **Bon réflexe :** travailler sur une copie, conserver l’original intact et noter chaque opération effectuée.

## Outils web

| Site | Fonction | Explication |
|---|---|---|
| [iLovePDF — déverrouiller un PDF](https://www.ilovepdf.com/fr/deverrouiller_pdf) | Traitement de PDF | Permet de travailler sur un PDF lorsque vous disposez des droits nécessaires. Ne l’utilisez pas pour contourner la protection d’un document tiers. |
| [AperiSolve](https://www.aperisolve.com/fr/) | Analyse d’image | Regroupe plusieurs traitements pour rechercher des informations visibles ou dissimulées dans une image. |
| [Jimpl](https://jimpl.com/) | Métadonnées EXIF | Affiche les données d’une image : date, appareil, coordonnées GPS lorsqu’elles existent, etc. |
| [Convert Guru](https://convert.guru/fr/convertisseur) | Conversion de fichiers | Convertit des fichiers entre plusieurs formats afin de faciliter leur analyse. |
| [Tembric Audio Forensics](https://tembrica.com/fr/audio-forensics) | Analyse audio | Aide à repérer des manipulations audio et des deepfakes. Les résultats doivent être vérifiés par un professionnel. |

## Outil local : ExifTool

[ExifTool](https://exiftool.org/) est un outil en ligne de commande qui lit et écrit les métadonnées de nombreux formats. Il est préférable à un service web pour les fichiers sensibles.

### Installation sous Debian, Ubuntu ou Kali

```bash
sudo apt update
sudo apt install libimage-exiftool-perl
```

### Lire les métadonnées

```bash
exiftool ./image.jpg
```

### Afficher uniquement les coordonnées GPS

```bash
exiftool -GPSLatitude -GPSLongitude ./image.jpg
```

### Exporter le résultat dans un fichier texte

```bash
exiftool ./image.jpg > analyse-image.txt
```

Ne modifiez pas l’original pendant une investigation. Pour un exercice de nettoyage de métadonnées, faites une copie puis travaillez sur cette copie :

```bash
cp ./image.jpg ./image-copie.jpg
exiftool -all= ./image-copie.jpg
```

## Procédure simple

1. Calculer éventuellement le hash du fichier original.
2. Faire une copie de travail.
3. Examiner les métadonnées avec ExifTool ou Jimpl.
4. Comparer les résultats avec le contexte du fichier.
5. Conserver les sorties et les dates de chaque analyse.
