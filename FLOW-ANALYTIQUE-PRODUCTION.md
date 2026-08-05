# Flow Analytique → Production
## Comment les routines cloud s'enchaînent pour la chaîne YouTube

---

## 🔁 Cycle hebdomadaire

```
┌─────────────────────────────────────────────────────────────────┐
│                    SEMAINE DE PRODUCTION                        │
│                                                                 │
│  Lundi          Mardi-Jeudi        Vendredi        Dimanche     │
│  ┌──────┐       ┌──────┐           ┌──────┐        ┌──────┐    │
│  │09h00 │       │10h00 │ (daily)   │10h00 │        │23h59 │    │
│  │ RECO │  ──→  │ PROD │  ──→  ─→  │ PROD │  ──→   │REPORT│    │
│  └──────┘       └──────┘           └──────┘        └──────┘    │
│                                                                 │
│  Génère        2 shorts/day      2 shorts/day    Analyse      │
│  directives   (privé YouTube)  (privé YouTube)   semaine      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
         ↑                                               │
         └───────────────── FEEDBACK LOOP ─────────────┘
          (directives lundi = basée sur report dimanche)
```

---

## 🔄 Détail: Flux Dimanche → Lundi → Mardi+

### 📊 DIMANCHE 23:59 GMT - RAPPORT ANALYTIQUE

**Routine cloud:** `trig_0164VZ1y6g5EpNwEkfTj2mQG`

**Ce qui se passe:**
1. Récupère YouTube Analytics API → stats vidéos publiées semaine (lun-dim)
2. Agrège données:
   - Nombre vidéos publiées
   - Vues totales + moyennes
   - Retention moyenne %
   - CPM moyen
   - RPM moyen
   - Abonnés gagnés
   - Watch time total
3. Génère 3 formats:
   - Word `.docx` (texte + chiffres)
   - PDF `.pdf` (version lecture)
   - PowerPoint `.pptx` (avec graphiques)
4. **Sauvegarde:** `livrables/youtube/.../rapports/rapport-2026-08-02.{docx,pdf,pptx}`

**Format fichier:** `rapport-YYYY-MM-DD.{docx,pdf,pptx}`  
(YYYY-MM-DD = dimanche de la semaine qui se termine)

**Exemple contenu:**
```
Rapport Tech & Café - Semaine 27/07 - 02/08

📊 Stats Globales
- Videos publiées: 8
- Vues totales: 12,400
- Vues moyennes/video: 1,550
- Retention moyenne: 36.2%
- CPM moyen: 1.62
- Abonnés gagnés: 47
- Watch time: 74.4 heures
- Progression YPP: 47/1000 abos (4.7%)

🎯 Patterns Détectés
- Hook surprise +8% retention vs curiosity
- Duration 50s optimal (abandon -30% vs >60s)
- Sujets AI security stable CPM 2.1+
- Affiliations tech courses conversion 3.2%

⚠️ Points Faibles
- Crypto/blockchain CPM très bas (0.9)
- Memes tech retention -12%

✅ Recommandations
1. Privilégier AI agents + security angles
2. Durée cible 50s (range 48-55s)
3. Hooks surprise 0-3s
4. Intégrer 1 affiliation/video naturelle
5. Target CPM 1.8+ (semaine prochaine)
```

**Dépendance:** YouTube Data API v3 + YouTube Analytics API + tokens OAuth valides

---

### 📋 LUNDI 9h00 GMT - RECOMMANDATIONS ANALYTIQUES

**Routine cloud:** `trig_01QgtHQfuS4GYWVGBZ3jA8M4`

**Ce qui se passe:**
1. Lit le rapport du dimanche 23:59 (format docx/pdf)
2. Parse et extrait insights clés
3. Identifie patterns généralisables (durée, hook, sujets, CPM)
4. Génère fichier **directives-production-YYYY-MM-DD.yaml**
5. **Sauvegarde:** `livrables/youtube/.../directives/directives-production-2026-08-03.yaml`

**Format fichier:** `directives-production-YYYY-MM-DD.yaml`  
(YYYY-MM-DD = lundi de la semaine)

