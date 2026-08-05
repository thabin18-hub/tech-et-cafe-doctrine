# Guide Génération Miniatures Automatiques

**Pour la Routine Claude Cloud**  
Version 1.0 | 05 août 2026

---

## 1. Contraintes Techniques (Hard Requirements)

### Dimensions
- **Format :** 1280 x 720 px (16:9, standard YouTube)
- **Safe Zone :** 1200 x 680 px (respecter 40px margin tous côtés pour YouTube UI)
- **Mobile Preview :** Miniature testée à 432x243 px (ce que 95% des users voient)

### Format Fichier & Export
- **Format :** PNG ou JPG
- **Compression :** Optimisé (<500 KB, acceptable sur YouTube)
- **Couleur :** sRGB (pas d'espace couleur exotique)

---

## 2. Palette de Couleurs (Hex Code Exact)

```
PRIMARY_CYAN = "#00D9FF"
PRIMARY_ORANGE = "#FF9500"
BG_BLACK = "#0A0E27"
TEXT_WHITE = "#FFFFFF"
TEXT_GRAY = "#4A5568"
ACCENT_DARK_CYAN = "#0099CC"
ACCENT_DARK_ORANGE = "#CC7700"
LIGHT_GRAY = "#E2E8F0"
```

**Usage :**
- Fonds : `BG_BLACK` ou dégradé vers `ACCENT_DARK_CYAN`
- Texte principal : `TEXT_WHITE` (haute visibilité)
- Texte accroche : `PRIMARY_CYAN` (tech, moderne)
- Callouts / sous-titres : `PRIMARY_ORANGE` sur `LIGHT_GRAY` ou blanc
- Shadows/glows : `PRIMARY_CYAN` subtle

---

## 3. Zones de Composition (Template Standard)

```
┌─────────────────────────────────────────────────────────┐
│                    MINIATURE 1280x720                    │
├─────────────────────────────────────────────────────────┤
│                                                           │
│  ┌──────────────────────────────────────────────────┐   │
│  │  ZONE A : TITRE PRINCIPAL (35-40% hauteur)      │   │
│  │  • Blanc gros (72-96px) ou Cyan (60-84px)       │   │
│  │  • Max 2-3 mots, lisible à 432x243px            │   │
│  │  • Centré horizontal, top 20px                   │   │
│  └──────────────────────────────────────────────────┘   │
│                                                           │
│  ┌──────────────────────────────────────────────────┐   │
│  │  ZONE B : ÉLÉMENT VISUEL (20-30% hauteur)       │   │
│  │  • Image/vidéo pertinente (crop smart)          │   │
│  │  • Filtre/effet optionnel (glow cyan subtle)    │   │
│  │  • Centré au milieu vertical                    │   │
│  └──────────────────────────────────────────────────┘   │
│                                                           │
│  ┌──────────────────────────────────────────────────┐   │
│  │  ZONE C : ACCROCHE / CALLOUT (20-25% hauteur)   │   │
│  │  • Orange texte sur box blanc/transparent       │   │
│  │  • Petite police (28-36px), gras                │   │
│  │  • Bottom 60px du cadre                          │   │
│  └──────────────────────────────────────────────────┘   │
│                                                           │
│                            🟦 LOGO WATERMARK             │
│                      (Bas-droit, 80x80 px, 70% opaque)  │
│                                                           │
└─────────────────────────────────────────────────────────┘
```

---

## 4. Détails par Zone

### Zone A : Titre Principal

**Police :**
- Montserrat Black ou Inter Bold
- Poids : 700-900
- Taille : 72-96px (mini 48px si texte long)
- Cas : Majuscules ou Title Case
- Couleur : `TEXT_WHITE` (priorité) ou `PRIMARY_CYAN`

**Règles de Texte :**
- Maximum 3 mots
- Pas de ponctuation sauf !?
- Lisible sans image de fond (utiliser subtle drop shadow si besoin)
- Padding : 20px top, 20px left/right

**Exemples ✅ :**
- "OPENAI LANCE GPT-5"
- "GOOGLE IA RÉVOLUTION"
- "DEEPSEEK CHOQUE TESLA"

**À Éviter ❌ :**
- "L'intelligence artificielle change votre futur"
- "Comment les nouvelles technologies..." (trop long)

---

### Zone B : Élément Visuel

**Source :**
- Récupérer via Drive API (librairie 77 assets existants)
- OU générer via DALL-E/Midjourney si urgent (budget low-cost)
- Dimensions : 400x300 px min, cropper/scale to fit

**Placement :**
- Centré horizontal
- Position vertical : 280-380px (milieu visuel)

**Effets Optionnels :**
- Glow subtle : `box-shadow: 0 0 15px #00D9FF; opacity: 0.8`
- Glitch : appliquer avec parcimonie (1 sur 5 miniatures max)
- Gradient overlay : noir semi-transparent (10-20% opacity) par-dessus l'image

**À Éviter :**
- Blur excessif (rend l'image floue sur mobile)
- Trop d'effets à la fois (overload)

---

### Zone C : Accroche / Callout

**Style :**
- Box arrondie (border-radius: 16px)
- Fond : `LIGHT_GRAY` (#E2E8F0) OU transparent avec border orange 2px
- Texte : `PRIMARY_ORANGE` (#FF9500), gras
- Padding : 12px horizontal, 8px vertical (min)
- Hauteur : 50-70px

**Police :**
- Inter Bold ou Montserrat Medium
- Taille : 28-36px
- Cas : Sentence case ou lowercase
- Ombre texte : subtile (noir 20% opacity)

**Placement :**
- Centré horizontal
- Position : 580-620px top (bas cadre)
- Safe zone : laisser 40px de margin bas

**Exemples ✅ :**
- "Ce que tu dois savoir"
- "4 conseils à retenir"
- "La vérité choquante"

**À Éviter ❌ :**
- Box trop grande (surcharge visuelle)
- Texte blanc sur orange (contraste nul)

---

## 5. Watermark Logo (Branding Discret)

**Assets disponibles :**
- `watermark-shorts.png` (150x150, RGBA transparent) — pour shorts
- `watermark-longue.png` (150x150, RGBA transparent) — pour vidéos longues
- `icon-transparent-bg.png` (260x320) — icon seule si besoin grossir

**Dimensions à utiliser :** 150x150 px (optimisé, visible sans être intrusif)

**Position :** Bas-droit
- X: 1280 - 150 - 20 = 1110 px
- Y: 720 - 150 - 20 = 550 px

**Style :**
- Opacité : 70% (visible mais discret)
- Border : none
- Drop shadow : très subtle (2px blur)

**Variante Alternative :** Logo seul (sans texte) si espace limité

---

## 6. Hiérarchie Visuelle : Poids Oculaire

**Priorité 1 (Regard accroche en <500ms) :**
- Titre blanc gros (Zone A)
- Couleur cyan/orange high-contrast

**Priorité 2 (Maintenir attention <2s) :**
- Élément visuel pertinent (Zone B)
- Callout orange distinctif (Zone C)

**Priorité 3 (Branding, pas distraction) :**
- Watermark discret (coin)

---

## 7. Checklist Auto-Génération Miniature

**Avant publication, la routine DOIT valider :**

- [ ] Dimensions : 1280x720 px exact
- [ ] Couleurs hex exactes utilisées (copy-paste, pas approximation)
- [ ] Titre lisible à 432x243 px (test mobile size)
- [ ] Orange visible et contrastant (WCAG AA min)
- [ ] Watermark présent, discret (70% opacité)
- [ ] Pas de texte blanc sur orange (contraste insuffisant)
- [ ] Image/élément central visible (pas caché par texte)
- [ ] Safe zone respectée (40px margins)
- [ ] Fichier <500 KB
- [ ] Format PNG ou JPG sRGB

**Notation :** Si une case échoue, auto-corriger ou rejeter miniature (score qualité <90 → pas de publication)

---

## 8. Variations Autorisées (3 Templates Prédéfinis)

### Template 1 : "Impact Direct"
```
Titre blanc gros centré
Image dynamique (glow subtle)
Callout orange callout box
Logo watermark
→ Idéal pour : Annonces, découvertes, chocs
```

### Template 2 : "Curiosité"
```
Titre cyan question (ex: "SAIS-TU QUE...")
Image mystérieuse/intrigante
Box orange : "Spoiler : c'est dingue"
Logo watermark
→ Idéal pour : Secrets, révélations, tips
```

### Template 3 : "Minimaliste"
```
Fond dégradé noir → cyan sombre
Titre blanc seul, grand espace blanc
Petit callout orange bas
Logo watermark
→ Idéal pour : Analyses, explications, slow-burn
```

**La routine choisit le template le plus adapté au sujet.**

---

## 9. Gestion des Erreurs

### Cas : Image introuvable / API Drive fail
- **Fallback :** Utiliser background unie (dégradé noir-cyan), agrandir texte
- **Log warning :** Sauvegarder l'erreur pour review manuel

### Cas : Texte trop long / déborde
- **Fallback :** Réduire police (min 48px), réarranger zones
- **Test :** Vérifier lisibilité avant upload

### Cas : Couleur orange insuffisamment visible
- **Fallback :** Augmenter opacité box, ajouter border sombre, tester WCAG
- **Rejet :** Score qualité visuelle <85 → pas de publication

---

## 10. Integration avec Routine Cloud

**Appel API miniature :**

```yaml
miniature_config:
  dimensions:
    width: 1280
    height: 720
  colors:
    primary_cyan: "#00D9FF"
    primary_orange: "#FF9500"
    bg_black: "#0A0E27"
    text_white: "#FFFFFF"
  fonts:
    title: "Montserrat-Black"
    body: "Inter-Regular"
    callout: "Inter-Bold"
  template: "auto"  # auto | impact | curiosity | minimal
  watermark: 
    enabled: true
    position: "bottom-right"
    opacity: 0.70
  quality_threshold: 90  # min score, sinon reject
```

**Output :** `miniature_YYYYMMDD_HHmmss.png` sauvegardée dans Drive + upload YouTube

---

## 11. Métriques & Feedback Loop

**Tracer :**
- CTR par template (impact > curiosity > minimal ?)
- Domaines couleur (cyan-dominant vs orange-dominant ?)
- Durée génération miniature (target: <30s)

**Ajustements :**
- Si CTR cyan >20% mieux que orange → diminuer orange usage
- Si mobile preview illisible → augmenter police
- Mise à jour guide tous les 2 semaines basée sur data

---

## 12. Fichiers Assets Requis

**Stockés dans Google Drive (`tech-et-cafe/assets/`):**

- ✅ Logo watermark (80x80 PNG transparence)
- ✅ Bibliothèque 77 images (catégorisées par sujet)
- ✅ Fonts (Montserrat, Inter disponibles en API Google Fonts)

**Routine accès via Drive API avec token restreint.**

---

## Notes pour le Développeur Routine

1. **Bibliothèque images :** Récupérer via `drive.files().list()`, cache en mémoire
2. **Typage couleur :** Utiliser classe Color(hex_string) pour validation
3. **Fallback aggressif :** Si n'importe quel élément échoue, rejeter plutôt que publier dégradé
4. **Test WCAG :** Intégrer petit checker contraste (lib open-source)
5. **Logging :** JSON log complet chaque miniature (timing, scores, décisions)

---

**Version:** 1.0 (05/08/2026)  
**Prochaine révision :** 19/08/2026 (après 2 semaines de data)
