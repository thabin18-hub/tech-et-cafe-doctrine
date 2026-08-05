# Validation Routine Analytique
## Checklist pour 02-03 août 2026

---

## 🔄 Timeline

| Date | Heure | Routine | Fichier attendu | Status |
|------|-------|---------|-----------------|--------|
| **02/08** | 23:59 GMT | Rapport analytique | `rapport-2026-08-02.{docx,pdf,pptx}` | À vérifier 03/08 00h15 |
| **03/08** | 09:00 GMT | Recommandations analytiques | `directives-production-2026-08-03.yaml` | À vérifier 03/08 09h30 |
| **03/08** | 10:00 GMT | Production (lire directives) | 2 shorts + logs | À vérifier 03/08 10h30 |

---

## ✅ Dimanche 02/08 - Rapport Analytique

**Routine:** `trig_0164VZ1y6g5EpNwEkfTj2mQG` ("Tech et Cafe - Rapport analytique hebdo")  
**Timing:** Dimanche 23:59 GMT (= lundi 01:59 Paris)

### À vérifier lundi 03/08 à 00h15+ :

```bash
ls -la livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/rapports/
```

**Fichiers attendus** (au moins 1):
- ✅ `rapport-2026-08-02.docx` (Word avec chiffres + graphiques)
- ✅ `rapport-2026-08-02.pdf` (PDF lisible)
- ✅ `rapport-2026-08-02.pptx` (PowerPoint avec diapos)

**Contenu attendu dans rapport**:
- Période: 27/07 - 02/08 (1ère semaine complète)
- Nombre videos publiées (8-10 expected)
- Vues totales + moyennes par video
- Retention moyenne %
- CPM moyen
- Abonnés gagnés (vers 1000 pour YPP)
- Patterns détectés (quels sujets performent mieux)
- Recommandations 3-5 items

**Si fichier absent** → Rapport analytique a échoué:
- Vérifie que YouTube Data API v3 + YouTube Analytics API sont activées
- Vérifie token OAuth `YOUTUBE_ANALYTICS_REFRESH_TOKEN` valide
- Check logs routine cloud (Anthropic dashboard)

---

## ✅ Lundi 03/08 - Directives Production

**Routine:** `trig_01QgtHQfuS4GYWVGBZ3jA8M4` ("Recommandations analytiques hebdo")  
**Timing:** Lundi 9h GMT (= 11h Paris)

### À vérifier lundi 03/08 à 09h30+ :

```bash
ls -la livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/directives/
```

**Fichiers attendus**:
- ✅ `directives-production-2026-08-03.yaml` (Nouvellement généré)
- ✅ `README.md` (Template/doc, existe déjà)

**Validation du fichier YAML**:

```bash
# Vérifier syntaxe YAML
python3 -c "import yaml; yaml.safe_load(open('directives-production-2026-08-03.yaml'))"
# Sortie: Rien = OK, Error = fichier mal formé

# Vérifier contenu
cat directives-production-2026-08-03.yaml | grep -E "semaine_du|angles_privilegier|cpm_target"
```

**Contenu attendu**:
- ✅ `semaine_du: "2026-08-03"`
- ✅ `data_semaine_precedente:` (chiffres du rapport)
- ✅ `angles_privilegier:` (3-4 sujets, avec % ou CPM)
- ✅ `angles_eviter:` (2-3 sujets à éviter)
- ✅ `parametres.duree_cible` (ex: "48-55s")
- ✅ `parametres.hook_strategy` (ex: "surprise + contre-intuitif")
- ✅ `retention_target` (ex: "40%")
- ✅ `cpm_target_min` (ex: "1.8")
- ✅ `affiliation_priority` (3+ options, conversions %)
- ✅ `patterns` (3+ patterns data-driven)
- ✅ `notes` (contexte + priorisation production)

**Exemple ligne d'un angle privilégier OK**:
```yaml
angles_privilegier:
  - "IA agents autonomes (retention +8%, CPM 2.1)"  ← Chiffres + source
  - "AI security (stable CPM 2.2, trending)"        ← Source
  - "Breakthrough research (trending Google + HN)"  ← Source visible
```

**Si fichier absent ou incomplet** → Recommandations a échoué:
- Vérifier rapport du 02/08 existe (dépendance)
- Check logs routine cloud
- Vérifier que prompt ROUTINE-RECOMMANDATIONS-PROMPT.md correspond à logique routin

---

## ✅ Lundi 03/08 - Production lit les directives

