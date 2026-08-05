# Charte Graphique Tech & Café

Version 1.0 | 05 août 2026

---

## 1. Identité Visuelle

**Nom :** Tech & Café  
**Tagline :** Le média francophone de référence sur l'intelligence artificielle  
**Style :** Néon cyberpunk moderne + humanité café  
**Ton :** Tech-forward, accessible, honnête

---

## 2. Palette de Couleurs

### Couleurs Primaires

| Couleur | Hex | RGB | Usage |
|---------|-----|-----|-------|
| **Cyan Néon** | `#00D9FF` | 0, 217, 255 | Texte principal, accents tech, éléments clés, borders |
| **Orange Chaud** | `#FF9500` | 255, 149, 0 | Sous-titres, callouts, points importants, humanité |
| **Noir Profond** | `#0A0E27` | 10, 14, 39 | Fond principal, text dark mode |
| **Blanc** | `#FFFFFF` | 255, 255, 255 | Texte sur fonds foncés, contraste maximum |

### Couleurs Secondaires

| Couleur | Hex | RGB | Usage |
|---------|-----|-----|-------|
| **Gris Neutre** | `#4A5568` | 74, 85, 104 | Texte secondaire, séparateurs discrets |
| **Gris Clair** | `#E2E8F0` | 226, 232, 240 | Surfaces légères, overlays transparents |
| **Cyan Sombre** | `#0099CC` | 0, 153, 204 | Hover states, inactive states |
| **Orange Sombre** | `#CC7700` | 204, 119, 0 | Emphasis on dark backgrounds |

---

## 3. Typographies

### Police Recommandée

**Titres (Bold, Accents) :**
- **Nom :** Inter Black ou Montserrat Bold
- **Poids :** 700-900
- **Cas :** Majuscules ou Title Case
- **Taille miniature :** 24-32px (écran mobile)

**Corps (Lisibilité) :**
- **Nom :** Inter Regular ou Open Sans
- **Poids :** 400-500
- **Taille miniature :** 14-18px
- **Interligne :** 1.4x min

**Accents (Sous-titres, Tags) :**
- **Nom :** Inter Medium
- **Poids :** 600
- **Cas :** Sentence case ou lowercase
- **Taille :** 12-16px

---

## 4. Éléments Visuels Récurrents

### Logo Principal
- **Variante :** Tasse stylisée néon cyan + vapeur montante
- **Dimensions :** Carré 1:1 (photo de profil YouTube)
- **Variantes :**
  - Logo plein (cyan sur transparent)
  - Logo inversé (blanc sur transparent)
  - Logo compact (vapeur seule pour watermark)

### Watermark (Coins vidéo)
- **Position :** Bas-droit ou bas-gauche
- **Taille :** 5-10% de la largeur vidéo
- **Style :** Tasse vapeur en cyan + texte "Tech & Café" petit
- **Opacité :** 70-80% (lisible mais discret)

### Séparateurs & Dividers
- **Style :** Ligne fine cyan (`#00D9FF`) ou orange (`#FF9500`)
- **Épaisseur :** 2-3px
- **Animations :** Fade-in/glitch effect facultatif (mais cohérent)

### Badges (Tags, Labels)
- **Style :** Pilule arrondie (border-radius 20px)
- **Fond :** Transparent ou cyan léger (10% opacity)
- **Border :** Cyan 1px
- **Texte :** Cyan, petite police (12px)
- **Exemple :** #IA #Tech #Actu #Security

---

## 5. Contraintes Accessibility

### Contraste
- ✅ Cyan sur noir : WCAG AAA (contraste >7:1)
- ✅ Orange sur blanc/clair : WCAG AAA
- ❌ Orange sur noir : insuffisant (< 4.5:1) → ne pas utiliser pour texte principal

### Sous-titres & Texte
- **Fond noir :** texte blanc ou cyan
- **Fond blanc/clair :** texte orange ou noir
- **Sous-titres durs :** Orange fond blanc (contraste excellent)

---

## 6. Règles de Composition (Miniatures)

### Structure Générale
1. **Fond :** Noir profond (#0A0E27) ou dégradé noir → cyan très sombre
2. **Zone de texte principal :** Haut 60%, centré
3. **Zone accent :** Bas 30%, orange ou cyan
4. **Logo/Watermark :** Coin bas-droit, petit

### Hiérarchie Visuelle
1. **Titre principal (35-40% de la hauteur :** Blanc ou cyan, gros
2. **Sous-titre / accroche (25-30%)** Orange sur blanc ou box léger
3. **Élément visuel (20-30%)** Image pertinente avec effet néon ou glow
4. **Branding discret (5-10%)** Logo watermark

### Densité & Clarté
- **Max 3 niveaux textuels** (titre + sous-titre + badge)
- **Blanc respirant** : 15-20% de la surface en espace vide
- **Pas de surcharge :** 1 image/vidéo clé, 1-2 accents

---

## 7. Dégradés & Effets (Optionnel)

### Dégradés Recommandés
- **Fond :** Noir profond (#0A0E27) → bleu très sombre (#1A3A4A)
- **Accent :** Orange (#FF9500) → Orange sombre (#CC7700) en angle 45°

### Effets
- **Glow/Néon :** Cyan avec `box-shadow: 0 0 10px #00D9FF` (subtil)
- **Glitch :** Optionnel, utilisé avec parcimonie (pas chaque vidéo)

---

## 8. Exemples de Combinaisons (Miniatures)

### Type 1 : Titre Blanc + Accent Orange
```
[Fond noir dégradé]
[Image tech/IA au centre, légèrement transparente]
[Titre blanc gros : "OpenAI Lance GPT-5"]
[Sous-titre orange sur box blanc arrondi : "Révolution IA"]
[Watermark cyan bas-droit]
```

### Type 2 : Titre Cyan + Callout Orange
```
[Fond noir]
[Titre cyan gros : "SECURITY BREACH"]
[Box orange blanc : "Ce que tu dois savoir"]
[Image pertinente côté droit]
[Logo watermark]
```

### Type 3 : Minimaliste (Texte Seul)
```
[Fond noir]
[Dégradé noir → cyan très sombre]
[Texte blanc principal centré]
[Accent orange très petit bas]
[Watermark discret]
```

---

## 9. Implémentation Routine (Points Clés)

### Pour la Routine de Génération Miniatures

- ✅ **Toujours** : Noir fond, cyan texte accroche ou blanc texte principal
- ✅ **Orange obligatoire** : Au moins 1 élément orange (sous-titre ou box)
- ✅ **Logo** : Watermark cyan petit, bas-droit, 70% opacité
- ✅ **Contraste** : Tester WCAG AA minimum
- ❌ **À éviter** : Orange sur noir pour texte principal, surcharge couleur, polices fancy non-lisibles

### Fichiers à Utiliser
- **Hex Codes** : Copier-coller exact (`#00D9FF`, `#FF9500`, etc.)
- **Fonts** : Montserrat Bold (titres), Inter Regular (corps)
- **Image Assets** : Utiliser la librairie Drive, redimensionner 1280x720 (shorts)

---

## 10. Évolution & Versioning

**Version 1.0 (05/08/2026) :**
- Palette initiale : Cyan + Orange + Noir
- Typographies définies
- Miniatures : structure validée

**Prochaines révisions :**
- Feedback après 2-3 semaines de miniatures auto-générées
- Ajustements based on CTR/performance
- Ajout effets visuels si pertinent
