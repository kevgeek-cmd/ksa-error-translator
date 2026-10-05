# Répertoire Pédagogique des Codes d'Erreur HTTP & API

Ce guide de référence permet au traducteur d'erreurs d'expliquer les statuts HTTP courants avec clarté et bienveillance, sans jargon obscur.

---

### 400 — Bad Request (Mauvaise Requête)
- 📌 **Ce qui se passe :** Le serveur n'a pas compris ce que le client lui a envoyé.
- 💡 **En clair :** "C'est comme envoyer un formulaire avec des champs remplis dans le désordre ou incomplets."
- 🔎 **Causes courantes :** Corps JSON mal formaté (`JSON.parse` échoue), paramètre obligatoire manquant, type de données erroné (texte envoyé au lieu d'un nombre).
- 🛠️ **Que vérifier :** Le contenu de `body` dans l'appel `fetch` / `axios` et les logs du serveur.

---

### 401 — Unauthorized (Non Authentifié)
- 📌 **Ce qui se passe :** Le serveur exige de savoir qui fait la demande avant de répondre.
- 💡 **En clair :** "Tu te présentes à une porte fermée sans ta carte d'accès ou ton badge."
- 🔎 **Causes courantes :** Token JWT absent dans les en-têtes `Authorization`, clé API non configurée dans le fichier `.env`, token expiré.
- 🛠️ **Que vérifier :** La présence de l'en-tête `Authorization: Bearer <token>` et la validité de la variable d'environnement associée.

---

### 403 — Forbidden (Accès Refusé)
- 📌 **Ce qui se passe :** Le serveur sait qui tu es, mais tu n'as pas le droit d'effectuer cette action.
- 💡 **En clair :** "Tu as ton badge pour entrer dans le bâtiment, mais pas la permission d'entrer dans la salle des serveurs."
- 🔎 **Causes courantes :** Rôle utilisateur insuffisant (ex: utilisateur standard tentant une action admin), politique RLS (Row Level Security) sur Supabase / PostgreSQL bloquant la ligne.
- 🛠️ **Que vérifier :** Les permissions de l'utilisateur connecté et les règles d'autorisation côté backend / base de données.

---

### 404 — Not Found (Non Trouvé)
- 📌 **Ce qui se passe :** La ressource, la page ou la route demandée n'existe pas sur le serveur.
- 💡 **En clair :** "Tu envoies une lettre à une adresse qui ne figure pas sur le plan de la ville."
- 🔎 **Causes courantes :** Faute de frappe dans l'URL (`/api/chatt` au lieu de `/api/chat`), route Next.js mal nommée, ressource supprimée en base de données.
- 🛠️ **Que vérifier :** L'URL exacte appelée, la structure des dossiers dans `app/api/...` ou `pages/api/...`.

---

### 429 — Too Many Requests (Trop de Requêtes / Rate Limit)
- 📌 **Ce qui se passe :** Trop de demandes ont été envoyées dans un court intervalle de temps.
- 💡 **En clair :** "Le serveur est submergé et demande de marquer une pause avant de réessayer."
- 🔎 **Causes courantes :** Boucle infinie dans un `useEffect` déclenchant des fetch en rafale, quota d'API externe dépassé (OpenAI, Gemini, Resend).
- 🛠️ **Que vérifier :** Les dépendances du `useEffect` ou l'état de consommation du quota auprès du fournisseur d'API.

---

### 500 — Internal Server Error (Erreur Interne du Serveur)
- 📌 **Ce qui se passe :** Le serveur a rencontré un problème imprévu qui l'a fait crasher pendant le traitement de la demande.
- 💡 **En clair :** "Le serveur a trébuché et s'est arrêté net pendant qu'il préparait ta réponse."
- 🔎 **Causes courantes :** Exception non gérée (`undefined is not an object`), échec de connexion à la base de données, clé d'environnement absente sur le serveur.
- 🛠️ **Que vérifier :** Les logs du terminal backend (`npm run dev` ou logs Vercel / Docker).

---

### 502 / 503 / 504 — Bad Gateway / Service Unavailable / Gateway Timeout
- 📌 **Ce qui se passe :** Le serveur intermédiaire ou passerelle n'arrive pas à joindre le service final dans le délai imparti.
- 💡 **En clair :** "L'intermédiaire attend une réponse qui n'arrive jamais car le service cible est éteint ou trop lent."
- 🔎 **Causes courantes :** Serveur backend non démarré, migration longue en cours, réseau inaccessible.
