https://pics.io/photo-metadata-viewer-fr          - métadonnée                  (analyzer les métadonnées EXIF, notamment GPS, date, modèle du téléphone, etc.)

https://github.com/khast3x/h8mail                 - email                 (recherche imail approfondie sur toutes les fuite et outil osint integrer se fait en local ,il peut trouver des choses comme :
nom ou prénom
pseudonymes
numéros de téléphone
adresses physiques
dates de naissance
mots de passe anciens ou hachés provenant de fuites historiques

https://github.com/megadose/toutatis              - recherche insta        (recherche toutes les donne d un identifiant instagrame comme adress email tel et plein d autre mais tout en local)

https://usersearch.org/                           - search username cloud  (recherche username cloud)

https://github.com/sherlock-project/sherlock      - search username local  (recherche username local)

https://web-check.xyz/                            - recherche les vulnerabilités  (tres bonne outil permettant les recherche de faille des serv dns et ip sur des url)

https://osintframework.com/                       - OSINT PRO              (meilleur outil OSINT le plus pro jamais crée,y a rien a dire car il fait tout -__-)

https://www.exploit-db.com/              (Exploit-DB permet de rechercher des vulnérabilités connues et les exploits associés afin d’analyser et de tester la sécurité de logiciels et d’applications web)

https://github.com/TheRealDalunacrobate/DaProfiler - outil osint          (tres tres fort outil local recherche sur des compt sur des adress email et bien d autre il est utiliser par des expert francais car il est disponible que en france) 

https://github.com/mxrch/GitFive                   - gitub osint          (permet de tracker toutes les activité et donné comme adress email autre compt local adresse et autre d un compt gitub. PS : vous devez vraiment pas aimez ce gas)

# Installation et mise à jour de IPinfo CLI – Windows 11

Projet officiel : [GitHub – IPinfo CLI](https://github.com/ipinfo/cli?utm_source=chatgpt.com)

## 1. Télécharger et installer Go

Site officiel : [Go Downloads](https://go.dev/dl/?utm_source=chatgpt.com)

Télécharger la version Windows (`.msi`), puis lancer l'installateur.

Vérifier l'installation :

```
go version
```

## 2. Télécharger le code source

Ouvrir PowerShell et exécuter :

```
git clone https://github.com/ipinfo/cli ipinfo-cli
```

Accéder au dossier :

```
cd ipinfo-cli
```

## 3. Compiler et installer IPinfo CLI

```
go install ./ipinfo/
```

## 4. Vérifier l'installation

```
ipinfo version
```

## 5. Mettre à jour IPinfo CLI

Pour installer la dernière version disponible depuis les sources officielles :

```
go install github.com/ipinfo/cli/ipinfo@latest
```

Vérifier la version après la mise à jour :

```
ipinfo version
```

Liens officiels :

- [Code source GitHub](https://github.com/ipinfo/cli?utm_source=chatgpt.com)
- [Historique des versions](https://github.com/ipinfo/cli/releases?utm_source=chatgpt.com)
- [Téléchargement de Go](https://go.dev/dl/?utm_source=chatgpt.com)

## video yt :

https://www.youtube.com/watch?v=8XDRUk4soS8
