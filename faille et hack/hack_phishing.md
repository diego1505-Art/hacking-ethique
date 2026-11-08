# Phishing — comprendre et simuler en laboratoire

Le phishing consiste à tromper une personne afin de lui faire révéler une information ou effectuer une action. Cette note sert à comprendre les signaux d’une campagne, construire une sensibilisation et tester des défenses avec des comptes de démonstration.

> **Interdit :** cloner un vrai service pour récupérer des identifiants, publier une page sur Internet, utiliser un tunnel public, collecter une caméra, un microphone ou une localisation, ou envoyer un lien à une personne sans consentement explicite.

## Projets cités dans la note originale

| Projet | Lien | Explication |
|---|---|---|
| Zphisher | [Dépôt GitHub](https://github.com/htr-tech/zphisher) | Projet cité pour étudier les mécanismes de pages de phishing. À utiliser uniquement pour lire le code et créer une simulation locale sans collecte de secrets. |
| Storm-Breaker | [Dépôt GitHub](https://github.com/ultrasecurity/Storm-Breaker) | Projet cité pour analyser les risques liés à la collecte de données par une page malveillante. Ne pas déployer ni utiliser sur une personne. |
| Seeker | [Dépôt GitHub](https://github.com/thewhiteh4t/seeker) | Projet cité pour comprendre les risques de géolocalisation et de collecte de données. Ne pas utiliser pour localiser quelqu’un. |
| Grabify | [Ouvrir](https://grabify.org/) | Service cité dans la note ; ne l’utiliser que dans un exercice explicitement autorisé et transparent. |
| Article sur le suivi IP | [Lire](https://curiouspatch.com/en/articles/understanding-ip-address-tracking-and-servers) | Présentation générale des risques du suivi d’adresse IP. |

## Lire un projet localement sans le déployer

La première étape consiste à cloner le dépôt dans une VM isolée et à lire sa documentation :

```bash
git clone --depth=1 https://github.com/htr-tech/zphisher.git
cd zphisher
sed -n '1,220p' README.md
```

Pour examiner les autres projets :

```bash
cd ..
git clone https://github.com/ultrasecurity/Storm-Breaker.git
git clone https://github.com/thewhiteh4t/seeker.git
```

N’exécutez pas les scripts d’installation ou de collecte sans avoir vérifié le code, les dépendances, les destinations réseau et le périmètre d’autorisation.

## Simulation pédagogique recommandée

Pour une sensibilisation, créez une page locale inoffensive qui :

- affiche un message de formation ;
- ne demande aucun vrai mot de passe ;
- ne collecte aucune adresse IP ou donnée personnelle ;
- explique les indices qui permettent de reconnaître le piège ;
- reste accessible uniquement sur `127.0.0.1` ou sur un réseau de test.

Exemple pour servir des fichiers statiques locaux :

```bash
mkdir simulation-phishing
cd simulation-phishing
printf '<h1>Simulation de sensibilisation</h1><p>Aucun identifiant n’a été collecté.</p>\n' > index.html
python3 -m http.server 8000 --bind 127.0.0.1
```

Ouvrez ensuite `http://127.0.0.1:8000` dans une VM de test. Arrêtez le serveur avec `Ctrl+C`.

## Signaux à apprendre à repérer

- domaine légèrement différent de l’original ;
- urgence artificielle ou menace ;
- pièce jointe inattendue ;
- demande de mot de passe ou de code MFA ;
- lien raccourci ou redirection inhabituelle ;
- fautes, incohérences de marque ou expéditeur inattendu.

## Protection

Activez l’authentification multifacteur, utilisez un gestionnaire de mots de passe, vérifiez le domaine avant de vous connecter et signalez les messages suspects au responsable informatique.
