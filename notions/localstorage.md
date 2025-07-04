# 📦 Comprendre et utiliser localStorage en JavaScript

## Qu'est-ce que localStorage ?

`localStorage` est une fonctionnalité du navigateur web qui permet de stocker des données (sous forme de texte) directement dans le navigateur de l'utilisateur. Les données restent enregistrées même si on ferme l'onglet ou le navigateur.

- **Capacité** : environ 5 Mo par site
- **Portée** : spécifique à chaque domaine (site)
- **Durée** : persiste tant que l'utilisateur ne vide pas le stockage ou que le site ne les supprime pas

## À quoi ça sert ?

- Garder en mémoire des préférences utilisateur (thème, langue...)
- Se souvenir d'un token d'authentification
- Retrouver un panier d'achat, des brouillons, etc.

## Comment stocker une valeur ?

```js
// Stocker une valeur (toujours sous forme de texte !)
localStorage.setItem("maCle", "maValeur");
```

## Comment lire une valeur ?

```js
// Lire une valeur (ou null si la clé n'existe pas)
const valeur = localStorage.getItem("maCle");
console.log(valeur); // Affiche "maValeur"
```

## Comment supprimer une valeur ?

```js
// Supprimer une valeur
localStorage.removeItem("maCle");
```

## Comment tout vider ?

```js
// Supprimer toutes les données du site
localStorage.clear();
```

## Bonnes pratiques et pièges à éviter

- **Tout est stocké en texte** : pour stocker un objet, il faut utiliser `JSON.stringify` et `JSON.parse`.
  ```js
  // Stocker un objet
  const user = { nom: "Alice", age: 25 };
  localStorage.setItem("utilisateur", JSON.stringify(user));

  // Lire un objet
  const userString = localStorage.getItem("utilisateur");
  const userObj = JSON.parse(userString);
  ```
- **Ne jamais stocker de données sensibles** (mot de passe, numéro de carte, etc.)
- **Attention à la taille** : ne pas stocker de gros fichiers ou images
- **localStorage est synchrone** : évitez d'y faire trop d'accès dans des boucles lourdes

## Exemple concret : retenir le pseudo d'un utilisateur

```js
// Au moment où l'utilisateur saisit son pseudo :
const pseudo = "Bob";
localStorage.setItem("pseudo", pseudo);

// Plus tard, pour le retrouver :
const pseudoSauvegarde = localStorage.getItem("pseudo");
if (pseudoSauvegarde !== null) {
  alert("Bienvenue, " + pseudoSauvegarde + " !");
}
```

## Sécurité et confidentialité

- Les données sont accessibles par **tout le JavaScript du site**
- Elles peuvent être lues par toute personne ayant accès à l'ordinateur (via les outils du navigateur)
- Ne jamais y stocker de secrets ou d'informations confidentielles

---

Pour aller plus loin : [MDN Web Docs - localStorage](https://developer.mozilla.org/fr/docs/Web/API/Window/localStorage) 