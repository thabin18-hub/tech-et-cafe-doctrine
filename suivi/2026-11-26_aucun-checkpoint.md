# Suivi performance — 2026-11-26 (run quotidien SOP 07/08)

**Statut : Aucun checkpoint aujourd'hui (selon le log de production). Aucune analyse, aucun score, aucune conclusion.**

## Vérification OAuth (~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- **17e run quotidien consécutif** avec la même panne (10/11 → 26/11), active depuis ~26/10 (~31 jours).
- Aucun autre token/clé utilisé (prompt de suivi limité à `YOUTUBE_ANALYTICS_REFRESH_TOKEN`).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-26 ~20h UTC ±12h.
- 30j → publications du 27/10 ~08h au 28/10 ~08h UTC : aucune vidéo consignée.
- 7j (19/11), 48h (24/11), 24h (25/11) : aucune publication consignée. Dernière publication consignée : 26/10 (31 jours sans production).
- Non confirmable via `playlistItems` tant que l'OAuth est hors service.
- Les 3 vidéos du 26/10 (`vOyjauSfD3I`, `vUrGqeGLQAE`, `AnllqK0aJgo`) ont désormais toutes dépassé la fenêtre 30j : **plus aucun checkpoint n'est attendu** tant qu'aucune nouvelle vidéo n'est publiée.

## Rattrapage
Backlog inchangé : **44 vidéos** au checkpoint 30j (12/10 → 26/10), récupérables via requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) dès rétablissement du client OAuth. Priorité : 30j puis 7j ; `PatL4gDO1C4` en tête.

## Action requise (humain)
1. Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si recréé).
2. Aucune production consignée depuis le 26/10 : tant que rien n'est publié, cette routine n'a plus de checkpoint à traiter (envisager de la suspendre jusqu'à reprise de la production / de l'OAuth).
