# Forensics — analyse de fichiers et de métadonnées

La forensics numérique consiste à examiner des fichiers et des traces pour comprendre leur origine, leur contenu et leurs éventuelles modifications. Les outils ci-dessous sont utiles pour des fichiers dont vous êtes propriétaire ou dans le cadre d’une enquête autorisée.

> **Bon réflexe :** travailler sur une copie, conserver l’original intact et noter chaque opération effectuée.

## Outils web

| Site | Fonction | Explication |
|---|---|---|
| [iLovePDF — déverrouiller un PDF](https://www.ilovepdf.com/fr/deverrouiller_pdf) | Traitement de PDF | Permet de travailler sur un PDF lorsque vous disposez des droits nécessaires. Ne l’utilisez pas pour contourner la protection d’un document tiers. |
| [AperiSolve](https://www.aperisolve.com/fr/) | Analyse d’image | Regroupe plusieurs traitements pour rechercher des informations visibles ou dissimulées dans une image. |
| [Jimpl](https://jimpl.com/) | Métadonnées EXIF | Affiche les données d’une image : date, appareil, coordonnées GPS lorsqu’elles existent, etc. |
| [Pic2Map](https://www.pic2map.com/) | EXIF et carte GPS | Lit les métadonnées EXIF d’une photo et affiche sa position sur une carte lorsque l’image contient des coordonnées GPS. Il peut aussi présenter la latitude, la longitude, l’altitude, la direction et une adresse estimée. |
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

Si l’image contient des coordonnées GPS, vous pouvez aussi l’analyser avec [Pic2Map](https://www.pic2map.com/) pour visualiser la position sur une carte. Le service peut convertir les coordonnées en lieu estimé, mais le résultat dépend de la présence et de la précision des métadonnées.

### Vérifier la présence de GPS avant d’utiliser une carte

```bash
exiftool -GPSLatitude -GPSLatitudeRef -GPSLongitude -GPSLongitudeRef -GPSAltitude ./image.jpg
```

S’il n’y a aucune valeur GPS, une carte ne peut pas retrouver de manière fiable le lieu réel de la prise de vue. Une photo peut aussi avoir été recadrée, réexportée ou dépouillée de ses métadonnées.

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
3. Examiner les métadonnées avec ExifTool, Jimpl ou Pic2Map.
4. Si des coordonnées GPS existent, vérifier leur affichage cartographique et leur précision.
5. Comparer les résultats avec le contexte du fichier.
6. Conserver les sorties et les dates de chaque analyse.
