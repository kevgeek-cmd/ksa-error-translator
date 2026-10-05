# Répertoire des Alertes & Vulnérabilités de Sécurité (🟣 SECURITY)

Ce guide de référence détaille les patterns de vulnérabilités fréquents rencontrés par les développeurs et les vibe coders, avec une explication claire du risque et de la remédiation.

---

### 1. `window.open('_blank')` ou `<a target="_blank">` sans `rel="noopener noreferrer"`

- 🟣 **Problème de sécurité :** Tabnabbing inverse (Reverse Tabnabbing).
- 📌 **Ce qui se passe :** La page cible ouverte dans un nouvel onglet obtient un accès partiel à l'objet `window.opener` de la page d'origine.
- 💡 **En clair :** "Quand tu ouvres une porte vers un site externe sans fermer le verrou derrière toi, ce site externe peut tenter de rediriger discrètement ta page d'origine vers une fausse page de connexion (phishing)."
- 🔎 **Pourquoi c'est important :** Un attaquant contrôlant la page externe peut manipuler l'utilisateur en lui faisant croire que sa session a expiré sur le site légitime.
- 🛠️ **Recommandation :**
  - Ajouter systématiquement `rel="noopener noreferrer"` sur les balises `<a>`.
  - En JavaScript : `window.open(url, '_blank', 'noopener,noreferrer')`.
- 🎯 **Niveau :** 🟡 Intermédiaire

---

### 2. Clé Secrète ou Token Exposé Côté Client (`NEXT_PUBLIC_...` ou durci dans le code)

- 🟣 **Problème de sécurité :** Fuite de secret d'authentification ou d'administration.
- 📌 **Ce qui se passe :** Une clé privée (ex: `STRIPE_SECRET_KEY`, `SUPABASE_SERVICE_ROLE_KEY`, `DATABASE_URL`) est injectée dans le code JavaScript envoyé au navigateur.
- 💡 **En clair :** "C'est comme coller le mot de passe de ton coffre-fort sur la vitrine du magasin : n'importe qui ouvrant l'inspecteur du navigateur peut le copier."
- 🔎 **Pourquoi c'est critique :** Toute personne inspectant les requêtes réseau ou les fichiers JS compilés peut vider la base de données ou consommer tes crédits.
- 🛠️ **Recommandation :**
  1. Ne jamais préfixer une clé secrète par `NEXT_PUBLIC_` ou `VITE_`.
  2. Utiliser uniquement ces clés dans des routes API sécurisées côté serveur (`src/app/api/...`).
  3. Révoquer immédiatement la clé sur le tableau de bord du fournisseur si elle a été poussée sur Git.
- 🎯 **Niveau :** 🔴 Avancé / Critique

---

### 3. Injection XSS via `dangerouslySetInnerHTML`

- 🟣 **Problème de sécurité :** Cross-Site Scripting (XSS).
- 📌 **Ce qui se passe :** Du code HTML fourni par un utilisateur ou une API externe est injecté directement dans le DOM sans nettoyage préalable.
- 💡 **En clair :** "Si quelqu'un écrit un commentaire contenant un script malveillant `<script>...</script>`, ce script s'exécute chez tous les autres utilisateurs qui lisent le commentaire."
- 🔎 **Pourquoi c'est critique :** Vol de cookies de session, usurpation d'identité, actions non autorisées au nom de la victime.
- 🛠️ **Recommandation :**
  - Éviter `dangerouslySetInnerHTML`.
  - Si l'injection HTML est indispensable, utiliser une bibliothèque de désinfection éprouvée comme `DOMPurify` ou `sanitize-html`.
- 🎯 **Niveau :** 🟡 Intermédiaire

---

### 4. Injection SQL / Requêtes Brutes Non Paramétrées

- 🟣 **Problème de sécurité :** SQL Injection (SQLi).
- 📌 **Ce qui se passe :** Concaténation directe d'une variable utilisateur dans une chaîne SQL (`SELECT * FROM users WHERE email = '` + email + `'`).
- 💡 **En clair :** "Si un utilisateur tape `' OR 1=1 --` dans le champ email, la base de données lui donne accès à tous les comptes sans vérifier le mot de passe."
- 🛠️ **Recommandation :**
  - Utiliser toujours les requêtes préparées ou un ORM moderne (Prisma, Drizzle) qui paramètre automatiquement les variables.
- 🎯 **Niveau :** 🔴 Avancé
