# Orchestration: 6 Prompts dans le Pipeline Production
## Comment intégrer automatiquement Prompt #1-6 dans la routine quotidienne

---

## 🎯 Vue d'ensemble

**Avant (ancien workflow):**
```
Directives (lundi 9h) → Production (lundi-vendredi 10h) → Script → Upload YouTube
```

**Après (optimisé avec 6 prompts):**
```
Directives
     ↓
Audit Niche (Prompt #1) ← Une fois seulement
     ↓
[Chaque jour]
├─ Titres/Miniatures (Prompt #2) ← Après sujet choisi
├─ Script (Prompt #3) ← 45min après
├─ Découpage B-Roll (Prompt #4) ← Parallèle
├─ Montage réalisé
└─ SEO/Meta (Prompt #5) + Monétisation (Prompt #6) ← 24h avant publication
```

---

## 🔄 Timeline quotidienne (10h GMT = 12h Paris)

### Lundi 10h00-10h05: Routine Production SETUP

```python
# Pseudocode: Routine production démarre
1. Charger directives (directives-production-2026-08-03.yaml)
2. Scraper trends (Google Trends + Reddit + HN)
3. Sélectionner TOP 2 sujets par CPM estimate
4. Créer dossier videos_prod/YYYY-MM-DD/
```

### Lundi 10h05-10h20: Prompt #2 (Titres & Miniatures)

**Trigger:** Sujet 1 défini

```
Input: Sujet choisi (ex: "Claude 3.5 Sonnet vs GPT-4o")
Agent Claude: Prompt #2 → 10 titres + 3 miniature specs
Output: titles-thumbnails.md
Time: ~5min
```

**Workflow:**
```bash
# Pseudo-bash
sujet_1="Claude 3.5 Sonnet vs GPT-4o"
claude_api --prompt prompts/2-titres-miniatures.txt \
           --context "sujet=$sujet_1" \
           > videos_prod/YYYY-MM-DD/titles-thumbnails.md
```

### Lundi 10h20-11h05: Prompt #3 (Script)

**Trigger:** Titre approuvé

```
Input: Sujet + Titre final + Directives (durée cible 50s, hook strategy)
Agent Claude: Prompt #3 → Script complet
Output: script-final.txt
Time: ~30-45min
```

**Workflow:**
```bash
titre_final="Cette IA code 10x plus vite que toi"
claude_api --prompt prompts/3-script-pro.txt \
           --context "sujet=$sujet_1&titre=$titre_final&duree=50&hook_strategy=surprise" \
           > videos_prod/YYYY-MM-DD/script-final.txt
```

**Validation Théo:** Théo scan script en 5min (check hook, tone, affiliation)

### Lundi 11h05-11h25: Prompt #4 (Découpage B-Roll)

**Trigger:** Script validé

```
Input: Script complet
Agent Claude: Prompt #4 → Tableau découpage technique
Output: storyboard-technique.csv
Time: ~20min
```

**Workflow:**
```bash
claude_api --prompt prompts/4-broll-decoupe.txt \
           --context "script=$(cat script-final.txt)" \
           > videos_prod/YYYY-MM-DD/storyboard-technique.csv
```

### Lundi 11h25-12h00: Montage Parallèle

**Parallèle:** Pendant que Claude fait découpage, monteur peut démarrer:
- [ ] Voix off générée (Google Cloud TTS ou similar)
- [ ] B-roll récupéré de library
- [ ] Commencer montage brut (rough cut)

### Lundi 12h00: Upload privé YouTube

**Routine production complète:**
- [ ] Video généré + uploadé privé
- [ ] Métadonnées vidéo sauvegardées

**Fichiers dans videos_prod/YYYY-MM-DD/:**
```
├── script-final.txt
├── titles-thumbnails.md
├── storyboard-technique.csv
├── video.mp4
└── metadata.json
```

### Dimanche 18h00 (24h avant publication): Prompt #5 + #6

**Trigger:** Video prêt à publier

```
Input: Titre + Sujet + Script
Agent Claude: Prompt #5 → Description + Tags + Pinned comment
Agent Claude: Prompt #6 → Affiliation/CTA recommendations

Output: seo-metadata.md + monetization-notes.md
Time: ~15min total
```

**Workflow:**
```bash
claude_api --prompt prompts/5-seo-metadata.txt \
           --context "titre=$titre_final&sujet=$sujet_1" \
           > videos_prod/YYYY-MM-DD/seo-metadata.md

claude_api --prompt prompts/6-monetization.txt \
           --context "sujet=$sujet_1&video_number=1" \
           > videos_prod/YYYY-MM-DD/monetization-notes.md
```

### Lundi publication (Théo valide)

**Théo dans YouTube Studio:**
- [ ] Copie description depuis seo-metadata.md
- [ ] Copie tags depuis seo-metadata.md
- [ ] Programme publication 11h Paris
- [ ] Épingle commentaire (depuis seo-metadata.md)

