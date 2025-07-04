# 🌐 Appeler une API en JavaScript avec fetch

## Qu'est-ce qu'une API ?

Une **API** (Application Programming Interface) est une porte d'entrée qui permet à un programme (ici, ton application JavaScript) de communiquer avec un autre service (par exemple : une IA, une base de données, un service météo, etc.).

- On "appelle" une API pour demander ou envoyer des informations.
- Les réponses sont souvent au format **JSON** (texte structuré).

## Pourquoi et quand utiliser une API ?

- Pour récupérer des données à afficher (ex : météo, messages, utilisateurs...)
- Pour envoyer des informations (ex : formulaire, message, score...)
- Pour interagir avec des services externes (ex : IA, paiement, stockage...)

## Comment faire un appel GET simple avec fetch

```js
fetch("https://api.exemple.com/endpoint")
  .then(response => response.json())
  .then(data => {
    console.log(data); // Les données reçues
  });
```

- `fetch` prend en paramètre l'URL de l'API.
- On utilise `.then(response => response.json())` pour lire la réponse au format JSON.

## Comment faire un appel POST avec fetch

```js
fetch("https://api.exemple.com/endpoint", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    nom: "Alice",
    age: 25
  })
})
  .then(response => response.json())
  .then(data => {
    console.log(data);
  });
```

- `method: "POST"` indique qu'on envoie des données.
- `headers` précise le type de contenu envoyé.
- `body` contient les données à envoyer (toujours sous forme de texte JSON).

## Ajouter un header Authorization Bearer

Certaines API demandent une "clé d'accès" (token) pour vérifier que tu es autorisé à utiliser le service. On la transmet dans le header `Authorization` avec le mot-clé **Bearer**.

### Exemple avec Bearer

```js
const token = "VOTRE_TOKEN_ICI";

fetch("https://api.exemple.com/endpoint", {
  method: "GET",
  headers: {
    "Authorization": "Bearer " + token
  }
})
  .then(response => response.json())
  .then(data => {
    console.log(data);
  });
```

- Le header `Authorization: Bearer ...` permet à l'API de savoir qui fait la demande.
- **Bearer** signifie littéralement "porteur" : c'est le porteur du token qui est autorisé.
- On place le mot "Bearer" suivi d'un espace, puis le token.

## Bonnes pratiques et pièges à éviter

- Toujours vérifier la réponse de l'API (`response.ok`) avant d'utiliser les données.
- Ne jamais afficher ou partager un token en public.
- Ne pas stocker de données sensibles dans le code source.
- Bien gérer les erreurs (API indisponible, mauvais token, etc.).

## Pour aller plus loin

- [MDN Web Docs - fetch](https://developer.mozilla.org/fr/docs/Web/API/Fetch_API)
- [MDN Web Docs - HTTP headers](https://developer.mozilla.org/fr/docs/Web/HTTP/Headers) 