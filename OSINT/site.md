# OSINT — recherche en sources ouvertes

L’OSINT consiste à recueillir et vérifier des informations accessibles publiquement. Une recherche doit rester proportionnée, légale et respectueuse de la vie privée. Les commandes ci-dessous sont prévues pour vos propres comptes, vos domaines de test ou des données publiques que vous êtes autorisé à analyser.

## Outils web

| Outil | Lien | Utilité |
|---|---|---|
| Pics.io Metadata Viewer | [Ouvrir](https://pics.io/photo-metadata-viewer-fr) | Lire les métadonnées EXIF d’une image. |
| UserSearch | [Ouvrir](https://usersearch.org/) | Vérifier la présence d’un pseudonyme sur plusieurs services. |
| Web-Check | [Ouvrir](https://web-check.xyz/) | Examiner les informations publiques d’un domaine ou d’une URL de test. |
| OSINT Framework | [Ouvrir](https://osintframework.com/) | Annuaire de méthodes et d’outils OSINT classés par thème. |
| Exploit-DB | [Ouvrir](https://www.exploit-db.com/) | Rechercher des vulnérabilités publiques afin de comprendre et corriger un risque. |

## Outils locaux

### h8mail — recherche liée à une adresse e-mail

[h8mail](https://github.com/khast3x/h8mail) automatise des recherches à partir d’une adresse e-mail et de sources publiques ou de fuites connues. Utilisez uniquement une adresse qui vous appartient ou pour laquelle vous avez une autorisation.

```bash
git clone https://github.com/khast3x/h8mail.git
cd h8mail
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python h8mail.py --help
```

### Toutatis — informations publiques Instagram

[Toutatis](https://github.com/megadose/toutatis) est un outil local destiné à l’étude des informations publiques associées à un identifiant Instagram. Il ne doit pas servir à contourner une protection ou à collecter des données privées.

```bash
git clone https://github.com/megadose/toutatis.git
cd toutatis
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python toutatis.py --help
```

### Sherlock — recherche de pseudonyme

[Sherlock](https://github.com/sherlock-project/sherlock) vérifie si un pseudonyme existe sur différentes plateformes. Les résultats sont des indicateurs, pas une preuve que plusieurs comptes appartiennent à la même personne.

```bash
git clone https://github.com/sherlock-project/sherlock.git
cd sherlock
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python sherlock_project/sherlock.py --help
```

Exemple sur un pseudonyme de test :

```bash
python sherlock_project/sherlock.py pseudo-de-test
```

### DaProfiler — recherche de profils publics

[DaProfiler](https://github.com/TheRealDalunacrobate/DaProfiler) est un projet local de recherche OSINT. Consultez toujours sa documentation avant l’installation, car ses dépendances peuvent évoluer.

```bash
git clone https://github.com/TheRealDalunacrobate/DaProfiler.git
cd DaProfiler
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
[ -f requirements.txt ] && python -m pip install -r requirements.txt
python -m pip install . 2>/dev/null || true
python -m daprofiler --help 2>/dev/null || python main.py --help
```

### GitFive — recherche liée à GitHub

[GitFive](https://github.com/mxrch/GitFive) aide à examiner des informations publiques associées à GitHub. Il faut limiter la recherche à ses propres comptes ou à un périmètre autorisé.

```bash
git clone https://github.com/mxrch/GitFive.git
cd GitFive
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
[ -f requirements.txt ] && python -m pip install -r requirements.txt
python gitfive.py --help 2>/dev/null || python main.py --help
```

### IPinfo CLI — informations IP

[IPinfo CLI](https://github.com/ipinfo/cli) est un outil en ligne de commande pour consulter des informations publiques liées à une adresse IP.

```bash
git clone https://github.com/ipinfo/cli ipinfo-cli
cd ipinfo-cli
```

L’installation officielle utilise Go : [télécharger Go](https://go.dev/dl/), puis :

```bash
go install ./ipinfo/
ipinfo version
go install github.com/ipinfo/cli/ipinfo@latest
```

Vérifier l’aide avant toute utilisation :

```bash
ipinfo --help
```

## Méthode OSINT recommandée

1. Définir une question précise et un périmètre légal.
2. Utiliser plusieurs sources indépendantes.
3. Distinguer un fait, une hypothèse et une corrélation.
4. Ne pas publier de données personnelles inutilement.
5. Documenter la date, la source et la méthode de vérification.

## Ressources complémentaires

- [Historique des versions IPinfo](https://github.com/ipinfo/cli/releases)
- [Vidéo associée à IPinfo CLI](https://www.youtube.com/watch?v=8XDRUk4soS8)
