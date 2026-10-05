---
name: explain-errors
description: "Traduire et expliquer les erreurs techniques de développement (TypeScript, React, Next.js, HTTP, Git, npm, sécurité) en français simple, accessible et bienveillant pour les débutants, vibe coders et AI Product Builders sans modifier le code automatiquement."
---

# Explain Errors — Skill de Traduction & Vulgarisation Pédagogique

Cette skill transforme les erreurs techniques rébarbatives en explications pédagogiques structurées, rassurantes et exploitables.

Elle s'active automatiquement chaque fois qu'un utilisateur :
- Demande ce qu'une erreur ou un warning signifie ;
- Rencontre une erreur signalée dans l'onglet **Problems**, le **Terminal**, la **Debug Console** ou les **Logs** ;
- Subit un échec de build (`npm run build`, `next build`, `tsc`, `vite build`) ;
- Rencontre un code d'erreur HTTP (400, 401, 403, 404, 429, 500) ;
- Est confronté à une alerte de sécurité ou de linting (Semgrep, ESLint, Trivy, Gitleaks, noopener, XSS).

---

## Directives Fondamentales

### 1. La Règle d'Or : EXPLIQUER ≠ MODIFIER
- Ne jamais modifier automatiquement un fichier source dès qu'une erreur apparaît.
- L'utilisateur doit d'abord **comprendre** ce qui se passe avant d'agir.
- Les propositions de correction doivent être soumises à son approbation.

### 2. Pas de Traduction Littérale
- Ne jamais faire de traduction mot à mot.
- Préserver tous les noms d'identifiants techniques (`useState`, `undefined`, `route.ts`, `npm`).
- Expliquer l'intention sous-jacente du programme.

---

## Démarche Opérationnelle en 5 Étapes

```text
Message brut / Diagnostic
        ↓
1. LOCALISATION & CAPTURE (Fichier, ligne, colonne)
        ↓
2. ANALYSE CONTEXTUELLE (Lecture du code environnant & package.json)
        ↓
3. DÉTECTION DE CAUSE RACINE (Regroupement si cascade d'erreurs)
        ↓
4. STRUCTURATION EN FRANÇAIS (Format officiel KSA)
        ↓
5. RECOMMANDATION & PROPOSITION DE FIX (Sans application forcée)
```

### Étape 1 : Localiser et Capturer
Identifier précisément :
- Le fichier cible concerné ;
- Le numéro de ligne et de colonne si signalés ;
- Le message technique original complet.

### Étape 2 : Analyser le Contexte
Avant d'écrire une réponse, si le workspace est accessible :
- Lire les 10 à 20 lignes autour de l'emplacement du problème ;
- Inspecter les `import` au début du fichier ;
- Vérifier les dépendances majeures dans `package.json` (React, Next.js, TypeScript, Prisma, Tailwind, etc.) ;
- Vérifier si un changement récent dans un autre fichier a pu induire ce blocage.

### Étape 3 : Regrouper et Isoler la Cause Racine
Si 5 à 10 erreurs apparaissent simultanément :
- Identifier si elles découlent toutes d'une seule cause primaire (ex: renommage d'un type partagé, parenthèse manquante, import défaillant).
- Afficher en priorité le **Problème Principal (Cause Racine)**.
- Lister les erreurs secondaires comme conséquences du problème principal.

### Étape 4 : Rédiger la Réponse selon le Format Standard

Appliquer obligatoirement le gabarit :

```markdown
━━━━━━━━━━━━━━━━━━━━
[ICÔNE] [TYPE DE PROBLÈME]

[Titre court et compréhensible en français]

📌 Ce qui se passe :
[Explication contextuelle simple]

💡 En clair :
[Vulgarisation accessible pour débutant ou vibe coder, avec analogie si pertinent]

🔎 Pourquoi :
[Cause probable identifiée]

📍 Où :
[Fichier] — Ligne [X], Colonne [Y]

🛠️ Que faire :
1. [Action de vérification 1]
2. [Action de vérification 2]

🤖 Correction possible :
```[langage]
[Code de correction propre et minimal]
```

⚠️ Attention :
[Avertissement sur les effets secondaires possibles si applicable]

🎯 Niveau :
[🟢 Débutant / 🟡 Intermédiaire / 🔴 Avancé]
━━━━━━━━━━━━━━━━━━━━
Créé par Stéphane Kevin Assamoi
AI Product Builder
```

---

## Typologie & Classification

- 🔴 **ERROR** : Erreur bloquante ou crash nécessitant une intervention.
- 🟠 **WARNING** : Avertissement sur une pratique déconseillée ou un risque de régression future.
- 🔵 **INFO** : Information d'optimisation ou remarque de workflow.
- 🟣 **SECURITY** : Risque de sécurité (exposition de token, XSS, SSRF, injection SQL, noopener).
- 🟢 **SUCCESS** : Problème résolu ou confirmation de bon fonctionnement.

---

## Références Spécialisées Incluses

Pour approfondir l'analyse selon le domaine, consulter les fichiers de référence :
- **Codes HTTP & Réseau** : `references/http-errors.md`
- **Sécurité & Vulnérabilités** : `references/security-warnings.md`
- **Frameworks (TS, React, Next, Git, npm)** : `references/common-framework-errors.md`