**Routine:** `trig_01QTPw2RxoroMRcD4E3FthPn` ("Tech et Cafe - Production 2 Shorts quotidiens")  
**Timing:** Lundi 10h GMT (= 12h Paris)

### À vérifier lundi 03/08 à 10h45+ :

```bash
# Vérifier que production a généré 2 shorts
ls -la livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/videos_prod/2026-08-03/

# Vérifier logs production
grep -E "directives|CPM|retention|hook" logs/production-2026-08-03.log
```

**Indicateurs succès**:
- ✅ 2 shorts générés pour 03/08
- ✅ Logs mentionnent "directives-production-2026-08-03.yaml" chargée
- ✅ Sujets choisis matchent `angles_privilegier` (pas crypto, pas memes)
- ✅ Durée scripts ~50s (in range 48-55s)
- ✅ Hooks incluent "surprise/contre-intuitif" comme indiqué
- ✅ CPM estimates logs ≥ 1.8 (target minimum)

**Logs attendus (exemple)**:
```
[03/08 10:00] Loading directives: directives-production-2026-08-03.yaml
[03/08 10:05] Angles privilegier: AI agents autonomes, AI security, Breakthrough research
[03/08 10:06] Scraping trends (Google Trends, Reddit, HN)
[03/08 10:08] Candidates: [Claude 3.5 Sonnet (CPM 2.1), EU AI Act fines (CPM 2.3)]
[03/08 10:10] Video 1: "Claude 3.5 Sonnet" - Hook: "Cette IA code mieux que les devs" - Duration: 51s - Estimated CPM: 2.1
[03/08 10:11] Video 2: "AI security holes" - Hook: "ChatGPT fera ce que tu veux" - Duration: 49s - Estimated CPM: 2.2
[03/08 10:20] Generated 2 videos. Uploaded private to YouTube.
```

**Si production n'a pas chargé les directives**:
- Vérifier PRODUCTION-CONFIG.yaml section `directives_hebdomadaire`
- Vérifier path du fichier directives est correct dans config
- Check logs production pour "Error loading directives"

---

## 🔧 En cas de problème

### Rapport absent (02/08 23:59)
```
Action: Vérifier YouTube Analytics API active + token OAuth valid
Fix: Re-auth ou regénérer token YOUTUBE_ANALYTICS_REFRESH_TOKEN dans .env
Workaround: Copier exemple rapport-template.docx → rapport-2026-08-02.docx pour test
```

### Directives absent (03/08 09:00)
```
Action: Vérifier rapport du 02/08 existe
Fix: Si rapport OK, check routine recommandations logs (Anthropic dashboard)
Workaround: Copier directives-production-2026-08-03.yaml (template déjà créé) pour test
```

### Production ne lit pas directives (03/08 10:00)
```
Action: Vérifier PRODUCTION-CONFIG.yaml section directives_hebdomadaire
Fix: Vérifier path: "directives/directives-production-YYYY-MM-DD.yaml" correct
Workaround: Éditer PRODUCTION-CONFIG.yaml manuellement, hardcoder les angles pour jour
```

---

## 📊 Metrics de succès

Après dimanche 09/08 (première semaine complète):

| Métrique | Target | Comment valider |
|----------|--------|-----------------|
| Rapport existe | 1 | Fichier dans `rapports/` |
| Directives existe | 1 | Fichier dans `directives/` |
| Directives YAML valide | ✅ | `python3 -c "import yaml; yaml.safe_load()"` |
| Production lit directives | ✅ | Logs mentionnent "directives chargées" |
| Angles respectés | ✅ | Sujets choisis ∈ `angles_privilegier` |
| CPM estimate ≥ target | ✅ | Logs montrent CPM ≥ 1.8 |
| Durée 48-55s | ✅ | Métadonnées scripts |
| Hooks data-driven | ✅ | Hooks matchent `hook_strategy` directives |

---

## 📞 Questions avant 02/08

- Avez-vous configuré les tokens OAuth (YouTube + Analytics) ?
- YouTube Analytics API activée sur le projet Cloud ?
- Avez-vous testé un rapport manuel pour valider format?
- Quelle version Python sur la machine cloud (pour parsing YAML) ?

---

## Prochaine étape: 09/08

Une fois tout validé (rapport + directives + production):
- Ajouter A/B testing miniatures (PRODUCTION-CONFIG.yaml enabled: true)
- Enrichir backlog-evergreen avec nouveaux concepts performants
- Affiner CPM estimates par sujet (machine learning trend)
