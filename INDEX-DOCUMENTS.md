# Index Documents Tech & Café

**Version 1.0 | 05 août 2026**

Tous les documents du pipeline production, triés par cas d'usage.

---

## 🚀 Je Viens D'Arriver (Premiers Pas)

| Document | Pourquoi | Temps |
|----------|---------|-------|
| **00-QUICK-START-BRANDING.md** | Mise à jour prompts cloud + réactivation shorts | 20 min |
| **CONTEXTE-GLOBAL-TECH-CAFE.md** | Comprendre identité + valeurs + hiérarchie | 10 min |

---

## 🎨 Je Travaille Sur Branding / Miniatures (Nouveau 05/08)

| Document | Contenu | Cas d'usage |
|----------|---------|-----------|
| **CHARTE-GRAPHIQUE.md** | Palette hex, typographies, règles WCAG, éléments visuels | Je dois savoir quelles couleurs utiliser |
| **GUIDE-MINIATURES.md** | Template zones A/B/C/D, 1280x720 specs, checklist 10 items, fallbacks | Je debug une miniature, elle ne match pas |
| **PROMPTS-ROUTINES-AVEC-BRANDING.md** | Tous les prompts cloud + intégration charte | Je dois update un prompt dans le cloud |

---

## 📺 Je Produis (Production Daily)

| Document | Quand consulter | Priorité |
|----------|-----------------|----------|
| **GUIDE-DE-PRODUCTION.md** | Chaque vidéo: respecter pipeline 17 étapes | Haute |
| **GUIDE-SEO-YOUTUBE.md** | Avant upload: optimiser titre/description/tags | Haute |
| **GUIDE-MINIATURES.md** | Avant miniature: zones, palette, checklist | Haute (NEW) |
| **PRODUCTION-CONFIG.yaml** | Directives quotidiennes, seuils qualité, backlog | Moyenne |
| **BASE-DE-CONNAISSANCES.md** | Pour reference: titres/hooks/erreurs précédentes | Moyenne |

---

## 📊 Je Fais L'Analytique (Réunion Hebdo)

| Document | Contenu | Fréquence |
|----------|---------|-----------|
| **GUIDE-ANALYSE-PERFORMANCES.md** | Checkpoints 24h/48h/7j/30j, grille diagnostic | Lundi 9h GMT |
| **BASE-DE-CONNAISSANCES.md** | Feed auto: titres/hooks/miniatures/sujets performants | Mis à jour daily (20h) |
| **directives/directives-production-YYYY-MM-DD.yaml** | Generated lundi 9h: angles privilégier/éviter, cpm, hooks | Consulter avant production |

---

## 🔧 Je Debug / Troubleshoot

**Problème:** Miniature ne matche pas la palette  
→ GUIDE-MINIATURES.md sec 5-6 + CHARTE-GRAPHIQUE.md sec 2

**Problème:** Score qualité <90  
→ GUIDE-DE-PRODUCTION.md sec 3 (gates) + logs JSON

**Problème:** YouTube API fail  
→ PROMPTS-ROUTINES-AVEC-BRANDING.md sec "fallbacks"

**Problème:** Confusion couleurs vs typographies  
→ CHARTE-GRAPHIQUE.md sec 2-3 (palettes + typographies)

**Problème:** Shorts pas lancés à 7h GMT  
→ 00-QUICK-START-BRANDING.md sec 3 (réactivation shorts)

---

## 📋 Tous Les Documents (Liste Complète)

### Doctrine & Identité

| Fichier | Créé | Utilité | Lecture |
|---------|------|---------|---------|
| CONTEXTE-GLOBAL-TECH-CAFE.md | 02/08 | Vision, mission, valeurs, hiérarchie décision (6 niveaux) | Fondamental |
| CHARTE-EDITORIALE.md | 02/08 | Ton, style, sujets autorisés (partiellement copié) | Complémentaire |

### Pipeline Production

| Fichier | Créé | Utilité | Lecture |
|---------|------|---------|---------|
| GUIDE-DE-PRODUCTION.md | 02/08 | Pipeline complet 17 étapes, score qualité ≥90 | Essentiel |
| GUIDE-SEO-YOUTUBE.md | 02/08 | Stratégie SEO, titre/description/tags/chapitres, score ≥85 | Essentiel |
| PROCEDURES-OPERATIONNELLES-SOP.md | 02/08 | SOP 01-12 (routines quotidiennes/hebdo/mensuelles) | Référence |
| GUIDE-ANALYSE-PERFORMANCES.md | 02/08 | Checkpoints analytique (24h/48h/7j/30j), grille diagnostic | Lundi 9h |

### Branding & Visuels (NOUVEAU 05/08)

| Fichier | Créé | Utilité | Lecture |
|---------|------|---------|---------|
| **CHARTE-GRAPHIQUE.md** | 05/08 | Palette hex + typos + accessibility WCAG + éléments visuels | Essentiel |
| **GUIDE-MINIATURES.md** | 05/08 | Template zones A/B/C/D, specs 1280x720, checklist 10 items | Essentiel |
| **PROMPTS-ROUTINES-AVEC-BRANDING.md** | 05/08 | Tous prompts cloud intégrés avec charte graphique | Mise à jour cloud |

### Configuration & Routines

