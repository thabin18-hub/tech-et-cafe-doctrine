# Suivi performance — 2026-11-14 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible — 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` → HTTP 401 `disabled_client: The OAuth client was disabled.` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` **et** `YOUTUBE_REFRESH_TOKEN`.
- 5e run quotidien consécutif avec la même panne (10/11 → 14/11), active depuis ~26/10. Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` présente mais vide (longueur 0, vérifié sans afficher de valeur) ; appel Data API → 403.

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-14 ~20h UTC ±12h → 30j = publications du 15/10 08h UTC au 16/10 08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `-ThJv5n1TZ4` | Samsung Rend Ta Maison 30% Plus Rapide | Short | 2026-10-16 ~02h UTC | 30j | Bloqué (48h déjà traité : `suivi/2026-10-18_-ThJv5n1TZ4_48h.md`) |
| `TR8hnU-j7UM` | Google Lance Foresight : Tes Réunions Ne Quittent Jamais Ton Mac | Short | 2026-10-16 ~02h30 UTC | 30j | Bloqué (aucun checkpoint antérieur consigné) |
| `yeLqHbbg7Kc` | Meta Muse Spark Open : L'IA De 816 Milliards De Paramètres Qui Tourne Sur Un Mac | Longue | 2026-10-16 ~02h35 UTC | 30j | Bloqué (48h déjà traité : `suivi/2026-10-18_yeLqHbbg7Kc_48h.md`) |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 13/11, 12/11 ou 07/11 (dernière publication consignée : `vOyjauSfD3I`, 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload ; si jamais passées en public, métriques 30j quasi nulles — à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **15 vidéos** (12/10 → 16/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 16/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si client recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10 — le même client OAuth bloque aussi l'upload (`YOUTUBE_REFRESH_TOKEN`).
