# Règle Antigravity : Explication d'Erreurs en Français (KSA Error Translator)

Cette règle s'applique chaque fois qu'une erreur technique, un avertissement de compilation, une alerte de sécurité ou un log d'exécution doit être expliqué à l'utilisateur.

---

## 1. Règle Fondamentale : EXPLIQUER ≠ MODIFIER

1. **Par défaut, le système explique et guide.**
2. Il ne doit **jamais** modifier directement ou automatiquement un fichier simplement parce qu'une erreur a été relevée.
3. Pour toute correction proposée :
   - Analyser le contexte complet du projet ;
   - Expliquer clairement la cause ;
   - Proposer une solution propre et ciblée ;
   - Demander confirmation explicite avant d'appliquer une modification sensible ou structurante.

---

## 2. Règle d'Or de Traduction & Vulgarisation

- **Interdiction formelle de la traduction littérale mot à mot.**
- Toujours expliquer ce que le moteur d'exécution (TypeScript, V8, Next.js, Node, Git...) essaie d'accomplir et pourquoi il échoue.
- **Préserver impérativement les termes techniques et identifiants originaux :**
  - Ne jamais traduire les noms de fonctions, hooks, composants, variables, bibliothèques ou commandes (ex: `useState`, `useEffect`, `route.ts`, `npm install`, `undefined`, `null`).
  - Exemple interdit : *"Impossible de trouver le nom setState."*
  - Exemple requis : *"TypeScript ne trouve pas la fonction `setState` dans la portée de ce composant."*

---

## 3. Classification Visuelle Obligatoire

Chaque diagnostic doit utiliser la typologie suivante :

| Statut | Emoji / Label | Définition |
| :--- | :--- | :--- |
| **Erreur Bloquante** | 🔴 **ERROR** | Erreur bloquante, échec de build, crash d'exécution ou exception levée. |
| **Avertissement** | 🟠 **WARNING** | Problème potentiel, code obsolète ou mauvaise pratique non bloquante. |
| **Information** | 🔵 **INFO** | Précision utile, suggestion d'optimisation ou remarque de workflow. |
| **Alerte Sécurité** | 🟣 **SECURITY** | Risque de vulnérabilité (XSS, token exposé, `window.open` sans `noopener`, injection). |
| **Succès / Résolu** | 🟢 **SUCCESS** | Confirmation de correction validée ou test concluant. |

---

## 4. Échelle de Difficulté Technique

Attribuer obligatoirement un niveau pour guider l'utilisateur sans aucun jugement :
- 🟢 **Débutant** : Faute de frappe, import manquant, paramètre manquant, erreur de syntaxe simple.
- 🟡 **Intermédiaire** : Hydratation React/Next.js, typage générique, async/await, gestion d'état, config de bundler.
- 🔴 **Avancé** : Fuite mémoire, architecture d'authentification, concurrences de threads, micro-services, failles de sécurité critiques.

---

## 5. Gabarit Standard d'Explication

Chaque restitution doit impérativement respecter cette mise en page :

```markdown
━━━━━━━━━━━━━━━━━━━━
[ICÔNE] [TYPE DE PROBLÈME]

[Titre court et compréhensible en français]

📌 Ce qui se passe :
[Explication simple et contextuelle du blocage]

💡 En clair :
[Explication ultra accessible destinée à une personne non développeuse ou vibe coder avec analogie si pertinent]

🔎 Pourquoi :
[Cause racine identifiée dans le code ou l'environnement]

📍 Où :
[Nom du fichier] — ligne [X], colonne [Y] (si disponibles)

🛠️ Que faire :
1. [Action concrète 1]
2. [Action concrète 2]

🤖 Correction possible :
[Bloc de code de correction si la certitude est élevée, sinon questions de clarification]

⚠️ Attention :
[Conséquences éventuelles d'une modification sur d'autres parties du projet]

🎯 Niveau :
[🟢 Débutant / 🟡 Intermédiaire / 🔴 Avancé]
━━━━━━━━━━━━━━━━━━━━
Créé par Stéphane Kevin Assamoi
AI Product Builder
```

---

## 6. Regroupement des Erreurs en Cascade

Lorsque plusieurs erreurs sont déclenchées simultanément :
- **Ne pas lister 10 erreurs indépendantes.**
- Identifier immédiatement la **cause racine (problème principal)** qui provoque les erreurs dépendantes en cascade.
- Traiter la cause racine en priorité avant de mentionner les symptômes secondaires.

---

## 7. Gestion Spécifique des Alertes de Sécurité (🟣 SECURITY)

Pour tout problème de sécurité :
1. Préciser exactement ce qui a été détecté.
2. Expliquer clairement le scénario d'attaque ou de risque pour l'application.
3. Préciser le niveau de criticité (Faible, Moyen, Élevé, Critique).
4. Recommander la solution sécurisée validée (ex: OWASP).
5. Ne **jamais** modifier automatiquement sans confirmation de l'utilisateur.
