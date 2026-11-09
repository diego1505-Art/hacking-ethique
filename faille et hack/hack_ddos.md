# DDoS — comprendre les risques et tester la résilience

Un déni de service distribué cherche à rendre un service indisponible en saturant ses ressources. Les projets listés ci-dessous peuvent générer du trafic agressif : ils ne doivent jamais être utilisés contre une IP, un domaine ou un service tiers.

Cette note est réorientée vers la compréhension, la détection et les tests de charge autorisés.

## Projets présents dans la note originale

| Projet | Lien | Explication |
|---|---|---|
| Ultra-DDos | [Dépôt GitHub](https://github.com/mishakorzik/Ultra-DDos) | Projet de génération de trafic cité pour étudier les risques d’un flux HTTP. À ne pas lancer contre Internet. |
| UnstableDDoS | [Dépôt GitHub](https://github.com/iJoshoa/UnstableDDoS) | Projet cité pour observer différents paramètres de trafic. Utilisation limitée à un réseau de lab isolé. |
| GreeDoS V2 | [Dépôt GitHub](https://github.com/MrEchoFi/GreeDoS_V2) | Projet cité pour analyser la variation de flux et de paramètres. Ne pas l’utiliser comme outil d’attaque. |

## Installation pour lecture et audit du code

Cloner un projet ne signifie pas l’exécuter. Commencez par lire son README et inspecter ses dépendances :

```bash
git clone https://github.com/mishakorzik/Ultra-DDos.git
cd Ultra-DDos
sed -n '1,220p' README.md
```

Pour analyser les deux autres dépôts dans des dossiers séparés :

```bash
cd ..
git clone https://github.com/iJoshoa/UnstableDDoS.git
git clone https://github.com/MrEchoFi/GreeDoS_V2.git
```

## Commandes de préparation des projets

Ces commandes reprennent les étapes de préparation présentes dans la note originale. Elles installent uniquement les dépendances et permettent de consulter l’aide ; elles ne lancent pas de trafic vers une cible.

### Ultra-DDos

```bash
sudo apt update
sudo apt upgrade
sudo apt install git python3 python3-pip
cd Ultra-DDos
python2 --version
python2 main.py --help
```

Si le projet demande sa dépendance Python indiquée dans sa documentation, installez-la dans la VM de laboratoire après avoir relu le paquet :

```bash
python3 -m pip install --break-system-packages user-agent
```

### UnstableDDoS

```bash
cd ../UnstableDDoS
sudo apt update
sudo apt upgrade
python3 -m pip install --break-system-packages pysocks bs4 scapy-python3
python3 UNSTABLE.py --help
```

### GreeDoS V2

```bash
cd ../GreeDoS_V2
sudo apt update
sudo apt upgrade
sudo apt install git python3 python3-pip
python3 -m pip install --break-system-packages pysocks bs4 scapy-python3
python3 GreeDoS_ii.py --help
```

Les scripts peuvent ne pas accepter `--help` selon leur version. Dans ce cas, arrêtez-vous à l’inspection du code et de leur documentation. Je ne fournis pas de commande de lancement de flood ni de cible à renseigner : même avec une IP locale, ces scripts sont conçus pour générer du trafic agressif. Pour un test de performance, utilisez plutôt le benchmark local et limité ci-dessous.

Avant toute exécution, examinez les scripts, les dépendances, les destinations réseau et les conditions de licence. Utilisez une VM sans accès à votre réseau de production.

## Test de charge bénin en local

Pour un service que vous avez écrit et qui écoute uniquement sur `127.0.0.1`, utilisez de préférence un outil de benchmark conçu pour le test de performance, avec un faible volume et une durée courte. Par exemple, installez ApacheBench :

```bash
sudo apt update
sudo apt install apache2-utils
ab -n 20 -c 2 http://127.0.0.1:8000/
```

Arrêtez immédiatement si le service ou la machine montre des signes de saturation. N’utilisez pas cette commande contre un domaine public.

## Défenses à étudier

- limitation de débit et quotas ;
- cache et CDN ;
- filtrage réseau ;
- files d’attente et timeouts ;
- supervision CPU, mémoire, connexions et bande passante ;
- plan de réponse à incident et contact de l’hébergeur.

## Conclusion

La valeur pédagogique de ces projets est d’apprendre à reconnaître un trafic anormal et à renforcer une infrastructure. La génération de trafic vers une cible non autorisée est illégale et peut causer une interruption de service.
