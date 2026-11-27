# Suivi performance — 2026-11-27 (run quotidien SOP 07/08)

**Statut : Aucun checkpoint aujourd'hui (selon le log de production). Aucune analyse, aucun score, aucune conclusion.**

## Vérification OAuth (~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- **18e run quotidien consécutif** avec la même panne (10/11 → 27/11), active depuis ~26/10 (~32 jours).
- Aucun autre token/clé utilisé (prompt de suivi limité à `YOUTUBE_ANALYTICS_REFRESH_TOKEN`).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-27 ~20h UTC ±12h.
- 30j (28/10), 7j (20/11), 48h (25/11), 24h (26/11) : aucune publication consignée. Dernière publication consignée : 26/10 (32 jours sans production).
- Non confirmable via `playlistItems` tant que l'OAuth est hors service.

## Rattrapage
Backlog inchangé : **44 vidéos** au checkpoint 30j (12/10 → 26/10), récupérables via requêtes Analytics historiques dès rétablissement du client OAuth. Priorité : 30j puis 7j ; `PatL4gDO1C4` en tête.

## Action requise (humain)
1. Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si recréé).
2. Tant qu'aucune vidéo n'est publiée, cette routine n'a plus de checkpoint à traiter : envisager de la suspendre jusqu'à reprise de la production / de l'OAuth.
