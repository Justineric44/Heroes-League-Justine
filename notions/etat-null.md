# ❓ Comprendre et utiliser `null` en JavaScript et dans Svelte

## Qu'est-ce que `null` ?

- `null` est une **valeur spéciale** en JavaScript qui signifie « il n'y a rien », « aucune valeur » ou « vide volontairement ».
- C'est différent de `undefined` (qui veut dire « pas encore défini ») et d'une chaîne vide `""` (qui est du texte, mais sans caractère).

| Valeur        | Signification                           |
|--------------|-----------------------------------------|
| `null`       | Vide volontairement, rien                |
| `undefined`  | Pas encore défini                        |
| `""`         | Chaîne de texte vide                     |

## Pourquoi utiliser `null` dans une variable d'état ?

Quand on écrit :
```js
let error = $state(null);
```
- On indique que **par défaut, il n'y a pas d'erreur**.
- Plus tard, si une erreur survient, on peut mettre un message d'erreur (ex : `error = "Erreur réseau";`).
- Si on veut effacer l'erreur, on remet `error = null;`.

## Comment tester si une variable est `null` ?

```js
if (error === null) {
  // Il n'y a pas d'erreur
}
if (error !== null) {
  // Il y a une erreur à afficher
}
```

## Exemple concret dans Svelte

```js
let error = $state(null);

// ...
if (response.ok === false) {
  error = "Problème avec l'API";
}
// ...
// Pour effacer l'erreur :
error = null;
```

Dans le HTML Svelte :
```svelte
{#if error !== null}
  <div class="error">{error}</div>
{/if}
```

## Bonnes pratiques

- Utiliser `null` pour dire « il n'y a rien » ou « pas d'erreur »
- Toujours tester avec `=== null` ou `!== null` (pas juste `if (error)`)
- Réinitialiser à `null` quand on veut effacer une valeur

## Pièges fréquents

- Ne pas confondre `null` et `undefined` (qui arrive si on oublie d'initialiser une variable)
- Ne pas confondre `null` et une chaîne vide `""` (qui est du texte, pas l'absence de valeur)
- Attention à l'affichage : afficher `null` dans le HTML ne montre rien (pas de texte)

## Pour aller plus loin
- [MDN Web Docs - null](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/null)
- [MDN Web Docs - undefined](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/undefined) 