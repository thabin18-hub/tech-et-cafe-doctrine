# Quick Start : Intégration Branding & Routines Cloud

**Date:** 05 août 2026  
**Pour:** Théo  
**Temps estimé:** 15-20 min pour copier-coller les prompts

---

## 0. Situation Actuelle

✅ **Charte graphique finalisée** (05/08 avec Théo)
- Palette hex: cyan `#00D9FF`, orange `#FF9500`, noir `#0A0E27`, blanc `#FFFFFF`
- Guide miniatures strict: zones A/B/C/D, 1280x720, checklist qualité, 3 templates
- Watermark: watermark-shorts.png et watermark-longue.png (150x150, 70% opacité)
- Assets prêts dans `branding/watermark/`

⏸️ **Shorts actuellement disabled** (jusqu'au 07/08)
- Théo produit manuellement en attendant

✅ **Vidéo longue active** (depuis 02/08)
- Continue en public direct

---

## 1. Avant de Commencer

**Checklist pré-lancement :**

- [ ] Accès aux configs routines cloud (Anthropic console)
- [ ] Tokens OAuth vérifiés (YouTube, Drive, Google Cloud TTS) dans .env cloud
- [ ] Accès Drive: dossier `tech-et-cafe/` avec assets + logs
- [ ] Google Cloud project: TTS API activée + clé API valide

---

## 2. Mise à Jour Prompts Routines (Copier-Coller)

**Fichier source:** `PROMPTS-ROUTINES-AVEC-BRANDING.md` (sections numérotées)

### Étape 1: Short #1 (7h GMT)

**Trigger ID:** `trig_01QTPw2RxoroMRcD4E3FthPn`

1. Va dans Anthropic console → Triggers → recherche trigger ID
2. Ouvre "Configuration du prompt"
3. Copie le texte de la section `## 1. PROMPT - Short #1 Quotidien` entièrement
4. Remplace le prompt existant
5. Sauve et valide

**Important:** Vérifier que le prompt contient:
- ✅ Référence GUIDE-MINIATURES.md (ligne "Lire GUIDE-MINIATURES.md complètement")
- ✅ Palette hex exacte (CYAN = #00D9FF, etc.)
- ✅ Variables locales en fin (oauth_token_youtube, etc.)

### Étape 2: Short #2 (10h GMT)

**Trigger ID:** `trig_01NXB2L6FyhAcC381Hg3RpRX`

Idem étape 1, section `## 2. PROMPT - Short #2 Quotidien`

**Attention:** Code anti-doublon entre short #1 et #2 (serait déjà inclus dans le prompt)

### Étape 3: Vidéo Longue (18h GMT)

**Trigger ID:** `trig_0147QDfn9iM9tgPJGYZySEnL`

Idem étape 1-2, section `## 3. PROMPT - Vidéo Longue Quotidienne`

**Note:** Utilise watermark-longue.png au lieu de watermark-shorts.png

### Étape 4 & 5: Autres Routines (Optionnel)

Si tu veux aussi mettre à jour:
- Suivi perf quotidien (sec 4) — probablement pas besoin (lecture seule)
- Réunion strat hebdo (sec 5) — utile si tu veux affiner directives (avancé)

---

## 3. Réactivation Shorts (07/08 avant 7h GMT)

**TODO dans PRODUCTION-CONFIG.yaml:**
```yaml
todo_reactivation_shorts:
  date_cible: "2026-08-07"
  triggers_a_reactiver:
    - "trig_01QTPw2RxoroMRcD4E3FthPn"  # Short #1
    - "trig_01NXB2L6FyhAcC381Hg3RpRX"  # Short #2
  fait: false  ← Changer à true une fois fait
```

**Avant le 07/08 à 6:50h GMT:**
1. Ouvre Anthropic console
2. Trigger #1: change `enabled: true`
3. Trigger #2: change `enabled: true`
4. Valide les deux
5. ✅ À 7h GMT, le premier run de short #1 se lance

---

## 4. Premier Test (19:00 GMT 05/08 Vidéo Longue)

Prochaine vidéo longue produite à 18h GMT environ ce jour.

**À vérifier après publication:**

1. **Miniature colors** — Ouvre YouTube Studio, regarde la thumbnail
   - [ ] Cyan visible? (`#00D9FF` ou proche)
   - [ ] Orange présent? (`#FF9500`)
   - [ ] Watermark discret bas-droit?
   - [ ] Titre lisible sur mobile (432x243px)?

2. **Dimensions** — Screenshot miniature, check EXIF / properties
   - [ ] 1280x720 px?
   - [ ] <500 KB?

3. **Logs** — Regarde Drive `logs/longue-YYYY-MM-DD.json`
   - [ ] Score global visible?
   - [ ] Score SEO visible?
   - [ ] Score miniature visible (nouveau)?
   - [ ] Tous ≥90 (ou ≥85 pour SEO)?

4. **YouTube perf** — Attends 24h, regarde impressions
   - [ ] Video se montre (>0 impressions)?
   - [ ] CTR raisonnable (2-5% acceptable pour premiers 24h)?

---

## 5. Suivi 2 Semaines (05-19 Août)

**Collecte data:**
- [ ] CTR par template miniature (Impact Direct vs Curiosité vs Minimaliste)
- [ ] Domaines couleur: cyan-dominant vs orange-dominant — lequel performe mieux?
- [ ] Rétention moyenne
- [ ] Abonnés nouveaux

**Stockage:**
- BASE-DE-CONNAISSANCES.md (feed auto routine 20h GMT)
- directives-production-2026-08-12.yaml (réunion lundi 9h)

**Révision 19/08:**
- Mettre à jour GUIDE-MINIATURES.md Section 11 "Évolution & Versioning"
- Noter changements / ajustements palette si data demande

---

## 6. Fichiers de Référence (Ordre de Lecture)

**Si besoin approfondir ou debuguer:**

| Document | Utilité | Lecture rapide |
|----------|---------|----------------|
| CHARTE-GRAPHIQUE.md | Palette, typos, éléments visuels | 5 min |
| GUIDE-MINIATURES.md | Template strict + checklist qualité | 10 min |
| GUIDE-DE-PRODUCTION.md | Pipeline 17 étapes (déjà maîtrisé) | — |
| PROMPTS-ROUTINES-AVEC-BRANDING.md | Prompts à copier-coller | 15 min |
| PRODUCTION-CONFIG.yaml | Config globale (déjà up-to-date) | — |
| GUIDE-ANALYSE-PERFORMANCES.md | Checkpoints 24h/48h/7j/30j | — |
| BASE-DE-CONNAISSANCES.md | Knowledge base auto-remplies (suivi) | — |

---

## 7. Troubleshooting Courant

### Problème: Miniature couleurs pas bonnes (cyan/orange pâles)
**Cause probable:** Hex approximé, pas exact (ex: `#00D8FF` au lieu de `#00D9FF`)  
**Fix:** Copier-coller exact depuis CHARTE-GRAPHIQUE.md sec 2, utiliser color picker pour vérifier

### Problème: Titre miniature illisible sur mobile
**Cause:** Police trop petite ou couleur insuffisante contraste  
**Fix:** Augmenter taille (min 48px), utiliser blanc ou cyan, test WCAG AA

### Problème: Watermark trop gros / intrusif
**Cause:** Opacity trop haute ou taille mal resizée  
**Fix:** Vérifier watermark-shorts.png = 150x150, opacité = 70% (#B2 en hex)

### Problème: Score miniature <90 but continue publication
**Cause:** Bug fallback (devrait rejeter ou auto-corriger)  
**Fix:** Vérifier prompt contient "if score <90: auto-revise or reject", pas "publish anyway"

### Problème: API Google Cloud TTS timeout
**Cause:** Quota atteint ou API non activée  
**Fix:** Vérifier facturation Google Cloud, quota TTS, clé API restreinte à TTS seulement

---

## 8. Fréquence de Révision Docs

**Mettre à jour:**
- [ ] Après chaque semaine de production (lundi): BASE-DE-CONNAISSANCES.md
- [ ] Après 2 semaines (19/08): GUIDE-MINIATURES.md v1.1 (ajustements palette/layout)
- [ ] Après 1 mois (05/09): révision complète pipeline qualité
- [ ] Si anomalie production: SOP10 dans BASE-DE-CONNAISSANCES.md + corrigez processus

---

## 9. Contact / Questions

Si bug ou incertitude:
1. Consulte TROUBLESHOOTING ci-dessus (sec 7)
2. Revérifier hex exactes vs CHARTE-GRAPHIQUE.md sec 2
3. Consulte logs JSON dernière production: `logs/longue-YYYY-MM-DD.json` ou `logs/short1-YYYY-MM-DD.json`
4. Escalade: contact Claude pour debug détaillé

---

**Version:** 1.0 (05/08/2026)  
**Prochaine révision:** 19/08/2026  
**Responsable:** Théo (implémentation), Claude (support + révisions)
