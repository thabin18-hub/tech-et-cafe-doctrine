# Suivi performance — 2026-11-10 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible — 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h05 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` :
  - `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
  - `YOUTUBE_REFRESH_TOKEN` → HTTP 401 `disabled_client` (même erreur, même client).
- Repli lecture publique (Data API `playlistItems` par clé API) impossible : `YOUTUBE_API_KEY` et `GOOGLE_API_KEY` sont **vides** dans l'environnement (HTTP 403).
- Panne identique à celle signalée dans les rapports hebdo du 02/11 et du 09/11 (début ~26/10) — **4e semaine**, non résolue.

## Checkpoints dus aujourd'hui (identifiés depuis les `publishedAt` consignés dans BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre de run : 2026-11-10 ~20h UTC, tolérance ±12h.

| video_id | Titre | publishedAt | Checkpoint | Statut |
|---|---|---|---|---|
| `uF60ehACm-Y` | OpenAI Retire 3 Preuves Maths Pour Une Erreur De Signe (Short) | 2026-10-12T02:18:58Z | 30j | Bloqué (7j déjà traité : `suivi/2026-10-18_uF60ehACm-Y_7j.md`) |
| `zKqJBLfZYJ0` | Meta Muse Arrive Sur iPad : 6,6 Millions D'Installations En 1 Mois (Short) | 2026-10-12T02:20:15Z | 30j | Bloqué |
| `zwDm08YudtM` | Meta Dévoile Personal Agent Protocol : Ton IA Va Faire Tes Achats (longue) | 2026-10-12T02:35:24Z | 30j | Bloqué |

- 24h / 48h / 7j : aucune vidéo connue publiée le 09/11, 08/11 ou 03/11 (dernière publication consignée : `vOyjauSfD3I`, 26/10 ; rapport hebdo du 09/11 : 0 vidéo produite sur 02/11-08/11). Non vérifiable via API ce run.

## Rattrapage possible (à faire dès rétablissement du client OAuth)
YouTube Analytics accepte des requêtes historiques (`startDate`=publication, `endDate`=publication+N jours) : les checkpoints manqués ne sont **pas perdus**, ils peuvent être recalculés a posteriori avec la fenêtre exacte.
Backlog connu (aucun rapport `suivi/` depuis le 18/10) : checkpoints 24h/48h/7j/30j de toutes les vidéos publiées du 12/10 au 26/10 (≈40 vidéos listées dans BASE-DE-CONNAISSANCES.md, dont 3 vidéos longues dues aujourd'hui à 30j ci-dessus). Prioriser au rattrapage : les 30j (valeur long terme) puis les 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si client recréé), et renseigner `YOUTUBE_API_KEY` dans l'environnement pour permettre au moins un repli lecture publique.
