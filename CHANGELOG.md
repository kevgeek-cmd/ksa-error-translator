# Changelog — KSA Error Translator

Toutes les évolutions notables de ce plugin Antigravity sont consignées dans ce fichier.

---

## [1.0.0] — 2026-10-05

### Initial Release
- **Manifeste Antigravity officiel** (`plugin.json`) conforme au standard des plugins d'agents Antigravity.
- **Skill d'explication** (`explain-errors`) capable d'analyser les erreurs TypeScript, React, Next.js, HTTP, Git, npm et sécurité.
- **Agent Expert Mentor** (`french-error-expert`) adoptant une posture bienveillante, pédagogique et constructive adaptée aux débutants et vibe coders.
- **Règle Antigravity stricte** (`french-error-explanations.md`) imposant :
  - Le principe **EXPLIQUER ≠ MODIFIER** ;
  - Le format d'explication standardisé avec icônes et niveaux ;
  - La préservation rigoureuse des termes techniques originaux ;
  - La recherche de cause racine et le regroupement d'erreurs en cascade.
- **Guides de référence spécialisés** :
  - `http-errors.md` : Vulgarisation des codes d'erreur HTTP courants (400, 401, 403, 404, 429, 500...).
  - `security-warnings.md` : Explication des alertes OWASP (XSS, tokens exposés, noopener, SQLi).
  - `common-framework-errors.md` : Catalogue des erreurs TypeScript, React hydration, Next.js client/server components, Git et npm.
- **Branding & Personnalisation** via `config.json` permettant de modifier l'auteur, le nom du plugin, la signature, la couleur d'accent et le mode d'explication.
