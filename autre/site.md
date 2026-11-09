# Ressources générales

Cette page regroupe des ressources complémentaires pour apprendre la cybersécurité, préparer un environnement de test et trouver de la documentation.

## Ressources par objectif

| Ressource | Lien | Explication |
|---|---|---|
| VX-Underground | [Ouvrir](https://vx-underground.org/) | Collection de ressources et d’échantillons utiles à la veille et à l’analyse défensive des malwares. À consulter dans un environnement isolé. |
| Hacker Roadmap | [Dépôt GitHub](https://github.com/sundowndev/hacker-roadmap) | Parcours d’apprentissage et liste de projets pour progresser en cybersécurité. |
| Fake Name Generator | [Ouvrir](https://www.fakenamegenerator.com/) | Génère des identités fictives pour des comptes de démonstration ou des tests. Ne pas l’utiliser pour usurper l’identité d’une personne. |
| FMHY | [Ouvrir](https://fmhy.net/) | Répertoire général de ressources et de logiciels. Vérifier chaque téléchargement et privilégier les sources officielles. |

Les outils d’intelligence artificielle et les commandes d’installation locale sont documentés séparément dans [coding.md](coding.md).

## Bon environnement de travail

Pour les exercices de sécurité, utilisez de préférence :

- une machine virtuelle dédiée ;
- un réseau privé hôte ou un réseau interne ;
- des comptes de test sans données réelles ;
- des instantanés de machine avant chaque manipulation ;
- des logiciels téléchargés depuis leur dépôt officiel.

## Vérification avant téléchargement

```bash
sha256sum fichier-telecharge
```

Comparez ensuite l’empreinte avec celle publiée par l’éditeur lorsque cette information existe. N’exécutez jamais un fichier inconnu sur votre machine principale.
