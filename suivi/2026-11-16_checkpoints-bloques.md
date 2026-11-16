# Suivi performance — 2026-11-16 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h03 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` → HTTP 401 `disabled_client: The OAuth client was disabled.` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` **et** `YOUTUBE_REFRESH_TOKEN`.
- 7e run quotidien consécutif avec la même panne (10/11 → 16/11), active depuis ~26/10. Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` et `GOOGLE_API_KEY` présentes mais vides (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-16 ~20h UTC ±12h → 30j = publications du 17/10 ~08h UTC au 18/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `a6m_SLU0t1c` | OpenAI Lance ChatGPT Slides : L'IA Fait Tes Diapos Avec Toi | Short | 2026-10-18 ~02h10-02h20 UTC (horodatage exact non consigné) | 30j | Bloqué |
| `ULvk2gUD9qE` | Microsoft : Son IA Repère Les Pièges Dans Tes Contrats | Short | 2026-10-18 ~02h20-02h40 UTC (horodatage exact non consigné) | 30j | Bloqué |
| `h9D3TlUiTk8` | Meta Muse Spark Open : L'IA Gratuite Qui Tourne Sur Ton Mac | Longue | 2026-10-18T02:35:42Z | 30j | Bloqué |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 15/11, 14/11 ou 09/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **21 vidéos** (12/10 → 18/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 18/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10 — le même client OAuth bloque aussi l'upload (`YOUTUBE_REFRESH_TOKEN`).
