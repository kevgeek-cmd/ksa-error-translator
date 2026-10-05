# Répertoire des Erreurs Courantes par Framework & Écosystème

Ce guide de référence recense les erreurs les plus fréquemment rencontrées dans les projets modernes (TypeScript, React, Next.js, Prisma, Git, npm).

---

## 1. TypeScript

### `Cannot find name 'X'. Did you mean 'Y'?`
- 📌 **Ce qui se passe :** TypeScript rencontre un identifiant `X` qui n'a été ni importé ni déclaré dans ce fichier.
- 💡 **En clair :** "Le programme cherche un mot ou un outil qui ne figure pas dans le dictionnaire de cette page."
- 🔎 **Causes :** Oubli d'import (`import { useState } from 'react'`), faute de frappe dans le nom, ou variable supprimée.
- 🛠️ **Que vérifier :** La présence de l'import en haut du fichier et l'orthographe exacte.

### `Object is possibly 'undefined' / 'null'`
- 📌 **Ce qui se passe :** Tu essaies d'accéder à une propriété (ex: `user.name`), mais TypeScript remarque que `user` peut valoir `undefined` (par exemple si les données sont encore en cours de chargement).
- 💡 **En clair :** "Tu essaies d'ouvrir une boîte qui n'est peut-être pas encore livrée."
- 🛠️ **Que vérifier :** Utiliser l'opérateur de chaînage optionnel `user?.name` ou vérifier au préalable `if (!user) return ...`.

### `Type 'A' is not assignable to type 'B'`
- 📌 **Ce qui se passe :** Tu essaies d'assigner une valeur d'un type incompatible avec ce que le composant ou la fonction attend (ex: passer une chaîne de caractères au lieu d'un nombre).
- 💡 **En clair :** "Tu essaies de brancher une prise carrée dans une prise ronde."

---

## 2. React & Next.js

### `Hydration failed because the server-rendered HTML didn't match the client`
- 📌 **Ce qui se passe :** Next.js a généré le HTML côté serveur, mais lors de l'exécution sur le navigateur du client, le rendu est différent.
- 💡 **En clair :** "Le serveur a préparé un plat, mais le navigateur a reçu un ingrédient différent au moment de dresser l'assiette."
- 🔎 **Causes :** Utilisation directe de `Date.now()`, `Math.random()`, `window.innerWidth`, ou d'extensions de navigateur modifiant le DOM (adblockers, traducteurs) avant l'hydratation.
- 🛠️ **Que vérifier :** Isoler le code dépendant du navigateur dans un `useEffect`, ou ajouter `suppressHydrationWarning` si la divergence est inoffensive et maîtrisée.

### `You're importing a component that needs useState. It only works in a Client Component...`
- 📌 **Ce qui se passe :** Un composant Next.js Server Component essaie d'utiliser des fonctionnalités interactives (hooks d'état, gestionnaires de clics).
- 💡 **En clair :** "Tu demandes au serveur d'écouter les clics de souris, or le serveur n'a pas d'écran ni de souris."
- 🛠️ **Que vérifier :** Ajouter `'use client';` tout en haut du fichier du composant concerné.

### `Too many re-renders. React limits the number of renders to prevent an infinite loop`
- 📌 **Ce qui se passe :** Un composant met à jour son état à chaque rendu sans condition d'arrêt, provoquant une boucle sans fin.
- 💡 **En clair :** "Le composant tourne en rond et s'actualise sans jamais s'arrêter."
- 🔎 **Causes :** Appel direct de fonction dans un gestionnaire d'événement : `onClick={handleClick()}` au lieu de `onClick={() => handleClick()}` ou mise à jour du state directement dans le corps de la fonction composant sans `useEffect`.

---

## 3. Git & Ligne de Commande

### `error: failed to push some refs to '...'`
- 📌 **Ce qui se passe :** Le dépôt distant (GitHub) contient des commits que ta machine locale ne possède pas encore.
- 💡 **En clair :** "Quelqu'un a ajouté des pages au livre sur GitHub pendant que tu écrivais les tiennes en local."
- 🛠️ **Que vérifier :** Effectuer d'abord un `git pull --rebase` ou `git pull` avant de pousser à nouveau avec `git push`.

---

## 4. Gestionnaires de Paquets (npm / pnpm / yarn)

### `ERESOLVE unable to resolve dependency tree`
- 📌 **Ce qui se passe :** Deux dépendances de ton projet exigent des versions différentes et incompatibles d'un même sous-paquet.
- 💡 **En clair :** "Deux outils installés se disputent la même pièce de rechange avec des tailles différentes."
- 🛠️ **Que vérifier :** Mettre à jour les dépendances obsolètes ou utiliser la section `overrides` dans `package.json`.
