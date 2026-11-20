# Suivi performance — 2026-11-20 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- `YOUTUBE_REFRESH_TOKEN` non testé (hors périmètre de la routine de suivi ; même client OAuth, présumé bloqué).
- **11e run quotidien consécutif** avec la même panne (10/11 → 20/11), active depuis ~26/10 (~25 jours). Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` toujours vide (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-20 ~20h UTC ±12h → 30j = publications du 21/10 ~08h UTC au 22/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `Cc92WIRYVEs` | ElevenLabs Architect : Ton Agent Vocal Se Configure Tout Seul | Short | 2026-10-22T02:20:18Z | 30j | Bloqué |
| `GGdUswq2Dhs` | GM : Une IA Remplace 5 Applications D'un Coup | Short | 2026-10-22T02:31:11Z | 30j | Bloqué |
| `PatL4gDO1C4` | ChatGPT Supprime Les GPT Personnalisés Le 11 Décembre 2026 | Longue | 2026-10-22T02:35:48Z | 30j | Bloqué |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 19/11, 18/11 ou 13/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.
- Point de vigilance (pour le rattrapage) : `PatL4gDO1C4` porte sur une échéance datée (11/12/2026) — sa valeur long terme dépend de cette date ; à analyser en priorité dès rétablissement pour en tirer un enseignement avant l'échéance.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **33 vidéos** (12/10 → 22/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 23/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10.
