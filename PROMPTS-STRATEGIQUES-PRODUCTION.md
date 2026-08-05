# 6 Prompts Stratégiques Production YouTube
## Adaptés pour Tech & Café (IA/Tech/Fondateurs)

---

## 📋 Vue d'ensemble

Ces 6 prompts couvrent l'**arc complet** d'une vidéo optimisée (de la niche à la monétisation).

**Quand les utiliser:**
1. **Audit Niche** = Une fois (ou trimestriel pour repositionnement)
2. **Titres/Miniatures** = Chaque vidéo (après script validé)
3. **Script Pro** = Chaque vidéo (avant montage)
4. **Découpage B-Roll** = Chaque vidéo (après script, avant montage)
5. **SEO/Méta** = Chaque vidéo (24h avant publication)
6. **Monétisation** = Chaque 3-4 vidéos (intégrer affiliations/CTA)

**Flux:**
```
Audit Niche (1x)
     ↓
[Pour chaque vidéo]
Titres/Miniatures → Script → Découpage B-Roll → SEO → Monétisation
```

---

## 1️⃣ AUDIT NICHE ET POSITIONNEMENT

### Prompt adapté Tech & Café

```
Agis en tant que stratège de croissance YouTube expert et analyste de données.
La chaîne Tech & Café produit des Shorts (30-60s) et long-format sur l'actualité IA/Tech/Fondateurs.

Analyse:
1. Les 5 sous-niches les plus rentables (CPM/RPM élevé) dans IA/Tech:
   - Format court (Shorts 30-60s)
   - Audience: décideurs tech, entrepreneurs, devs, étudiants IA
   
2. Identifie les angles morts que les TOP creators (MrBeast, Vsauce, TED-Ed style) n'exploitent PAS:
   - Quels sujets IA/Tech sont sur-traités? (Crypto, ChatGPT basics)
   - Quels angles sont vierges? (AI safety, founding stories, regulatory)
   
3. Propose 3 concepts de chaîne uniques avec positionnement premium:
   - Concept 1: Nom + Tagline + Style narratif + Promesse spectateur + Barrière entrée
   - Concept 2: Idem
   - Concept 3: Idem
   
4. Profil type audience:
   - Âge, profession, revenus
   - Douleurs/objectifs
   - Où ils consomment le contenu? (YouTube, Reddit, Product Hunt, HN)
   - Quoi les fait s'abonner? (What hooks them?)

Format:
- Sous-niches: JSON array avec {name, cpm_range, audience_type, content_pillars}
- Angles morts: Liste bullet with "Opportunity" + "Why nobody does it" + "Your angle"
- Concepts: Tableau 3 colonnes {Concept | Narrative Style | Differentiation}
```

**Où sauvegarder:** `livrables/youtube/.../NICHE-AUDIT-2026.md`  
**Fréquence:** Trimestrielle (ou si repositionnement)  
**Output:** Inputs pour les 5 autres prompts

---

## 2️⃣ INGÉNIERIE TITRES & MINIATURES

### Prompt adapté Tech & Café

```
Agis en tant que Directeur Artistique et Growth Hacker YouTube expert en psychologie visuelle.

Sujet vidéo: [INSÉRER SUJET]
Format: Short (30-60s)
Audience cible: Tech entrepreneurs et devs (25-45 ans)
CPM target: 1.8+

Génère:
1. 10 titres classés par psychologie (<60 chars chacun):
   - 3 titres "Curiosité" (question/mystère/révélation)
   - 3 titres "Bénéfice" (promesse valeur/hack/skin in game)
   - 3 titres "Contre-intuitif" (brise idée reçue/chiffre choc)
   - 1 titre "Viral potential" (trending angle)

2. Pour les TOP 3 titres, décris PRÉCISÉMENT le visuel miniature:
   - Titre: [Title]
   - Sujet central miniature: [Objet/personne/graphique focal]
   - Arrière-plan: [Couleur, texture, pattern pour mobile 340x190px]
   - Expression faciale (si présent): [Emotion: surprise, concern, confidence?]
   - Texte overlay (MAX 3 mots): [Phrase choc ou chiffre]
   - Stratégie contraste mobile: [Pourquoi ça pop sur petit écran?]
   - Psychologie couleur: [Rouge = urgency, Bleu = trust, Jaune = energy]

3. Validation:
   - Titre et miniature se complètent-ils SANS redondance?
   - Est-ce lisible sur mobile (340x190px)?
   - Y a-t-il contraste suffisant (texte vs background)?

Format output:
```
TITRE #1 (Curiosité)
━━━━━━━━━━━━━━━━━━━
Titre: [Title]
Miniature:
  - Focal: [Objet/Expression]
  - Background: [Couleur/Texture]
  - Overlay: [3 mots max]
  - Mobile test: [Lisible? Oui/Non]
  - Psychologie: [Couleur strategy]

