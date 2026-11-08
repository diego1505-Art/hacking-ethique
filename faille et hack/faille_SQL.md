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