| Fichier | Créé | Utilité | Lecture |
|---------|------|---------|---------|
| PRODUCTION-CONFIG.yaml | 02/08, maj 05/08 | Config centrale: directives, backlog, gates qualité, branding | Référence |
| 00-QUICK-START-BRANDING.md | 05/08 | Steps pour copier prompts + réactiver shorts + tester | Action immédiate |

### Connaissance & Suivi

| Fichier | Créé | Utilité | Lecture |
|---------|------|---------|---------|
| BASE-DE-CONNAISSANCES.md | 02/08 | Mémoire stratégique: titres/hooks/miniatures/erreurs, alimente routines | Auto-fed daily |
| directives-production-YYYY-MM-DD.yaml | Lundi 9h | Generated weekly: angles, cpm, hooks, retention targets | Lundi avant prod |

### Navigation & Planning

| Fichier | Créé | Utilité | Lecture |
|---------|------|---------|---------|
| INDEX-DOCUMENTS.md | 05/08 | Ce fichier: navigation par cas d'usage | Vous êtes ici |
| START-HERE.md | 01/08 | Point entrée initial (peut être obsolète?) | Legacy |

---

## 🎯 Checklist : Quoi Faire Quand

### Avant Chaque Production (Daily)

- [ ] Lire PRODUCTION-CONFIG.yaml (directives du jour si lundi)
- [ ] Consulter BASE-DE-CONNAISSANCES.md (quelle palette/hooks performent?)
- [ ] Produire: GUIDE-DE-PRODUCTION.md (17 étapes)
- [ ] Miniature: GUIDE-MINIATURES.md (zones, palette, checklist)
- [ ] SEO: GUIDE-SEO-YOUTUBE.md (titre, description, tags)

### Après Chaque Production (Daily 20h GMT)

- [ ] Suivi perf: GUIDE-ANALYSE-PERFORMANCES.md (checkpoints)
- [ ] Update: BASE-DE-CONNAISSANCES.md (titres/hooks qui performent, erreurs)

### Lundi 9h GMT (Réunion Stratégique)

- [ ] Analyser semaine précédente avec GUIDE-ANALYSE-PERFORMANCES.md
- [ ] Générer directives-production-2026-MM-DD.yaml (angles, cpm targets)
- [ ] Décider: quoi continuer / arrêter / tester cette semaine

### Tous Les 2 Semaines (19/08, 02/09, etc.)

- [ ] Réviser GUIDE-MINIATURES.md (v1.1): feedback CTR par template?
- [ ] Mettre à jour CHARTE-GRAPHIQUE.md si palette besoin ajustement

---

## 🔀 Dépendances Entre Documents

```
CONTEXTE-GLOBAL (identité, hiérarchie)
    ↓
├─ CHARTE-GRAPHIQUE (palette, typos)
│   └─ GUIDE-MINIATURES (template + specs + checklist)
│       └─ PROMPTS-ROUTINES-AVEC-BRANDING (copier-coller cloud)
│
├─ GUIDE-DE-PRODUCTION (17 étapes)
│   └─ GUIDE-SEO-YOUTUBE (score ≥85)
│       └─ PROCEDURES-OPERATIONNELLES (SOP 01-12)
│
├─ GUIDE-ANALYSE-PERFORMANCES (checkpoints)
│   └─ BASE-DE-CONNAISSANCES (feedback loop)
│
└─ PRODUCTION-CONFIG (directives quotidiennes)
    └─ directives-production-YYYY-MM-DD.yaml (lundi 9h)
```

---

## 📈 Évolution Documents (Versioning)

### v1.0 (27/07 - 04/08)
- Pipeline production établi
- Doctrine qualité + analytique en place
- SOP 01-12 documentées

### v1.1 (05/08) — AUJOURD'HUI 🎨
- ✅ CHARTE-GRAPHIQUE.md créée
- ✅ GUIDE-MINIATURES.md créée
- ✅ PROMPTS-ROUTINES-AVEC-BRANDING.md créée
- ✅ 00-QUICK-START-BRANDING.md créée
- ✅ PRODUCTION-CONFIG.yaml maj v5.1 (section branding)
- ✅ INDEX-DOCUMENTS.md créé (ce fichier)

### v1.2 (19/08 prévue)
- GUIDE-MINIATURES.md v1.1: ajustements basés CTR data 2 semaines
- CHARTE-GRAPHIQUE.md v1.1: palette refinements si needed
- BASE-DE-CONNAISSANCES.md: enrichissements patterns

### v2.0 (05/09 prévue)
- Révision complète: pipeline, qualité, branding, analytics
- Longs formats vs shorts: ratio optimal?
- A/B testing miniatures: activation?

---

## 💡 Pro Tips

**Bookmark shortcuts:**
- Production daily? Marque GUIDE-DE-PRODUCTION.md
- Debug miniature? Marque GUIDE-MINIATURES.md
- Analytique lundi? Marque BASE-DE-CONNAISSANCES.md + directives

**Workflow optimisé:**
1. Lundi matin: lire directives + BASE-DE-CONNAISSANCES
2. Daily 7h-18h: GUIDE-DE-PRODUCTION + GUIDE-MINIATURES + GUIDE-SEO
3. Lundi 9h: GUIDE-ANALYSE-PERFORMANCES

**Avant modifier un document:**
- Checke CONTEXTE-GLOBAL (hiérarchie décision valide change?)
- Notifie Théo si révision majeure (palette, process, gates)

---

**Responsable:** Claude (maintenance) + Théo (validation)  
**Dernière maj:** 05/08/2026  
**Prochaine révision:** 19/08/2026
