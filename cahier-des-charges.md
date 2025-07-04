# Cahier des charges - Application de messagerie avec IA

L'objectif de ce projet est de concevoir et développer une application de messagerie interactive intégrant une IA. Cette application permet aux utilisateurs de créer des conversations, d'envoyer et de recevoir des messages, et d'interagir avec un modèle d'IA via une API externe.

## Fonctionnalités principales

### Gestion des Messages

- Affichage des messages sous forme de discussion (utilisateur vs IA).
- Envoi d'un message utilisateur et stockage en base de données locale.
- Envoi du message à une API externe d'IA et récupération de la réponse.
- Affichage de la réponse de l'IA et stockage en base de données locale.

### Gestion du Token d'Authentification

- Saisie et enregistrement d'un token API dans le stockage local.
- Vérification de la présence du token avant d'envoyer une requête à l'API d'IA.

### Gestion des Conversations

- Affichage des conversations existantes récupérées depuis une API locale.
- Sélection d'une conversation pour afficher les messages associés.
- Création d'une nouvelle conversation avec un titre personnalisé.
- Suppression d'une conversation avec mise à jour de l'interface utilisateur.

## Technologies utilisées

- **Framework Frontend** : Svelte
- **Bibliothèques** :
  - `svelte-exmarkdown` pour l'affichage des messages en Markdown
  - [Ce fichier css](https://github.com/sindresorhus/github-markdown-css/blob/main/github-markdown.css) pour styliser le markdown rapidement
- **Backend API** : Pocketbase pour stocker les messages et conversations
- **API IA** : Service externe (ex : Mistral AI)
- **Stockage** : LocalStorage pour la gestion du token API

## Architecture de l'application

### Composants principaux

On peut s'inspirer des outils existants tels que [Le Chat Mistral](https://chat.mistral.ai/chat) ou [ChatGPT](https://chatgpt.com/).

- **Interface de gestion des conversations** : liste des conversations disponibles avec possibilité de sélection.
- **Zone de chat** : affichage des messages avec distinction entre utilisateur et IA.
- **Zone de saisie** : champ pour entrer un message et bouton d'envoi.
- **Système de gestion des tokens** : formulaire de saisie pour l'authentification de l'utilisateur auprès de l'API IA.

### Echanges API

#### API locale :

- Récupération des conversations (`GET /collections/conversations/records`)
- Création d'une conversation (`POST /collections/conversations/records`)
- Suppression d'une conversation (`DELETE /collections/conversations/records/{id}`)
- Récupération des messages (`GET /collections/messages/records?filter=conversation_id`)
- Envoi d'un message (`POST /collections/messages/records`)

#### API IA :

Envoi d'un message et récupération de la réponse (`POST https://api.mistral.ai/v1/chat/completions`)

## Contraintes et spécifications techniques

- L'application doit être responsive et utilisable sur desktop et mobile.
- Utilisation de classes CSS spécifiques pour différencier les messages utilisateur et IA.
- Gestion des erreurs lors des appels API (ex : problème de connexion, réponse invalide).

## Livrables

Code source du projet

## Etapes

1. J1 - Mise en place du projet Svelte et intégration HTML/CSS
2. J2 - Implémentation de l'échange de messages avec Mistral
3. J3 - Persistance des données à l'aide de Pocketbase pour conserver l'historique de messages
4. J4 - Implémentation d'un système de conversations
