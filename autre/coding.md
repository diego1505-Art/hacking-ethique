# IA pour coder — cloud, local et outils agentiques

Cette page rassemble les assistants de programmation mentionnés dans le projet. Elle distingue les services **cloud**, qui envoient généralement le contexte vers une infrastructure distante, des outils **locaux**, qui permettent d’exécuter un modèle sur son propre ordinateur.

Le mot « uncensored » ne garantit ni la qualité, ni la confidentialité, ni la légalité d’un outil. Un modèle local reste soumis aux lois, aux licences des modèles et aux risques de fuite de données. Utilisez des données de test, vérifiez les changements produits par l’agent et ne lui donnez pas automatiquement accès à vos secrets, clés SSH ou fichiers personnels.

## Services cloud et assistants de développement

| Outil | Lien officiel | Type | Explication |
|---|---|---|---|
| Uncensored Chat | [Ouvrir](https://uncensored.chat/chat/) | Cloud | Service de conversation cité dans la note originale. Ne lui transmettre aucune donnée sensible et vérifier ses conditions d’utilisation. |
| HackerAI | [Ouvrir](https://hackerai.co/) | Cloud | Service orienté cybersécurité cité dans le projet. Utiliser ses réponses pour apprendre et vérifier les commandes avant toute exécution. |
| Manus | [Ouvrir](https://manus.im/) | Cloud | Agent généraliste capable d’aider à créer des sites, des programmes, des documents et des projets. Il peut utiliser des outils : il faut relire et valider ses actions. |
| Claude / Claude Code | [Claude Code](https://www.anthropic.com/claude-code) | Cloud avec terminal local | Assistant qui peut analyser un dépôt, proposer un plan, modifier des fichiers, lancer des tests et travailler depuis un terminal ou un IDE. Les droits d’exécution doivent rester contrôlés. |
| VS Code Agent | [Agent mode](https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode) | IDE connecté au cloud | Mode agent de VS Code pour planifier des changements, modifier plusieurs fichiers et utiliser des outils avec validation de l’utilisateur. |
| Cursor | [Ouvrir](https://www.cursor.com/) | IDE connecté au cloud | Éditeur orienté agents et génération de code. Il peut travailler en parallèle et modifier un projet ; utilisez Git et les revues de diff. |
| Trae AI | [Ouvrir](https://www.trae.ai/) | IDE et agent cloud | Éditeur avec modes d’assistance et d’agent, dont des workflows qui planifient puis exécutent plusieurs étapes. Vérifiez la politique de confidentialité avant d’ouvrir un dépôt privé. |
| OpenAI Codex | [Ouvrir](https://openai.com/codex/) | Agent cloud / outils de développement | Assistant de programmation pour comprendre, modifier et tester du code selon les fonctions disponibles dans le produit. |
| Freebuff | [Ouvrir](https://freebuff.com/) | Agent cloud avec clients desktop, mobile et terminal | Le client peut être installé localement, mais les threads et le traitement sont présentés comme cloud. Ce n’est donc pas un moteur de modèle local hors ligne. |

## Bon usage des assistants cloud

Avant d’ouvrir un dépôt, retirez les fichiers `.env`, les clés API, les certificats, les tokens et les données personnelles. Commencez avec un dossier de test et un dépôt Git propre :

```bash
git status
git diff
```

Demandez d’abord à l’agent d’expliquer son plan. Après chaque modification, relisez le diff puis lancez les tests vous-même :

```bash
git diff
# Exemple à adapter au projet :
npm test
# ou
python -m pytest
```

Ne demandez pas à un agent de désactiver l’antivirus, de contourner des contrôles d’accès ou d’exécuter une commande dont vous ne comprenez pas l’effet.

## Exécution locale avec Ollama

[Ollama](https://ollama.com/) permet de télécharger et d’exécuter des modèles ouverts sur Windows, macOS et Linux. Les modèles et leurs licences varient : consultez la fiche du modèle avant le téléchargement.

### Installation

Téléchargez l’installeur depuis le site officiel. Sous Linux, utilisez uniquement la commande publiée par le site officiel et relisez le script avant de l’exécuter. Une fois Ollama installé :

```bash
ollama --version
ollama list
```

### Télécharger et lancer un modèle gratuit

Les tailles exactes et les noms disponibles peuvent évoluer. Ces exemples utilisent le catalogue Ollama :

```bash
ollama pull qwen3:4b
ollama run qwen3:4b
```

Autres modèles à consulter dans le catalogue :

| Modèle | Catalogue | Profil général |
|---|---|---|
| Qwen3 | [Ollama](https://ollama.com/library/qwen3) | Modèles compacts et polyvalents, avec plusieurs tailles. |
| Gemma 3 | [Ollama](https://ollama.com/library/gemma3) | Modèles ouverts de Google, disponibles en plusieurs tailles. |
| Mistral | [Ollama](https://ollama.com/library/mistral) | Modèles compacts adaptés à de nombreux usages de texte et de code. |
| DeepSeek-R1 | [Ollama](https://ollama.com/library/deepseek-r1) | Modèles orientés raisonnement ; contrôler les réponses et les licences. |
| Llama 3.2 | [Ollama](https://ollama.com/library/llama3.2) | Modèles compacts pour expérimenter en local. |

Commandes de base :

```bash
ollama list
ollama show qwen3:4b
ollama run qwen3:4b
ollama rm qwen3:4b
```

### Utiliser Ollama avec un projet

Ollama expose une API locale. Vérifiez d’abord que le serveur local est actif, puis utilisez votre bibliothèque préférée. Ne publiez pas le port local sur Internet et ne placez pas de secret dans le prompt.

## Exécution locale avec LM Studio

[LM Studio](https://lmstudio.ai/) fournit une interface graphique pour rechercher, télécharger et exécuter des modèles locaux. Il convient surtout aux personnes qui préfèrent choisir un modèle, sa quantification et les paramètres depuis une interface.

### Procédure

1. Télécharger LM Studio depuis le site officiel.
2. Choisir un modèle compatible avec la mémoire RAM ou VRAM disponible.
3. Télécharger une version quantifiée adaptée à la machine.
4. Charger le modèle dans le chat local.
5. Désactiver les fonctions réseau inutiles lorsque vous manipulez des données sensibles.
6. Si vous activez un serveur local compatible OpenAI, le laisser lié à `127.0.0.1` et l’arrêter après le test.

LM Studio et Ollama peuvent exécuter des familles de modèles similaires, mais ils ne sont pas obligés d’utiliser exactement les mêmes formats ou paramètres.

## Heretic : modification expérimentale d’un modèle

[Heretic](https://github.com/p-e-w/heretic) n’est ni un chatbot cloud ni un moteur de génération. C’est un outil de modification de modèles transformer qui applique une technique appelée *abliteration* afin de réduire certaines tendances au refus. Le dépôt indique que le processus est automatique, expérimental et dépend fortement du modèle, du matériel et de la configuration.

Une modification qui réduit les refus peut aussi réduire la fiabilité, la robustesse et la capacité du modèle à distinguer une demande légitime d’une demande dangereuse. Il faut conserver le modèle original, vérifier la licence du modèle et évaluer le résultat uniquement sur des prompts de test non dangereux.

### Installation isolée

Heretic demande Python 3.10 ou une version ultérieure et une installation PyTorch adaptée au matériel. Dans un environnement de test :

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -U heretic-llm
heretic --help
```

Sous Windows PowerShell, l’activation s’écrit :

```powershell
py -3 -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -U heretic-llm
heretic --help
```

Le dépôt officiel donne l’exemple d’un modèle Hugging Face compatible. Avant de lancer un traitement coûteux, lisez la documentation et testez avec un petit modèle que votre machine peut charger. Heretic peut nécessiter beaucoup de RAM ou de VRAM et produire une copie modifiée volumineuse.

Après modification, faites des tests de qualité, de factualité, de robustesse et de sécurité. Ne mettez pas directement un modèle modifié en production et ne l’utilisez pas pour contourner des contrôles d’accès ou fabriquer du contenu nuisible.

## Choisir entre cloud et local

| Besoin | Choix conseillé |
|---|---|
| Commencer rapidement sans GPU | Assistant cloud ou Ollama avec un petit modèle quantifié. |
| Garder un dépôt sensible hors d’un service externe | Ollama ou LM Studio, après vérification des fonctions réseau. |
| Obtenir une aide agentique qui modifie un projet | Claude Code, Cursor, VS Code Agent, Trae, Codex ou Manus, avec revue des changements. |
| Tester plusieurs modèles locaux avec une interface | LM Studio. |
| Automatiser l’exécution locale par terminal ou API | Ollama. |
| Étudier les effets d’une modification de modèle | Heretic dans une VM ou un environnement Python séparé, avec le modèle original conservé. |

## Règles de sécurité

- Ne jamais coller une clé API, un mot de passe ou une donnée personnelle dans un chatbot.
- Toujours sauvegarder le projet avant de laisser un agent modifier plusieurs fichiers.
- Vérifier les commandes générées avant de les exécuter.
- Utiliser des modèles et des jeux de données dont la licence autorise l’usage prévu.
- Garder les serveurs locaux liés à `127.0.0.1` sauf besoin clairement justifié.
- Ne pas confondre « moins de garde-fous » avec « plus fiable » ou « plus compétent ».
