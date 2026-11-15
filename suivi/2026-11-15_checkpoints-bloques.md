# Suivi performance — 2026-11-15 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` → HTTP 401 `disabled_client: The OAuth client was disabled.` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` **et** `YOUTUBE_REFRESH_TOKEN`.
- 6e run quotidien consécutif avec la même panne (10/11 → 15/11), active depuis ~26/10. Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` présente mais vide (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-15 ~20h UTC ±12h → 30j = publications du 16/10 ~20h UTC au 17/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `GNjWp0NpfEM` | Google Lance Deep Review, 9 Erreurs Sur 10 Repérées | Short | 2026-10-17T02:19:43Z | 30j | Bloqué (48h déjà traité : `suivi/2026-10-18_GNjWp0NpfEM_48h.md`) |
| `G510CjrlUPQ` | Google Trouve Enfin Le Bon Jeu Pour Toi | Short | 2026-10-17T02:16:01Z | 30j | Bloqué (48h déjà traité : `suivi/2026-10-18_G510CjrlUPQ_48h.md`) |
| `_lvEGjbAF1c` | MAI-Base-2 : Microsoft Affirme Avoir Battu OpenAI Avec 4x Moins De Calcul | Longue | 2026-10-17T02:34:33Z | 30j | Bloqué (24h déjà traité : `suivi/2026-10-18__lvEGjbAF1c_24h.md`) |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 14/11, 13/11 ou 08/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **18 vidéos** (12/10 → 17/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 17/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10. Le même client OAuth bloque aussi l'upload (`YOUTUBE_REFRESH_TOKEN`).
