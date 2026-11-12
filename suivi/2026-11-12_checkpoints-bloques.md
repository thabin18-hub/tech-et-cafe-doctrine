# Suivi performance — 2026-11-12 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible — 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h05 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` et `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- 3e run quotidien consécutif avec la même panne (10/11, 11/11, 12/11), active depuis ~26/10. Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` et `GOOGLE_API_KEY` toujours vides dans l'environnement (re-vérifié ce run).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre de run : 2026-11-12 ~20h UTC, tolérance ±12h → 30j = publication du 13/10 08h UTC au 14/10 08h UTC (les vidéos du 13/10 ~02h ont été rattachées au run d'hier).

| video_id | Titre | Format | publishedAt | Checkpoint | Statut |
|---|---|---|---|---|---|
| `ZENA7xiDtFQ` | Alibaba Rend Son IA De Création D'Images 5 Fois Plus Rapide | Short | 2026-10-14T02:16:38Z | 30j | Bloqué (48h déjà traité : `suivi/2026-10-15_ZENA7xiDtFQ_48h.md`) |
| `kplT7b4e5r8` | OpenAI : Son IA A Triché Pour Forcer Son Propre Redémarrage | Short | 2026-10-14T02:22:06Z | 30j | Bloqué (48h déjà traité : `suivi/2026-10-15_kplT7b4e5r8_48h.md`) |
| `Uv8I-xAATck` | Apple HomeView : Son Écran Connecté, Mais Pas Sûr Pour L'Europe | Longue | 2026-10-14T02:37:48Z | 30j | Bloqué (24h déjà traité : `suivi/2026-10-15_Uv8I-xAATck_24h.md`) |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 11/11, 10/11 ou 05/11 (dernière publication consignée : `vOyjauSfD3I`, 26/10). Non vérifiable via API ce run.
- Rappel : ces vidéos sont consignées `privacyStatus private` à l'upload ; si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles — à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : 9 vidéos (3 du 12/10, 3 du 13/10, 3 du 14/10), plus l'ensemble des checkpoints 24h/48h/7j/30j non traités des vidéos du 15/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si client recréé) et renseigner `YOUTUBE_API_KEY` pour un repli lecture publique.