[Répéter pour titres #2, #3]
```
```

**Où sauvegarder:** `livrables/youtube/.../videos_prod/YYYY-MM-DD/titles-thumbnails.md`  
**Fréquence:** Chaque vidéo (après script validé, avant montage)  
**Input:** Sujet vidéo (issu des directives/trends)  
**Output:** Titre final + Miniature spec (design team ou Canva template)

---

## 3️⃣ SCRIPT PRO À RÉTENTION MAXIMALE

### Prompt adapté Tech & Café

```
Agis en tant que scénariste professionnel pour documentaires premium (style Vox, TED-Ed, Kurzgesagt).

Contexte:
- Format: Short (50s) OU Long (8-12min)
- Niche: IA/Tech/Fondateurs
- Audience: Décideurs tech 25-45 ans (éduqués, tech-savvy)
- Style: Accessible + intelligent (pas condescendant, pas trop jargon)
- Hook: Brise une idée reçue ou révèle stat choc

[INSÉRER SUJET ET DURÉE]

Rédige le script complet en structurant ainsi:

**STRUCTURE (timecode inclus):**

[00:00-00:15] HOOK (15s)
- Accroche percutante qui brise une idée reçue
- Ou une question provocante
- Ou un chiffre contre-intuitif
- Format: "Tu croyais que X, mais en réalité..."

[00:15-00:45] SETUP (30s)
- Établis le contexte/problème
- Pose la question centrale
- Crée la curiosité

[00:45-DURATION-10s] CORPS (40-70s pour Shorts, 2-5min pour long)
- Pattern interrupts toutes les 90 secondes (relance narrative/visuelle)
- Utilise des exemples concrets (pas d'abstractions)
- Voix active, phrases courtes
- Un concept par 20-30 secondes

[DURATION-10s-DURATION] CTA (10s)
- Appel à l'action organique (pas forcé)
- Aligné monétisation si possible
- Format: "Abonne-toi pour X" ou "Découvre Y"

**RÈGLES:**
- Langage simple, actif, percutant
- Zéro jargon inutile (ou explique si nécessaire)
- Une idée par phrase
- Verbes d'action (ne pas "il y a X")
- Pas de "euh", "hmmm", filler words

**OUTPUT FORMAT:**
[Timecode] SPEAKER: "Exact text à dire avec pauses naturelles."

---

Après le script complet, fournis:
- Hook strength (1-10): Pourquoi?
- Pattern interrupts count: Quand?
- Estimated retention: Basé sur structure
- Affiliate/CTA opportunity: Où l'intégrer naturellement?
```

**Où sauvegarder:** `livrables/youtube/.../videos_prod/YYYY-MM-DD/script-final.txt`  
**Fréquence:** Chaque vidéo  
**Input:** Sujet + Durée + Directives optionnelles (hook strategy)  
**Output:** Script prêt pour voix off

---

## 4️⃣ DÉCOUPAGE B-ROLL ET AMBIANCE VISUELLE

### Prompt adapté Tech & Café

```
Agis en tant que monteur vidéo senior expert en rythme et pacing.

À partir du script ci-après [ou insérer passage spécifique]:

Fournis un TABLEAU DE DÉCOUPAGE TECHNIQUE détaillé:

| Timecode | Texte dit | Effet visuel | B-Roll suggestion | Sound design |
|----------|-----------|--------------|------------------|--------------|
| 00:00-00:03 | "Tu croyais..." | Texte cinétique blanc | Fond neutre noir | Silence 0.2s |
| 00:03-00:08 | "...mais..." | Zoom 1.2x | Graphique trend | Whoosh subtle |
| [etc] | | | | |

**Colonnes du tableau:**

1. **Timecode**: [00:00-00:XX] (en secondes)

2. **Texte dit**: Texte exact du script (vérifie que ça matche audio)

3. **Effet visuel** (à l'écran):
   - Texte cinétique: [Texte + animation, ex: "fade-in, hold 2s, exit zoom"]
   - Graphique/données: [Type + couleur, ex: "bar chart rouge trending up"]
   - Animation: [Mouvement, ex: "zoom progressif 1.2x", "pan left"]
   - Pattern interrupt: [TOUS les 90s environ]

4. **B-Roll suggestion**:
   - Source: [Local library / Pexels / Pixabay / Wikimedia]
   - Description: [Précis, ex: "Laptop screen coding, dim blue light, 2s clip"]
   - Mood: [Color grade, ex: "cool tones, desaturated, cinematic"]
   - Duration: [2s, 5s, etc]
   - Transition: [Cut, Fade, Zoom, etc]

5. **Sound design**:
   - Type: [Whoosh, beat, silence, tone, ambient]
   - Timing: [Exact secondes où le son démarre]
   - Duration: [0.2s, 1s, etc]
   - Purpose: [Emphasis, transition, energy boost]
   - Example: "Whoosh 0.3s at 00:05 for transition punch"

**RÈGLES:**
- Pattern interrupts: minimum 1 chaque 90s (visuel OR son)
- Transitions: fade (60ms) naturel, pas jarring
- Text on-screen: max 1 ligne à la fois, sans-serif bold, blanc+shadow
- B-roll pacing: change toutes les 5-7s (keeps engagement)
- Sound: whoosh (hook impact), silence (emphasis), beat (CTA energy)

**À la fin du tableau, résume:**
- Total pattern interrupts: X (toutes les ~90s? ✓)
- Music/ambient: Suggestion (genre + BPM)
- Color grading unity: Cohérent visually? (Tous cinéma, tous tech, etc)
```

**Où sauvegarder:** `livrables/youtube/.../videos_prod/YYYY-MM-DD/storyboard-technique.csv`  
**Fréquence:** Chaque vidéo (après script approuvé)  
**Input:** Script complet  
**Output:** Blueprint montage (pour monteur ou IA video generation)

---

## 5️⃣ OPTIMISATION SEO ET MÉTA-DESCRIPTION

### Prompt adapté Tech & Café

```
Agis en tant qu'expert SEO YouTube avec profonde connaissance de l'algo.

Vidéo titre: [INSÉRER TITRE FINAL]
Niche: IA/Tech/Fondateurs
Format: [Short 30-60s OU Long-form]

Rédige:

**1. DESCRIPTION (300 mots optimisée)**
- Phrase 1-2: Mots-clés principaux naturellement
- Phrase 3+: Contexte enrichi
- Include: Horodatages chapitres (si long-form)
- Format structure:
  ```
  [Phrase d'intro avec keyword principal]
  
  [Context + 2-3 sentences expansion]
  
  [Timecode chapters si applicable]:
  00:00 - Hook
  00:15 - Concept 1
  02:30 - Concept 2
  [etc]
  
  [Call-to-action subscribe]
  ```

**2. TAGS (15 tags classés par importance)**
Format: 1 tag par ligne, du plus important au moins important
Exemple ordre:
- Exact match keywords (high search vol): "AI", "machine learning"
- Long-tail keywords (specific): "claude 3.5 sonnet", "AI agents"
- Trend tags (seasonal): [Current hot topic]
- Niche tags (audience): "tech entrepreneurs", "founders"
- Brand tags: "tech and cafe", "tech actualite"

**3. MESSAGE ÉPINGLÉ (Engagement generator)**
- Timing: À publier immédiatement (heure 1)
- Longueur: 2-3 phrases max
- Objectif: Créer engagement dès le départ
- Format: Question + call-to-action
- Exemple: "❓ [Question provocante relative vidéo] — Partage ton avis dans les commentaires! 👇"

**Output format:**
```
DESCRIPTION:
[300 mots]

TAGS (15):
1. [Tag 1]
2. [Tag 2]
...
15. [Tag 15]

PINNED COMMENT:
[2-3 phrases]
```
```

**Où sauvegarder:** `livrables/youtube/.../videos_prod/YYYY-MM-DD/seo-metadata.md`  
**Fréquence:** Chaque vidéo (24h avant publication)  
**Input:** Titre final + Sujet  
**Output:** Description + Tags + Pinned message (prêt à copier-coller YouTube)

---

## 6️⃣ STRATÉGIE MONÉTISATION & TUNNEL DE VENTE

### Prompt adapté Tech & Café

```
Agis en tant que consultant en business digital et creator economy expert.

Contexte:
- Niche: IA/Tech/Fondateurs
- Format: Shorts (30-60s) + quelques long-forms
- Audience: Entrepreneurs/devs 25-45 ans, revenus moyens-élevés
- Objectif: Dépasser AdSense (RPM bas ~0.5-1.0) vers multiple revenue streams
- Timeline: 12 mois

Conçois un plan de monétisation hybride:

**1. OFFRES FRONT-END (Low ticket, volume):**
- Affiliation produits: [3-5 produits tech pertinents]
  - Produit: [Nom]
  - Commission: [X%]
  - Angle intégration: [Comment l'intégrer naturellement?]
  - Expected CTR: [X%]
  - Expected conversion: [X%]
  
- Produits numériques: [1-2 options]
  - Produit: [Email course / guide / template]
  - Price: [$X]
  - Landing page CTA: [Où dans la vidéo?]

**2. OFFRES HIGH-TICKET (Premium, profitability):**
- Sponsorship vidéo: [Qui pourrait te sponsoriser?]
  - Prospect company: [Ex: GitHub, Linear, Anthropic]
  - Package: [$X pour vidéo + mention]
  - Fit: [Pourquoi ça marche avec ton audience?]

- Community/Course premium:
  - Concept: [Quoi enseigner?]
  - Price: [$X/mois]
  - Value prop: [Quoi que YouTube libre ne propose pas?]

**3. PLAN D'INTÉGRATION (10 prochaines vidéos):**
Pour chaque vidéo:
  - Video #1: [Sujet] → Affiliation [Produit X] CTA @ [00:45]
  - Video #2: [Sujet] → Sponsor [Company Y] (native integration)
  - Video #3: [Sujet] → Course pitch (soft mention)
  - [etc]

**Format output:**
```
FRONT-END OFFERS:
[Table: Produit | Commission | CTR | CTA timing]

HIGH-TICKET OFFERS:
[Table: Prospect | Package price | Pitch timing]

12-MONTH ROADMAP:
[Table: Month | Revenue stream | Target $ | Execution]

INTEGRATION CHECKLIST (10 videos):
Video 1: Affiliation [Product] @ timecode + copy
Video 2: Sponsor [Company] native @ timecode
[etc]
```

**Règles:**
- CTA doit être organique (pas "click this link!")
- Affiliation seulement si produit tu crois vraiment dedans
- Sponsorship: premium only (pas n'importe qui)
- Mix: 60% AdSense + 30% affiliation + 10% high-ticket = revenue target
```

**Où sauvegarder:** `livrables/youtube/.../MONETIZATION-PLAN-12MONTHS.md`  
**Fréquence:** Chaque 3-4 vidéos (mise à jour roadmap)  
**Input:** Audience insights + Performance data  
**Output:** Stratégie + Calendar intégration

---

## 🔄 Workflow Intégration

### Arc complet (pour chaque vidéo)

```
1. SUJET DÉFINI (via directives/trends)
       ↓
2. TITRES/MINIATURES générés (Prompt #2)
       ↓
3. SCRIPT écrit (Prompt #3)
       ↓
4. DÉCOUPAGE B-ROLL créé (Prompt #4)
       ↓
5. MONTAGE réalisé (par monteur ou IA)
       ↓
6. SEO/META-DESCRIPTION ajoutés (Prompt #5, 24h avant)
       ↓
7. CTA/AFFILIATION intégrée (Prompt #6, si applicable)
       ↓
8. PUBLICATION (validation Théo)
```

### Fichiers stockés par vidéo

```
videos_prod/YYYY-MM-DD/
├── script-final.txt                 ← Prompt #3
├── titles-thumbnails.md             ← Prompt #2
├── storyboard-technique.csv         ← Prompt #4
├── seo-metadata.md                  ← Prompt #5
├── monetization-notes.md            ← Prompt #6 extract
├── video.mp4                        ← Fichier final
└── metadata.json                    ← YouTube upload meta
```

---

## 📊 Métriques de succès

Après 4 semaines (10 vidéos):

| Métrique | Target | Comment mesurer |
|----------|--------|-----------------|
| Titre CTR | +15% vs baseline | YouTube Analytics |
| Thumbnail performance | Win rate 60%+ | A/B test data |
| Retention (hook) | 45%+ @ 10s | YouTube Analytics |
| Affiliation CTR | 2%+ | Link tracking / affiliate stats |
| Script quality | Viewer feedback | Commentaires + survey |
| SEO ranking | Top 3 YouTube search | Search query reports |

---

## 🎯 TL;DR: Intégration immédiate

**Semaine 1 (cette semaine):**
- [ ] Run Prompt #1 (Audit Niche) = Inputs pour autres prompts

**Semaine 2+ (chaque vidéo):**
- [ ] Prompt #2 (Titres) → Choisis meilleur
- [ ] Prompt #3 (Script) → Valide
- [ ] Prompt #4 (Découpage) → Brief monteur
- [ ] Prompt #5 (SEO) → 24h avant publication
- [ ] Prompt #6 (Monétisation) → Chaque 3-4 videos

**Automation possible:**
- Prompts #2-5 peuvent être APIfiés (Claude API)
- Intégration dans routine production cloud (lundi-vendredi 10h)
- Output: Scripts + metadata auto, validation manuelle Théo

---

**Statut:** ✅ Prêt implementation  
**Ressources:** Ce fichier + 6 prompts adaptés niche  
**Prochaine étape:** Appliquer à première vidéo demain (testing)
