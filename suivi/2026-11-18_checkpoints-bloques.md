# Suivi performance — 2026-11-18 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h03 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- `YOUTUBE_REFRESH_TOKEN` non testé ce run (hors périmètre de la routine de suivi ; même client OAuth, donc présumé bloqué comme les 8 runs précédents).
- **9e run quotidien consécutif** avec la même panne (10/11 → 18/11), active depuis ~26/10. Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` présente mais vide (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-18 ~20h UTC ±12h → 30j = publications du 19/10 ~08h UTC au 20/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `idv58KSiZ78` | Amazon Défie Nvidia : -70% Sur Le Prix De L'IA Vocale | Short | 2026-10-20 ~02h16-02h25 UTC (horodatage exact non consigné) | 30j | Bloqué |
| `15V_xb-9wqI` | xAI Rend La Vidéo IA 4 Fois Moins Chère | Short | 2026-10-20 ~02h-03h UTC (horodatage exact non consigné) | 30j | Bloqué |
| `xCR5nGjhC9E` | Grok Voice 3.0 : L'IA Vocale De xAI Qui Remplace Les Centres D'Appels | Longue | 2026-10-20T02:31:15Z | 30j | Bloqué |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 17/11, 16/11 ou 11/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **27 vidéos** (12/10 → 20/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 21/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10.