---

## 📦 Fichiers de configuration

### Fichier 1: `prompts/config.yaml`

```yaml
# Configuration centrale des 6 prompts

prompts:
  1_audit_niche:
    file: "1-audit-niche.txt"
    frequency: "quarterly"
    trigger: "manual"
    inputs: ["niche", "audience_type"]
    outputs: ["NICHE-AUDIT-2026.md"]
    
  2_titres_miniatures:
    file: "2-titres-miniatures.txt"
    frequency: "per_video"
    trigger: "sujet_defined"
    inputs: ["sujet", "directives_optional"]
    outputs: ["titles-thumbnails.md"]
    time_estimate: "5min"
    
  3_script_pro:
    file: "3-script-pro.txt"
    frequency: "per_video"
    trigger: "titre_approuvé"
    inputs: ["sujet", "titre", "directives.duree_cible", "directives.hook_strategy"]
    outputs: ["script-final.txt"]
    time_estimate: "30min"
    
  4_broll_decoupe:
    file: "4-broll-decoupe.txt"
    frequency: "per_video"
    trigger: "script_validated"
    inputs: ["script_complet"]
    outputs: ["storyboard-technique.csv"]
    time_estimate: "20min"
    
  5_seo_metadata:
    file: "5-seo-metadata.txt"
    frequency: "per_video"
    trigger: "24h_before_publication"
    inputs: ["titre_final", "sujet", "script"]
    outputs: ["seo-metadata.md"]
    time_estimate: "10min"
    
  6_monetization:
    file: "6-monetization.txt"
    frequency: "per_video"
    trigger: "24h_before_publication"
    inputs: ["sujet", "video_number", "audience_profile"]
    outputs: ["monetization-notes.md"]
    time_estimate: "10min"

# Validation checkpoints
validation:
  prompt_2_output: "Must have 3 thumbnail specs with mobile testing"
  prompt_3_output: "Script must have hook (15s) + pattern interrupts"
  prompt_4_output: "Storyboard must have 1 interrupt every 90s"
  prompt_5_output: "Description must have keywords in first 2 sentences"
  prompt_6_output: "CTA must be organic, not forced"
```

### Fichier 2: `templates/prompt-template.txt`

```
[PROMPT TEMPLATE - Adaptable]

Contexte (standard pour tous les prompts):
- Chaîne: Tech & Café (Shorts 30-60s + long-form occasionnel)
- Niche: IA/Tech/Fondateurs
- Audience: Décideurs tech, entrepreneurs, devs 25-45 ans
- CPM target: 1.8+
- Style: Premium, accessible, pas condescendant
- Brand voice: Intelligent + léger + actionable

[PROMPT SPÉCIFIQUE]

Livrable attendu: [Format spécifique]
Délai: [X minutes]
Validation: [Checklist]
```

---

## 🤖 Intégration Cloud Routine (API Claude)

### Amélioration Routine Production Cloud

**Ajout à `trig_01QTPw2RxoroMRcD4E3FthPn`:**

```python
# Pseudocode: Routine production améliorée

def production_routine():
    # ÉTAPE 0: Load directives
    directives = load_yaml("directives-production-YYYY-MM-DD.yaml")
    
    # ÉTAPE 1: Scraper + Sélection sujets
    trends = scrape_trends()
    top_2_subjects = rank_by_cpm_velocity(trends, directives)
    
    for subject in top_2_subjects:
        # PROMPT #2: Titres/Miniatures
        titles_output = claude_api(
            prompt=load_prompt("prompts/2-titres-miniatures.txt"),
            context={"sujet": subject, "directives": directives}
        )
        titles_thumbnails = parse(titles_output)
        best_title = select_top_title(titles_thumbnails)
        save(f"videos_prod/{date}/titles-thumbnails.md", titles_output)
        
        # PROMPT #3: Script
        script_output = claude_api(
            prompt=load_prompt("prompts/3-script-pro.txt"),
            context={
                "sujet": subject,
                "titre": best_title,
                "duree": directives.duree_cible,
                "hook_strategy": directives.hook_strategy
            }
        )
        save(f"videos_prod/{date}/script-final.txt", script_output)
        
        # PROMPT #4: Découpage B-Roll
        broll_output = claude_api(
            prompt=load_prompt("prompts/4-broll-decoupe.txt"),
            context={"script": script_output}
        )
        save(f"videos_prod/{date}/storyboard-technique.csv", broll_output)
        
        # ÉTAPE 5-6: Voix off + Montage + Upload
        voix_off = generate_voix(script_output)
        broll_assets = get_broll_from_library(broll_output)
        video = montage(voix_off, broll_assets)
        
        # Upload privé YouTube
        video_id = youtube_upload_private(video, metadata)
        
        # PROMPT #5 + #6: SEO + Monétisation (24h avant)
        schedule_delayed_task({
            "delay": "24h",
            "tasks": [
                {
                    "prompt": "5-seo-metadata.txt",
                    "context": {"titre": best_title, "sujet": subject},
                    "output": f"videos_prod/{date}/seo-metadata.md"
                },
                {
                    "prompt": "6-monetization.txt",
                    "context": {"sujet": subject, "video_num": len(videos_this_week)},
                    "output": f"videos_prod/{date}/monetization-notes.md"
                }
            ]
        })

if __name__ == "__main__":
    production_routine()
```

