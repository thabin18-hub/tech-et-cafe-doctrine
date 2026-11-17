# Suivi performance — 2026-11-17 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h03 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` → HTTP 401 `disabled_client: The OAuth client was disabled.` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` **et** `YOUTUBE_REFRESH_TOKEN`.
- **8e run quotidien consécutif** avec la même panne (10/11 → 17/11), active depuis ~26/10. Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` et `GOOGLE_API_KEY` présentes mais vides (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-17 ~20h UTC ±12h → 30j = publications du 18/10 ~08h UTC au 19/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `SaBQ9a9Qkzs` | Black Forest Labs : Son IA D'Images Gratuite Sous 5 Millions De Dollars | Short | 2026-10-19 ~02h-03h UTC (horodatage exact non consigné) | 30j | Bloqué |
| `r08TqBGga6w` | Kling 4.0 : Son IA Vidéo Fait 30 Secondes En 4K, Pour Tous | Short | 2026-10-19T02:31:56Z | 30j | Bloqué |
| `m08SOAsYR6U` | ChatGPT Contrôle Chrome : Il Remplit Tes Formulaires Pour Toi | Longue | 2026-10-19 ~02h-03h UTC (horodatage exact non consigné) | 30j | Bloqué |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 16/11, 15/11 ou 10/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **24 vidéos** (12/10 → 19/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 19/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10 — le même client OAuth bloque aussi l'upload (`YOUTUBE_REFRESH_TOKEN`).
