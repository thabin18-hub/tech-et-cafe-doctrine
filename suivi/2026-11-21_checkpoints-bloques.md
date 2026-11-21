# Suivi performance — 2026-11-21 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- **12e run quotidien consécutif** avec la même panne (10/11 → 21/11), active depuis ~26/10 (~26 jours). Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` toujours vide (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-21 ~20h UTC ±12h → 30j = publications du 22/10 ~08h UTC au 23/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `so9qNHaYRyA` | D'Anciens De Google DeepMind Défient La Chine Sur L'IA | Short | 2026-10-23T02:39:14Z | 30j | Bloqué |
| `axlnAGh2IeU` | Walmart Laisse 3 IA Faire Tes Courses À Ta Place | Short | non consigné (run ~02h06-02h55 UTC le 23/10) | 30j | Bloqué |

- Aucune vidéo longue consignée le 23/10 (seulement 2 shorts) : backlog du jour = 2 vidéos, pas 3.
- `publishedAt` exact de `axlnAGh2IeU` absent du log de production (même défaut que `9uYYwwZNPmU`, cf. 11/11) ; la fenêtre du run le place sans ambiguïté dans le checkpoint 30j d'aujourd'hui.
- 24h / 48h / 7j : aucune vidéo consignée publiée le 20/11, 19/11 ou 14/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **35 vidéos** (12/10 → 23/10), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 24/10 au 26/10 (dont les 30j dus du 22/11 au 25/11). Priorité : 30j, puis 7j ; `PatL4gDO1C4` (échéance datée 11/12/2026) en tête.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10 (26 jours).
