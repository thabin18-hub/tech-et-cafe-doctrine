# Suivi performance — 2026-11-25 (run quotidien SOP 07/08)

**Statut : Aucun checkpoint aujourd'hui (selon le log de production). Aucune analyse, aucun score, aucune conclusion.**

## Vérification OAuth (~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- **16e run quotidien consécutif** avec la même panne (10/11 → 25/11), active depuis ~26/10 (~30 jours).
- Repli `YOUTUBE_API_KEY` non utilisé (non autorisé par le prompt de suivi, et ne fournit pas les métriques Analytics).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-25 ~20h UTC ±12h.
- 30j → publications du 26/10 ~08h au 27/10 ~08h UTC : **aucune vidéo consignée** (les 3 vidéos du 26/10 — `vOyjauSfD3I`, `vUrGqeGLQAE`, `AnllqK0aJgo` — ont été comptées au checkpoint 30j du 24/11 ; si l'un des shorts a en réalité été publié après 08h UTC le 26/10, son 30j tomberait aujourd'hui — non vérifiable sans API, couvert par le rattrapage).
- 7j (18/11), 48h (23/11), 24h (24/11) : aucune publication consignée. Dernière publication consignée : 26/10 (30 jours sans production).
- Non confirmable via `playlistItems` tant que l'OAuth est hors service.

## Rattrapage
Backlog inchangé : **44 vidéos** au checkpoint 30j (12/10 → 26/10), récupérables via requêtes Analytics historiques dès rétablissement du client OAuth. Priorité : 30j puis 7j ; `PatL4gDO1C4` en tête.

## Action requise (humain)
1. Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si recréé).
2. Constat : aucune production consignée depuis le 26/10 — tant que rien n'est publié, cette routine n'aura plus de checkpoint à traiter.
