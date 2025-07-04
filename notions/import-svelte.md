# 📦 Importer des ressources dans un projet Svelte

Importer des fichiers (CSS, JS, images, etc.) est une étape courante dans le développement d'une application Svelte. Voici comment faire, étape par étape !

## Pourquoi importer des fichiers ?

- Ajouter des styles personnalisés (CSS)
- Utiliser des fonctions ou composants réutilisables (JS)
- Afficher des images ou des icônes
- Utiliser des librairies externes

## Importer un fichier CSS dans un composant Svelte

Pour appliquer des styles spécifiques à un composant, on peut importer un fichier CSS directement dans le script du composant :

```js
import "./md.css";
```

- Le chemin doit être relatif au fichier Svelte où se trouve l'import.
- Le CSS importé s'applique globalement (à toute l'application).

## Importer un module JavaScript ou une librairie

Pour utiliser des fonctions ou des modules JS :

```js
import { maFonction } from "./utils.js";
import Markdown from "svelte-exmarkdown";
```

- On peut importer des fonctions, des objets, ou des modules entiers.
- Les librairies installées via npm s'importent par leur nom (ex : `import ... from "svelte-exmarkdown";`).

## Importer une image ou une ressource statique

Pour afficher une image dans un composant Svelte :

```svelte
<img src="/images/logo.png" alt="Logo" />
```

- Placez vos images dans le dossier `public/` (ex : `public/images/logo.png`).
- Le chemin commence toujours par `/` pour pointer vers le dossier public.

## Où placer les fichiers à importer ?

- **CSS/JS spécifiques à un composant** : dans le même dossier que le composant (`src/MonComposant.svelte`, `src/MonComposant.css`)
- **Images et ressources statiques** : dans le dossier `public/`
- **Librairies externes** : installées via npm/yarn, puis importées par leur nom

## Bonnes pratiques

- Toujours vérifier le chemin (relatif ou absolu)
- Respecter la casse (majuscules/minuscules)
- Ne pas oublier l'extension (`.js`, `.css`, etc.) sauf pour les librairies npm
- Utiliser des noms de fichiers explicites

## Erreurs fréquentes

- Mauvais chemin relatif (`../` ou `./` mal placé)
- Fichier non présent dans le dossier attendu
- Oubli de l'extension (`.css`, `.js`)
- Mauvaise casse dans le nom du fichier

## Pour aller plus loin

- [Svelte - Documentation officielle](https://svelte.dev/docs) 