**Contenu du YAML** (voir template en détail):
```yaml
semaine_du: "2026-08-03"
data_semaine_precedente: [chiffres du rapport]
angles_privilegier:
  - "IA agents autonomes (retention +8%, CPM 2.1)"
  - "AI security (stable CPM 2.2)"
angles_eviter:
  - "Crypto/blockchain"
parametres:
  duree_cible: "48-55s"
  hook_strategy: "surprise + contre-intuitif"
  retention_target: "40%"
  cpm_target_min: "1.8"
affiliation_priority: [...]
patterns: [...]
notes: "Strategy pour semaine: ..."
```

**Dépendance:** Rapport du dimanche doit exister

**Sortie:** Fichier YAML parseable + lisible = directif production

---

### 🎬 LUNDI 10h00 GMT - PRODUCTION LIRE DIRECTIVES

**Routine cloud:** `trig_01QTPw2RxoroMRcD4E3FthPn`

**Ce qui se passe (amélioration 01/08):**

1. **STEP 0 - Charger directives hebdo** ← NOUVEAU
   ```
   if fichier directives-production-2026-08-03.yaml existe:
       load config from YAML
   else:
       load config from PRODUCTION-CONFIG.yaml (default)
   ```

2. **STEP 1 - Prioriser sujets** (avec directives)
   ```
   Scrape trends (Google Trends, Reddit, HN)
   Filter par angles_privilegier (ex: AI agents, security)
   Estime CPM par sujet (ex: AI security = 2.2)
   Rank par: (trend_velocity × CPM_estimate) = priorité
   Select TOP 2 sujets rentables
   ```

3. **STEP 2-6 - Framework 6 étapes** (adapté directives)
   - Titre + miniature (5 options)
   - Script court (hook 0-3s surprise, corps 40s, CTA 5s)
   - Découpe technique (timing/visuels/son)
   - SEO (keywords prioritaires du YAML)
   - Affiliation (priority du YAML)
   - Metadata (CPM estimate, durée réelle)

4. **STEP 7 - Upload privé YouTube**
   - 2 vidéos uploadées en privé
   - Fichiers métadonnées stockés: `livrables/youtube/.../videos_prod/2026-08-03/`

**Logs production (exemple avec directives):**
```
[03/08 10:00] Loading config...
[03/08 10:01] Directives found: directives-production-2026-08-03.yaml ✓
[03/08 10:02] Angles privilégier: AI agents autonomes, AI security, Breakthrough research
[03/08 10:03] Angles éviter: Crypto/blockchain, Memes tech
[03/08 10:04] Scraping trends...
[03/08 10:06] Top 2 candidates: 
  - Claude 3.5 Sonnet (CPM estimate 2.1, velocity high)
  - EU AI Act enforcement (CPM estimate 2.3, trending)
[03/08 10:10] Video 1: "Claude 3.5 Sonnet lancements" - Duration: 51s - CPM: 2.1
[03/08 10:10] Video 2: "AI regulation fines Europe" - Duration: 49s - CPM: 2.3
[03/08 10:20] Uploading to YouTube...
[03/08 10:25] Done: 2 videos uploaded (private)
```

**Résultat:** 2 shorts générés par jour × 5 jours = 10 shorts/semaine  
(Tu valides/publies les 2 de chaque jour)

---

## 🔐 Configuration Cloud

Les 3 routines cloud sont configurées dans Anthropic:

| Routine | ID Cloud | Cron | Fonction |
|---------|----------|------|----------|
| **Rapport** | `trig_0164VZ1y6g5EpNwEkfTj2mQG` | `59 23 * * 0` (dim 23h59) | YouTube Analytics → docx/pdf/pptx |
| **Recommandations** | `trig_01QgtHQfuS4GYWVGBZ3jA8M4` | `0 9 * * 1` (lun 9h00) | Rapport → directives YAML |
| **Production** | `trig_01QTPw2RxoroMRcD4E3FthPn` | `0 10 * * *` (daily 10h) | Directives + trends → 2 shorts |

---

## 📁 Fichiers stockés

