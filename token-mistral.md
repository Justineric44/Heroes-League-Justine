# 🚀 Récupérer un Token d'API Mistral AI

Voici comment récupérer ton token d'authentification ! 🔑

## 🔹 Étapes

1. **Accède à la console Mistral AI** 🌍
   - Rends-toi sur la console Mistral AI à l'adresse suivante : [https://console.mistral.ai/](https://console.mistral.ai/).

2. **Crée un compte et/ou connecte-toi** 🔐

3. **Génère un token d'API** 🎟️
   - Une fois connecté(e), accède à la section "API Keys" ou "Clés API".
   - Clique sur "Créer une nouvelle clé" _(ou similaire)_.
   - Copie et sauvegarde ton token en lieu sûr. 🛡️

##  Exemple équivalent en JavaScript (fetch)

L'exemple `curl` ci-dessus devient en JavaScript :

```js
fetch("https://api.mistral.ai/v1/endpoint", {
  method: "GET",
  headers: {
    "Authorization": "Bearer TON_TOKEN"
  }
})
  .then(response => response.json())
  .then(data => {
    console.log(data);
  });
```

**Explications :**
- L'option `-H "Authorization: Bearer TON_TOKEN"` de curl correspond à l'objet `headers` dans fetch.
- Le verbe `-X GET` de curl devient `method: "GET"` dans fetch (optionnel car GET est la valeur par défaut).
- L'URL est la même.
- On remplace `TON_TOKEN` par la clé obtenue.

## ⚠️ Sécurité

- 🔒 **Ne partage jamais ton token !**
- 📂 **Stocke-le dans un gestionnaire de secrets ou une variable d'environnement.**
- 🔄 **Renouvelle-le régulièrement si nécessaire.**

---
🎉 Voilà, tu es prêt(e) à utiliser l'API Mistral AI ! Amuse-toi bien ! 🚀