---

## 📊 Stockage fichiers de prompts

```
livrables/youtube/.../prompts/
├── config.yaml                          ← Config centrale
├── template.txt                         ← Template generic
├── 1-audit-niche.txt                   ← Prompt Audit Niche
├── 2-titres-miniatures.txt             ← Prompt Titres/Miniatures
├── 3-script-pro.txt                    ← Prompt Script
├── 4-broll-decoupe.txt                 ← Prompt Découpage
├── 5-seo-metadata.txt                  ← Prompt SEO
└── 6-monetization.txt                  ← Prompt Monétisation
```

**Chaque fichier de prompt:**
- Texte exact à passer à Claude API
- Personnalisé pour Tech & Café (contexte niche)
- Versioning (v1.0, v1.1, etc) si améliorations

---

## ✅ Checklist Implémentation

### Phase 1: Setup (cette semaine)
- [ ] Créer dossier `prompts/`
- [ ] Remplir `config.yaml`
- [ ] Extraire 6 prompts dans fichiers `.txt`
- [ ] Tester Prompt #1 (Audit Niche) manuellement

### Phase 2: Test (semaine 2)
- [ ] Tester Prompt #2 sur sujet réel (titres/miniatures)
- [ ] Tester Prompt #3 (script complet)
- [ ] Valider output format (parseable)

### Phase 3: Intégration Cloud (semaine 3)
- [ ] Modifier routine production cloud (`trig_01QTPw2RxoroMRcD4E3FthPn`)
- [ ] Ajouter appels Claude API Prompts #2-4 dans routine
- [ ] Scheduler delayed tasks (Prompt #5-6 à 24h)
- [ ] Test production full cycle (du sujet au YouTube upload)

### Phase 4: Optimisation (semaine 4+)
- [ ] Mesurer CTR titres/miniatures (A/B test)
- [ ] Affiner prompts basé sur performance
- [ ] Enrichir backlog evergreen avec meilleurs concepts

---

## 📈 KPI à tracker

| Métrique | Baseline | Target 4 sem | Mesure |
|----------|----------|-------------|--------|
| Titre CTR | Unknown | +15% | YouTube Analytics |
| Thumbnail perf | Unknown | 60% win rate | A/B tests |
| Hook retention @ 10s | 36% | 42% | YouTube Analytics |
| Script affiliation CTR | Unknown | 2%+ | Link tracking |
| SEO visibility | Unknown | Top 3 search | YouTube search console |
| Production time | 2h | 1.5h (optimisé) | Time tracking |

---

## 🔗 Connexion avec Pipeline Existant

```
DIRECTIVES (lundi 9h)
     ↓
PRODUCTION CLOUD (lundi 10h)
├─ Load directives
├─ Scrape trends (filtrées par angles privilégiés)
├─ Rank sujets par CPM
├─ Run Prompts #2-4 (titres, script, découpage)
├─ Generate voix off + montage
├─ Upload YouTube (privé)
└─ Schedule Prompts #5-6 pour dimanche 18h
     ↓
YOUTUBE UPLOAD (lundi 11h)
     ↓
SEO/METADATA (dimanche 18h, 24h avant)
├─ Run Prompt #5 (description + tags)
├─ Run Prompt #6 (affiliation)
└─ Output prêt pour YouTube Studio
     ↓
THÉO VALIDATION (dimanche 19h)
├─ Review description/tags/CTA
├─ Programme publication lundi 11h
└─ Épingle commentaire d'engagement
```

---

## 🎯 TL;DR: Prochaines étapes

1. **Créer dossier `prompts/`** + fichiers `.txt` pour 6 prompts ✓ (dans ce document)
2. **Tester Prompt #1 (Audit Niche)** manuellement d'ici mercredi
3. **Modifier routine production cloud** pour intégrer Prompts #2-4 (semaine 2)
4. **Mesurer impact** sur titre CTR + retention (semaine 4)

**Estimation effort:** 
- Phase 1 (setup): 2h
- Phase 2 (test manual): 3h
- Phase 3 (cloud integration): 4h
- Phase 4+ (optimisation): Ongoing

---

**Status:** ✅ Ready  
**Ressources:** PROMPTS-STRATEGIQUES-PRODUCTION.md + this file  
**Next:** Approve + start Phase 1
