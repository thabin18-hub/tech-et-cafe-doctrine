# Directives Production Hebdomadaires

Auto-générées chaque lundi 9h GMT par routine analytique.

## Format

Chaque fichier `directives-production-YYYY-MM-DD.yaml` contient:

```yaml
semaine_du: "2026-08-05"
data_semaine_precedente:
  videos_publiees: 10
  vues_totales: 45000
  retention_moyenne: "38%"
  cpm_moyen: "1.75"
  abonnes_gagnes: 120
  progression_monetisation: "640/1000 abos (64%)"

angles_privilegier:
  - "IA agents autonomes"
  - "AI security"
  - "Breakthrough research"

angles_eviter:
  - "Crypto"
  - "Memes tech"

parametres:
  duree_cible: "48-55s"
  hook_strategy: "surprise > curiosity"
  retention_target: "42%"
  cpm_target_min: "1.8"

affiliation_priority:
  - "online courses AI"
  - "tech newsletters"

notes: |
  Semaine passée: hooks surprise marchaient 2x mieux
  Duration 50s optimal (plus court perd retention, plus long abandonment)
  Sujets AI security stable 2.2 CPM
```

## Utilisation

La routine production lit le fichier directives de la semaine courante et adapte:
- Choix des sujets (veille priorisée par angles privilégiés)
- Duration cible du script
- Hook strategy
- Affiliation intégrée

Si pas de fichier directives, use default framework (voir PRODUCTION-CONFIG.yaml).
