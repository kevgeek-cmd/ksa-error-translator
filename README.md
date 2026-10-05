# KSA Error Translator — French AI Error Assistant

> **"Comprendre les erreurs. Construire sans stress."**  
> *Un assistant IA intégré à Antigravity qui transforme les erreurs techniques de développement en explications simples et compréhensibles en français, particulièrement adaptées aux débutants, aux vibe coders et aux AI Product Builders.*

---

## 💡 Le Problème Résolu

Lorsqu'on débute dans le développement ou qu'on utilise l'IA pour créer des applications (*vibe coding*), les messages d'erreur affichés par le terminal, TypeScript ou Next.js sont souvent intimidants, cryptiques et en anglais technique :

> `Cannot find name 'setState'. Did you mean 'useState'?`  
> `Hydration failed because the server-rendered HTML didn't match the client.`  
> `ERESOLVE unable to resolve dependency tree`

Une traduction mot à mot n'aide pas : ce qu'il faut, c'est **comprendre l'intention de l'ordinateur**, **identifier la cause racine** et savoir **exactement quoi faire**, sans casser son projet.

**KSA Error Translator** agit comme un mentor senior patient qui s'assoit à côté de vous, regarde votre écran et vous explique en français limpide :
1. Ce qui bloque réellement ;
2. Pourquoi cela arrive (avec des analogies du quotidien) ;
3. Les étapes simples pour débloquer la situation, **sans jamais modifier vos fichiers à votre insu**.

---

## ⚡ Principes Fondamentaux

- **EXPLIQUER ≠ MODIFIER** : Par défaut, le plugin explique et oriente. Il n'applique aucune modification de code automatique sans votre validation expresse.
- **ZÉRO TRADUCTION MOT À MOT** : Les concepts sont contextualisés et les identifiants techniques (`useState`, `undefined`, `route.ts`) restent intacts.
- **PRIORITÉ À LA CAUSE RACINE** : Si 8 erreurs surgissent après une modification, le plugin identifie l'erreur mère au lieu de vous noyer sous les symptômes.
- **CLASSIFICATION CLAIRE** :
  - 🔴 **ERROR** : Problème bloquant
  - 🟠 **WARNING** : Avertissement
  - 🔵 **INFO** : Suggestion d'optimisation
  - 🟣 **SECURITY** : Risque de vulnérabilité
  - 🟢 **SUCCESS** : Validation réussie

---

## 📁 Architecture du Plugin

```text
ksa-error-translator/
├── plugin.json                              # Manifeste officiel Antigravity
├── config.json                              # Configuration du branding et des préférences
├── README.md                                # Documentation produit
├── CHANGELOG.md                             # Historique des versions
├── rules/
│   └── french-error-explanations.md         # Règle d'or de restitution
├── agents/
│   └── french-error-expert.md               # Définition du subagent mentor
└── skills/
    └── explain-errors/
        ├── SKILL.md                         # Logique de détection et workflow
        └── references/
            ├── http-errors.md               # Base pédagogique HTTP (400, 401, 404, 500...)
            ├── security-warnings.md         # Répertoire des alertes de sécurité (XSS, noopener...)
            └── common-framework-errors.md   # Catalogue des erreurs TS, React, Next, Git, npm
```

---

## 🚀 Installation

Le plugin est compatible avec les deux modes de déploiement d'Antigravity :

### Option 1 : Déploiement Workspace (Projet Actuel)
Placez le dossier du plugin dans le sous-dossier `.agents/plugins/` de votre projet :
```text
votre-projet/
└── .agents/
    └── plugins/
        └── ksa-error-translator/
```

### Option 2 : Déploiement Global (Disponible sur tous vos projets)
Pour disposer de **KSA Error Translator** sur n'importe quel projet ouvert dans Antigravity :
```bash
# Copier le plugin dans le dossier de configuration global Antigravity
cp -R "/Users/macbook/Desktop/Akwaba chat/.agents/plugins/ksa-error-translator" ~/.gemini/config/plugins/
```

### 🔍 Vérification de la Détection
Antigravity découvre automatiquement les plugins placés dans ces répertoires. Vous pouvez vérifier sa prise en compte dans l'environnement en demandant à l'agent :
> *"Quels sont les plugins actifs ?"* ou en lui soumettant directement une erreur technique.

---

## ⚙️ Personnalisation & Branding

Toute l'identité du plugin est paramétrable dans le fichier `config.json` :

```json
{
  "plugin_name": "KSA Error Translator",
  "display_name": "KSA Error Translator — French AI Error Assistant",
  "author_name": "Stéphane Kevin Assamoi",
  "author_role": "AI Product Builder",
  "signature": "Créé par Stéphane Kevin Assamoi\nAI Product Builder",
  "tagline": "Comprendre les erreurs. Construire sans stress.",
  "language": "fr",
  "explanation_mode": "simple"
}
```

### Les 3 Modes d'Explication disponibles :
1. **`simple`** : Idéal pour les débutants et vibe coders. Utilise des analogies de la vie courante.
2. **`standard`** : Pour les développeurs intermédiaires. Explication technique directe et concise.
3. **`technique`** : Pour les experts voulant une analyse poussée des piles d'appels et des spécifications.

---

## 🛠️ Ajouter de Nouvelles Catégories d'Erreurs

Pour enrichir la base de connaissances du plugin :
1. Créez ou modifiez un fichier Markdown dans `skills/explain-errors/references/` (ex: `docker-errors.md` ou `supabase-errors.md`).
2. Référencez ce guide dans `skills/explain-errors/SKILL.md`.

---

## 👤 Auteur & Crédits

**Créé par Stéphane Kevin Assamoi — AI Product Builder**  
Tagline : *"Comprendre les erreurs. Construire sans stress."*
