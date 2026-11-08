# Cryptographie — outils en ligne

Cette catégorie rassemble des sites utiles pour comprendre les encodages, les hachages et les transformations de données. Ces outils sont pratiques pour les exercices de CTF, l’analyse de fichiers de test et l’apprentissage des bases.

> **À retenir :** Base64 n’est pas un chiffrement : c’est un encodage réversible. Un hash, lui, est conçu pour être difficile à inverser. N’envoyez jamais de mot de passe, secret ou donnée personnelle réelle sur un site en ligne.

## Outils par usage

| Site | À quoi sert-il ? | Quand l’utiliser ? |
|---|---|---|
| [Base64 Decode](https://www.base64decode.org/fr/) | Encode et décode du texte en Base64. | Pour reconnaître et tester rapidement un encodage Base64. |
| [CyberChef](https://gchq.github.io/CyberChef/) | Enchaîne des opérations d’encodage, décodage, conversion, compression et analyse. | Pour explorer un texte ou un fichier de laboratoire étape par étape. |
| [PleaseTools](https://pleasetools.com/) | Regroupe des outils de hachage, conversion, encodage et analyse. | Pour comparer plusieurs formats pendant un exercice. |
| [CrackStation](https://crackstation.net/) | Compare des hachages avec une base de valeurs déjà connues. | Pour vérifier, en laboratoire, pourquoi un mot de passe faible peut être retrouvé. |

## Méthode conseillée

1. Identifier si la donnée est encodée, chiffrée ou hachée.
2. Travailler sur une copie ou une valeur de test.
3. Utiliser d’abord CyberChef pour observer les transformations.
4. Ne jamais considérer un résultat en ligne comme une preuve suffisante : vérifier l’opération localement lorsque c’est possible.

## Résumé

- **Encodage :** transforme une donnée pour la transporter ou la représenter.
- **Chiffrement :** protège une donnée avec une clé et doit être déchiffrable avec la bonne clé.
- **Hachage :** produit une empreinte normalement non réversible, utile pour vérifier l’intégrité ou stocker des mots de passe correctement.
