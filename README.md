# Hacking éthique

Catalogue des outils, projets et ressources présents dans ce dépôt. Les ressources sont regroupées par catégorie, avec une description courte et un lien vers la note Markdown qui contient les détails.

> **Avertissement légal** — Utilisez ces ressources uniquement sur vos propres systèmes, dans un laboratoire isolé ou avec une autorisation écrite explicite. Les sections consacrées aux failles, au phishing, aux malwares et au déni de service sont uniquement destinées à l’apprentissage, à la défense et aux tests contrôlés.

## Sommaire

- [Cryptographie](#cryptographie)
- [Forensics et analyse de fichiers](#forensics-et-analyse-de-fichiers)
- [OSINT et collecte d’informations](#osint-et-collecte-dinformations)
- [Failles web et injection SQL](#failles-web-et-injection-sql)
- [Malwares, Metasploit et laboratoire](#malwares-metasploit-et-laboratoire)
- [Phishing et ingénierie sociale](#phishing-et-ingénierie-sociale)
- [DDoS et résilience réseau](#ddos-et-résilience-réseau)
- [IA et outils de programmation](#ia-et-outils-de-programmation)
- [Ressources générales](#ressources-générales)

## Cryptographie

Outils en ligne pour encoder, décoder, hacher, analyser et convertir des données dans le cadre d’exercices de cryptographie.

Détails : [Cryptographie/site.md](Cryptographie/site.md)

| Outil | Lien | Description |
|---|---|---|
| Base64 Decode | [Ouvrir](https://www.base64decode.org/fr/) | Encoder et décoder des messages en Base64. |
| CyberChef | [Ouvrir](https://gchq.github.io/CyberChef/) | Atelier polyvalent pour encoder, décoder, transformer et analyser des données. |
| PleaseTools | [Ouvrir](https://pleasetools.com/) | Collection d’outils de hachage, chiffrement, analyse et conversion. |
| CrackStation | [Ouvrir](https://crackstation.net/) | Analyse de valeurs hachées et recherche dans une base de hachages connus. |

## Forensics et analyse de fichiers

Ressources pour examiner des fichiers, extraire des métadonnées et rechercher des traces ou des manipulations dans un contexte d’investigation numérique.

Détails : [Forensics/site.md](Forensics/site.md)

| Outil | Lien | Description |
|---|---|---|
| iLovePDF — déverrouillage PDF | [Ouvrir](https://www.ilovepdf.com/fr/deverrouiller_pdf) | Outil de traitement et de déverrouillage de fichiers PDF dont vous avez l’autorisation. |
| AperiSolve | [Ouvrir](https://www.aperisolve.com/fr/) | Analyse d’images et recherche d’informations ou de données dissimulées. |
| Jimpl | [Ouvrir](https://jimpl.com/) | Lecture des métadonnées EXIF de différents types de fichiers. |
| Convert Guru | [Ouvrir](https://convert.guru/fr/convertisseur) | Conversion et analyse de fichiers. |
| Tembric — Audio Forensics | [Ouvrir](https://tembrica.com/fr/audio-forensics) | Détection de manipulations audio et de deepfakes. |
| ExifTool | [Ouvrir](https://exiftool.org/) | Lecture et modification des métadonnées de fichiers, notamment les données EXIF. |

## OSINT et collecte d’informations

Outils de recherche en sources ouvertes pour étudier des pseudonymes, comptes, adresses e-mail, métadonnées, domaines et informations publiques dans un cadre autorisé.

Détails : [OSINT/site.md](OSINT/site.md)

| Outil | Lien | Description |
|---|---|---|
| Pics.io Metadata Viewer | [Ouvrir](https://pics.io/photo-metadata-viewer-fr) | Analyse des métadonnées EXIF d’une image : GPS, date, appareil, etc. |
| h8mail | [Dépôt GitHub](https://github.com/khast3x/h8mail) | Recherche OSINT liée aux adresses e-mail et aux fuites connues, en local. |
| Toutatis | [Dépôt GitHub](https://github.com/megadose/toutatis) | Recherche d’informations publiques associées à un identifiant Instagram. |
| UserSearch | [Ouvrir](https://usersearch.org/) | Recherche d’un nom d’utilisateur sur différents services en ligne. |
| Sherlock | [Dépôt GitHub](https://github.com/sherlock-project/sherlock) | Recherche d’un pseudonyme sur de nombreuses plateformes. |
| Web-Check | [Ouvrir](https://web-check.xyz/) | Vérifications et reconnaissance de domaines, services, DNS et éléments exposés. |
| OSINT Framework | [Ouvrir](https://osintframework.com/) | Répertoire organisé de ressources et méthodes OSINT. |
| Exploit-DB | [Ouvrir](https://www.exploit-db.com/) | Base de données de vulnérabilités et d’exploits publics pour l’analyse défensive. |
| DaProfiler | [Dépôt GitHub](https://github.com/TheRealDalunacrobate/DaProfiler) | Outil local de recherche d’informations publiques liées à des comptes et adresses e-mail. |
| GitFive | [Dépôt GitHub](https://github.com/mxrch/GitFive) | Recherche d’informations publiques et d’activité associées à GitHub. |
| IPinfo CLI | [Dépôt GitHub](https://github.com/ipinfo/cli?utm_source=chatgpt.com) | Outil en ligne de commande pour interroger des informations IP. |
| Releases IPinfo CLI | [Versions](https://github.com/ipinfo/cli/releases?utm_source=chatgpt.com) | Historique des versions d’IPinfo CLI. |
| Go | [Téléchargements](https://go.dev/dl/?utm_source=chatgpt.com) | Dépendance utilisée dans la note d’installation d’IPinfo CLI sous Windows. |
| Tutoriel IPinfo CLI | [Vidéo YouTube](https://www.youtube.com/watch?v=8XDRUk4soS8) | Vidéo associée à l’installation ou à l’utilisation de l’outil. |

## Failles web et injection SQL

Cette catégorie regroupe les notes pédagogiques sur les vulnérabilités web et les environnements d’entraînement. Les essais doivent rester limités à des applications volontairement vulnérables et à des laboratoires locaux.

Détails : [faille et hack/faille.md](faille%20et%20hack/faille.md) · [faille et hack/faille_SQL.md](faille%20et%20hack/faille_SQL.md)

| Ressource | Lien | Description |
|---|---|---|
| Panorama de failles web | [Lire la note](faille%20et%20hack/faille.md) | Exemples introductifs de familles de vulnérabilités web à étudier dans un lab isolé. |
| Injection SQL | [Lire la note](faille%20et%20hack/faille_SQL.md) | Notes sur l’injection SQL, SQLmap, Burp Suite et DVWA. |
| SQLmap — introduction | [Vidéo YouTube](https://www.youtube.com/watch?v=CoiA-6qhzvE) | Présentation débutant de SQLmap. |
| SQLmap — exemple | [Vidéo YouTube](https://www.youtube.com/watch?v=fbt50vQfWZg) | Exemple d’utilisation de SQLmap dans un environnement de test. |
| DVWA — niveau débutant | [Vidéo YouTube](https://www.youtube.com/watch?v=ex4003kemTc&list=PLdZk2ypV8xBGn_KjnGWODTAm4iNBoNrtK&index=2) | Entraînement sur une application volontairement vulnérable. |
| Burp Suite — introduction | [Vidéo YouTube](https://www.youtube.com/watch?v=dbfciJsFJIA) | Découverte de Burp Suite. |
| Burp Suite — tutoriel complet | [Vidéo YouTube](https://www.youtube.com/watch?v=fpx1fjBI-uI) | Parcours général d’utilisation de Burp Suite. |
| Burp Suite — niveau avancé | [Vidéo YouTube](https://www.youtube.com/watch?v=KWOs0Waq2TM&t=742s) | Approches avancées présentées dans la note. |
| Burp Suite — brute force et SQLi | [Vidéo YouTube](https://www.youtube.com/watch?v=1sYa65LsL94) | Démonstration à reproduire uniquement sur une cible de laboratoire. |
| Google Dorks SQLi | [Fichier GitHub](https://github.com/Proviesec/google-dorks/blob/main/google-dorks-for-sql-injection.txt) | Exemples de recherches à étudier pour comprendre l’exposition de ressources. |

## Malwares, Metasploit et laboratoire

Projet long consacré à Metasploit, aux modules, aux payloads et à la mise en place d’un environnement de laboratoire avec Kali Linux et Windows virtuels.

Détails : [faille et hack/hack_les malwars.md](faille%20et%20hack/hack_les%20malwars.md)

| Ressource | Lien | Description |
|---|---|---|
| Note complète Malwares / Metasploit | [Lire le MD](faille%20et%20hack/hack_les%20malwars.md) | Explication générale de Metasploit, de ses modules et de l’analyse de payloads en environnement virtuel. |
| PuTTY 64 bits | [Téléchargement](https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe) | Exécutable légitime cité comme modèle de laboratoire dans la note. |
| PuTTY 32 bits | [Téléchargement](https://the.earth.li/~sgtatham/putty/latest/w32/putty.exe) | Variante 32 bits citée dans la note. |
| Chrome Installer | [Téléchargement](https://dl.google.com/chrome/install/latest/chrome_installer.exe) | Installateur officiel cité comme exemple de fichier légitime. |
| Firefox Installer | [Téléchargement](https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=fr) | Installateur officiel Firefox cité dans la note. |
| Notepad++ | [Téléchargement](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v8.5.4/npp.8.5.4.Installer.exe) | Installateur d’un outil légitime cité comme exemple. |
| 7-Zip | [Téléchargement](https://www.7-zip.org/a/7z2201.exe) | Utilitaire de compression cité dans la note. |
| Ressource d’analyse complémentaire | [Ouvrir](https://github.com/user-attachments/assets/66c3f45b-dbcd-41a9-be69-3c94079fe26e) | Lien présent dans la note originale ; consulter le fichier MD pour son contexte. |

## Phishing et ingénierie sociale

Outils et ressources mentionnés dans les notes sur la simulation de phishing, la sensibilisation et les tests contrôlés. Ne jamais les utiliser contre des personnes ou services sans consentement explicite.

Détails : [faille et hack/hack_phishing.md](faille%20et%20hack/hack_phishing.md)

| Ressource | Lien | Description |
|---|---|---|
| Zphisher | [Dépôt GitHub](https://github.com/htr-tech/zphisher) | Projet cité dans la note pour étudier les mécanismes de pages de sensibilisation et de simulation. |
| Storm-Breaker | [Dépôt GitHub](https://github.com/ultrasecurity/Storm-Breaker) | Projet cité dans la note pour analyser les risques liés aux campagnes de phishing. |
| Seeker | [Dépôt GitHub](https://github.com/thewhiteh4t/seeker) | Projet cité pour étudier les risques de collecte de localisation et de données. |
| Grabify | [Ouvrir](https://grabify.org/) | Service cité dans la note ; à réserver à des tests autorisés et transparents. |
| Article de présentation du suivi IP | [Lire](https://curiouspatch.com/en/articles/understanding-ip-address-tracking-and-servers?tkn=eyJhbGciOiJIUzI1NiJ9.eyJhZHRpdGxlIjoiZ3JhYmlmeS5uZXQiLCJjaGFubmVsIjoiZF8wMTAxMiIsImNvdW50cnkiOiJmciIsImRvbWFpbiI6ImN1cmlvdXNwYXRjaC5jb20iLCJleHAiOjE3OTM1NTg1MTgsImxhbmciOiJFTiIsImxhbmd1YWdlIjoiRU4iLCJzYWxlYmFubmVyIjp7ImxpbmsiOiJodHRwczovL3d3dy5teWRvbWFpbmNvbnRhY3QuY29tLz9kb21haW5fbmFtZT1ncmFiaWZ5Lm5ldCIsInRleHQiOiJJbmZvcm1hdGlvbiBhYm91dCAgZ3JhYmlmeS5uZXQ6IC1ALUFjaGV0ZXIgY2UgZG9tYWluZS4tQC0iLCJ0eXBlIjoic3VidGxlIn0sInRhcmdldF91cmwiOiJodHRwczovL2N1cmlvdXNwYXRjaC5jb20vZW4vYXJ0aWNsZXMvdW5kZXJzdGFuZGluZy1pcC1hZGRyZXNzLXRyYWNraW5nLWFuZC1zZXJ2ZXJzIiwidHJhY2tfaWQiOiI4NzcxZDdiM2ZlNTM3ZDY3MjMwMTE0YzM0Y2RlMmQ2OTg4MzkzNjZhIn0.CBYQ051zj4deQ-Q8x9gJGGlQFMbXcWbjdSRAoxTt8fs) | Article présent dans la note originale sur le fonctionnement du suivi d’adresse IP. |
| Lien de test présent dans la note | [Ouvrir](https://grabber.cy/ef2a1ec59d44da97b667ffb917b814f1/login) | Lien conservé uniquement pour refléter le contenu original ; ne pas utiliser sur autrui. |

## DDoS et résilience réseau

Notes sur plusieurs outils de génération de trafic. Cette section doit servir à comprendre les risques et à tester la résilience d’une infrastructure vous appartenant, jamais à perturber un service tiers.

Détails : [faille et hack/hack_ddos.md](faille%20et%20hack/hack_ddos.md)

| Projet | Lien | Description |
|---|---|---|
| Ultra-DDos | [Dépôt GitHub](https://github.com/mishakorzik/Ultra-DDos) | Projet cité dans la note pour étudier la génération de trafic et ses risques. |
| UnstableDDoS | [Dépôt GitHub](https://github.com/iJoshoa/UnstableDDoS) | Projet cité pour analyser différents paramètres de trafic dans un lab contrôlé. |
| GreeDoS V2 | [Dépôt GitHub](https://github.com/MrEchoFi/GreeDoS_V2) | Projet cité dans la note pour étudier la configuration de tests de charge autorisés. |

## IA et outils de programmation

Catalogue séparé des assistants cloud, des agents de programmation, des runtimes locaux comme Ollama et LM Studio, ainsi que des modèles gratuits et du projet Heretic.

Détails : [autre/coding.md](autre/coding.md)

| Ressource | Lien | Description |
|---|---|---|
| Coding et IA cloud/local | [Lire la note](autre/coding.md) | Comparaison cloud/local, commandes Ollama, installation LM Studio, modèles téléchargeables et présentation prudente de Heretic. |

## Ressources générales

Ressources complémentaires liées à l’apprentissage, à l’analyse de malwares, aux identités de test et à la recherche de documentation.

Détails : [autre/site.md](autre/site.md)

| Ressource | Lien | Description |
|---|---|---|
| VX-Underground | [Ouvrir](https://vx-underground.org/) | Banque de ressources et d’échantillons utilisée pour la veille et l’analyse défensive des malwares. |
| Hacker Roadmap | [Dépôt GitHub](https://github.com/sundowndev/hacker-roadmap) | Parcours et ressources pour structurer l’apprentissage de la cybersécurité. |
| Fake Name Generator | [Ouvrir](https://www.fakenamegenerator.com/) | Génération d’identités fictives pour des comptes et scénarios de test, sans usurpation. |
| FMHY | [Ouvrir](https://fmhy.net/) | Répertoire général de ressources en ligne cité dans la note. |

## Notes du dépôt

Les descriptions détaillées, commandes, exemples et captures sont conservés dans les fichiers Markdown suivants :

- [Cryptographie/README.md](Cryptographie/README.md) — explication de la catégorie cryptographie.
- [Cryptographie/site.md](Cryptographie/site.md)
- [Forensics/README.md](Forensics/README.md) — explication de la catégorie forensics.
- [Forensics/site.md](Forensics/site.md)
- [OSINT/README.md](OSINT/README.md) — explication de la catégorie OSINT.
- [OSINT/site.md](OSINT/site.md)
- [autre/site.md](autre/site.md)
- [autre/coding.md](autre/coding.md)
- [faille et hack/faille.md](faille%20et%20hack/faille.md)
- [faille et hack/faille_SQL.md](faille%20et%20hack/faille_SQL.md)
- [faille et hack/hack_ddos.md](faille%20et%20hack/hack_ddos.md)
- [faille et hack/hack_les malwars.md](faille%20et%20hack/hack_les%20malwars.md)
- [faille et hack/hack_phishing.md](faille%20et%20hack/hack_phishing.md)