```
livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/
│
├── rapports/                          ← Générés dimanche 23h59
│   ├── rapport-2026-08-02.docx
│   ├── rapport-2026-08-02.pdf
│   └── rapport-2026-08-02.pptx
│
├── directives/                        ← Générés lundi 9h00
│   ├── directives-production-2026-08-03.yaml
│   ├── directives-production-2026-08-10.yaml
│   └── README.md (template)
│
├── videos_prod/                       ← Générés lundi-vendredi 10h
│   ├── 2026-08-03/
│   │   ├── video-1-metadata.json
│   │   ├── video-1-script.txt
│   │   └── video-1-cutting-table.csv
│   ├── 2026-08-04/
│   └── ...
│
├── PRODUCTION-CONFIG.yaml             ← Config centrale + defaults
├── ROUTINE-RECOMMANDATIONS-PROMPT.md  ← Prompt routine analytique
└── VALIDATION-ROUTINE-ANALYTIQUE.md   ← Checklist validation
```

---

## ✅ Validation Timeline

**Samedi 02/08 ou dimanche 03/08:**
- [ ] Rapport du 02/08 existe (`.docx`, `.pdf`, `.pptx`)
- [ ] Contenu: 8-10 vidéos, chiffres remplis, patterns détectés

**Lundi 03/08 après 9h30:**
- [ ] Directives du 03/08 existe (`.yaml`)
- [ ] YAML valide + parseable
- [ ] Contenu: angles, durée, CPM, patterns, notes

**Lundi 03/08 après 10h30:**
- [ ] Production a chargé directives (logs mentionnent fichier)
- [ ] 2 shorts générés pour 03/08
- [ ] Logs montrent sujets ∈ angles_privilegier
- [ ] Durée ~50s, CPM estimate ≥ 1.8

**Si tout OK:**
- Pipeline analytique fonctionne
- Directives influencent production quotidienne
- Feedback loop fermée dimanche → lundi → mardi+

---

## 🎯 Impact attendu

### Avant (sans directives)
- Production chaque jour sans insights data
- Sujets = actu brute
- CPM moyen ~1.5
- Pas de priorisation rentabilité

### Après (avec directives)
- Production = data-driven (dimanche → lundi)
- Sujets priorisés par CPM + trend velocity
- CPM moyen +20-30% (estimé)
- Angles rentables toujours priorisés

---

## 🔧 Ajustements possibles

Si une semaine est déçue (CPM bas, retention baisse):
1. Lire le rapport du dimanche
2. Identifier le pattern manquant
3. Améliorer prompt ROUTINE-RECOMMANDATIONS-PROMPT.md
4. La routine génère directives améliorées lundi suivant

Ex: "Si CPM bas semaine précédente, augmenter poids AI security angle"

---

## 📞 Troubleshooting rapide

| Problème | Cause probable | Fix |
|----------|-----------------|-----|
| Pas de rapport dimanche | YouTube Analytics API fail | Vérifier token OAuth + permissions |
| Pas de directives lundi | Rapport absent | Attend rapport + retry routine |
| Production ignore directives | Config path faux | Vérifier `PRODUCTION-CONFIG.yaml` path |
| Directives YAML mal formé | Bug routine syntaxe | Check logs cloud, fix prompt |
| Sujets ne matchent pas directives | Production chargé default au lieu de YAML | Vérifier fallback logic |

---

## 🚀 Prochaines évolutions possibles

- [ ] A/B testing miniatures (config préparé, ready for activation)
- [ ] Machine learning CPM estimates (plus précis que estimates manuels)
- [ ] Backlog enrichissement automatique (meilleurs concepts chaque semaine)
- [ ] Dashboards Grafana (trend charts semaine à semaine)
- [ ] Notifications Slack si CPM baisse (alertes thresholds)

---

**Dernière mise à jour:** 01/08/2026 (validation + amélioration)  
**Statut:** ✅ Prêt pour test 02-03/08  
**Ressources:** ROUTINE-RECOMMANDATIONS-PROMPT.md + directives-production-2026-08-03.yaml (template) + VALIDATION-ROUTINE-ANALYTIQUE.md
