# Failles web — comprendre et corriger

Cette note présente plusieurs familles de failles web de manière pédagogique. Les exemples doivent être reproduits uniquement sur une application locale volontairement vulnérable, comme DVWA, WebGoat ou une application créée pour le test.

## 1. XXE — XML External Entity

Une faille XXE apparaît lorsqu’une application accepte du XML et autorise des entités externes sans filtrage adapté. Le serveur peut alors tenter de lire une ressource locale ou d’effectuer une requête sortante.

### Risques

- divulgation de fichiers ;
- requêtes vers des services internes ;
- consommation excessive de ressources ;
- fuite de secrets de configuration.

### Prévention

- désactiver les entités externes ;
- utiliser un parseur XML configuré en mode sécurisé ;
- limiter les schémas et les tailles de documents ;
- journaliser les erreurs sans révéler de contenu sensible.

## 2. Erreurs de validation des paramètres HTTP

Une API peut devenir vulnérable lorsqu’elle fait confiance à un identifiant, à une longueur ou à un format fourni par le client. Une valeur mal validée peut provoquer un accès non prévu, une erreur de logique ou un contournement d’autorisation.

### Vérifications défensives

- valider le type et la plage de chaque paramètre côté serveur ;
- refuser les valeurs inattendues et les conversions ambiguës ;
- vérifier les autorisations sur chaque objet demandé ;
- tester les réponses avec des valeurs limites dans un lab.

## 3. XSS — Cross-Site Scripting

Une XSS se produit lorsqu’une donnée fournie par un utilisateur est réinjectée dans une page sans échappement adapté. Le navigateur peut alors interpréter cette donnée comme du code au lieu de texte.

### Variantes

- **réfléchie :** la donnée revient immédiatement dans la réponse ;
- **stockée :** la donnée est enregistrée puis affichée à d’autres utilisateurs ;
- **DOM :** le problème vient d’un traitement JavaScript côté navigateur.

### Prévention

- échapper les sorties selon leur contexte HTML, attribut, URL ou JavaScript ;
- utiliser une politique CSP adaptée ;
- éviter `innerHTML` lorsque `textContent` suffit ;
- valider les entrées sans considérer la validation comme un remplacement de l’échappement.

## Laboratoire conseillé

Créez une application locale et vérifiez les correctifs avec un scanner autorisé. Ne testez jamais une URL publique sans permission écrite.

## Checklist de correction

- [ ] Les entrées sont validées côté serveur.
- [ ] Les sorties sont encodées selon leur contexte.
- [ ] Les parseurs XML sont configurés de manière sécurisée.
- [ ] Les contrôles d’accès sont appliqués côté serveur.
- [ ] Les journaux ne contiennent pas de secrets.
- [ ] Les tests sont réalisés dans un environnement isolé.
