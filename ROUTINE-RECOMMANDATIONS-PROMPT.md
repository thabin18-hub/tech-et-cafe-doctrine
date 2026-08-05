# Prompt Routine Recommandations Analytiques
## Exécution: Lundi 9h GMT (après rapport dimanche 23:59)

### Mission
Lire le rapport analytique de dimanche, extraire patterns data-driven, générer directives YAML pour la semaine de production.

---

## Étapes (dans l'ordre)

### 1. LIRE le rapport analytique
- Cherche le fichier le plus récent dans: `livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/rapports/`
- Format: `rapport-YYYY-MM-DD.docx` OU `.pdf` (préférer .docx s'il existe)
- Extrait les sections clés:
  - Nombre vidéos publiées semaine
  - Vues totales et moyennes par vidéo
  - Retention moyenne %
  - CPM moyen
  - RPM moyen
  - Abonnés gagnés
  - Watch time total (heures)
  - Progression vers 1000 abos (pour YPP)
  - Notes analytiques/patterns détectés

### 2. EXTRAIRE insights clés

**Performance par sujet** (si présent dans rapport):
- Quels sujets ont meilleure retention ? (ex: "AI security" +8% vs baseline)
- Quels sujets ont meilleur CPM ? (ex: "fondateurs tech" 2.1 CPM)
- Quels sujets ont pire performance ? (noter pour eviter)

**Performance par format**:
- Durée optimale (ex: "50s retention +4% vs >60s")
- Hook timing (ex: "0-3s surprise beats curiosity by 8%")
- Visual patterns (ex: "B-roll change every 5-7s +6% engagement")

**Performance par affiliation**:
- Quelles affiliations ont marché ? (conversions, CTR)
- Lesquelles intégrer davantage ?

**Trends détectés**:
- Patterns rétention/CPM
- Anomalies (video outlier haute/basse perf)
- Trajectoire: monte/baisse/stable

### 3. IDENTIFIER patterns généralisables

Cherche des **patterns actionnables** (pas des observations à usage unique):
- "Hooks surprise > curiosity" (réutilisable chaque semaine)
- "Duration 50s sweet spot" (recommandation durable)
- "AI security angle toujours CPM 2.1+" (privilégier ce type de contenu)

### 4. GENERER directives YAML

Crée fichier: `directives-production-YYYY-MM-DD.yaml` (où YYYY-MM-DD = lundi de la semaine)

**Structure obligatoire**:

```yaml
semaine_du: "2026-08-03"

data_semaine_precedente:
  period: "27/07 - 02/08"
  videos_publiees: 8
  vues_totales: 12400
  vues_moyennes_par_video: 1550
  retention_moyenne: "36.2%"
  cpm_moyen: "1.62"
  rpm_moyen: "0.58"
  abonnes_gagnes: 47
  progression_monetisation: "47/1000 abos (4.7%)"
  watch_time_hours: 74.4

angles_privilegier:
  - "Sujet 1 (raison data: retention +X%, CPM Y)"
  - "Sujet 2 (raison data: trending, stable CPM)"

angles_eviter:
  - "Sujet 1 (raison: CPM bas, retention -X%)"

parametres:
  duree_cible: "48-55s"
  duree_optimal: "50s"
  raison_duree: "Evidence from data"
  
  hook_strategy: "Description"
  hook_timing: "0-3s"
  hook_patterns_best:
    - "Pattern 1"
    - "Pattern 2"
  
  retention_target: "40%"
  retention_actual: "36.2%"
  
  cpm_target_min: "1.8"
  cpm_actual: "1.62"
  cpm_delta: "+11% needed"

affiliation_priority:
  - name: "Affiliation 1"
    cpm_boost: "+0.3"
    conversion_rate: "3.2%"
    note: "Why it worked"

patterns:
  - "Pattern 1: evidence + % impact"
  - "Pattern 2: evidence + % impact"

trends_emerging:
  - "Trend 1 (source: Google Trends / HN / Reddit)"
  - "Trend 2"

backlog_fallback:
  - "Backlog concept 1 (ref: backlog-evergreen/EG-001)"
  - "Backlog concept 2"
  note: "Use if < 2 trends solides"

qualite:
  son_design: "whoosh, silence, beat (avec secondes)"
  transitions: "fade (60ms), zoom (1.2x), pan"
  text_on_screen: "max 1 ligne, sans-serif bold"

seo:
  keywords_priority: ["keyword1", "keyword2"]
  description_length: "150-200 chars"
  tags_count: "7-10"
  hashtags: "#IA #Tech #Automation"

notes: |
  Résumé libre de la semaine + recommandations stratégiques.
  Inclure: challenge/opportunity, solution proposée, priorisation pour production.

metadata:
  version: "1.0"
  generated_at: "2026-08-03T09:00:00Z"
  algorithm: "analytique data-driven + trends"
  next_update: "2026-08-10T09:00:00Z"
```

### 5. SAUVEGARDER le fichier

- Chemin: `livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/directives/directives-production-YYYY-MM-DD.yaml`
- Format: YAML lisible, 100+ lignes minimum (assez détaillé pour aider production)
- Validation: fichier bien formé, parseable par routine production

### 6. METTRE A JOUR PRODUCTION-CONFIG.yaml (optionnel)

Si tu veux que les directives soient lues automatiquement:
- Ajoute section dans PRODUCTION-CONFIG.yaml:
  ```yaml
  directives_hebdomadaire:
    chemin: "directives/directives-production-YYYY-MM-DD.yaml"
    override_defaults: true
  ```

---

## Règles strictes

### Base decisions sur DATA REELLE
- Pas d'intuition, **données ou evidence uniquement**
- Cite les chiffres (ex: "retention 36.2%" pas "plutôt mauvais")

### Si données insuffisantes
- < 3 videos publiées: "Données insuffisantes, use default framework"
- < 24h recul: "Rapport incomplet, use default framework"
- Rapport manquant: Check le dossier `rapports/`, si vide, abort avec message clair

### Directives ACTIONNABLES
- Pas "Fais mieux"
- Oui "Privilégier AI security (CPM stable 2.1+)"
- Oui "Durée cible 50s (abandon rates -30% vs >60s)"
- Oui "Hook 0-3s surprise strategy"

### Format YAML
- Valide et parseable (pas de typos syntaxe)
- Lisible par scripts Python/Go
- Commentaires clairs (Pourquoi cette recommandation?)

---

## Test de succès

✅ Routine exécute lundi 9h GMT
✅ Lit rapport dimanche (format .docx/.pdf)
✅ Génère directives-production-YYYY-MM-DD.yaml
✅ Fichier dans dossier correct
✅ Format YAML valide
✅ Recommandations data-driven (cités sources/chiffres)
✅ Routine production peut lire le fichier et adapter production

---

## Notes pour l'agent Cloud

- Temps estimé: 5-10 min (lecture rapport + analysis + écriture YAML)
- Dépendances: Rapport analytique doit exister (dimanche 23:59 GMT doit avoir tourné)
- Fallback: Si rapport absent, log "Waiting for report" et retry, ou use default framework
- Logs: Affiche "Recommandations générées: directives-production-YYYY-MM-DD.yaml" en fin
