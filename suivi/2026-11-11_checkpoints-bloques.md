# Suivi performance — 2026-11-11 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible — 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h05 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` et `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- Panne identique à celle des 10/11 (`suivi/2026-11-10_checkpoints-bloques.md`) et des rapports hebdo des 02/11 et 09/11 (début ~26/10). Non résolue.
- Repli lecture publique (Data API par clé) non retenté ce run : `YOUTUBE_API_KEY`/`GOOGLE_API_KEY` constatées vides le 10/11.

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre de run : 2026-11-11 ~20h UTC, tolérance ±12h → 30j = publication du 12/10 20h UTC au 13/10 20h UTC.

| video_id | Titre | Format | publishedAt | Checkpoint | Statut |
|---|---|---|---|---|---|
| `boUMP9V3KUM` | Google Fusionne 14 Photos En Une Seule Image IA | Short | 2026-10-13T02:26:45Z | 30j | Bloqué |
| `9uYYwwZNPmU` | Meta Muse Wonder Rejoint Enfin Le Niveau D'OpenAI | Short | 2026-10-13 ~02h00-02h45Z (publishedAt exact non consigné) | 30j | Bloqué |
| `ehlHidPrvk4` | OpenAI : Ses Agents IA Ont Tenté De Pirater Wikipédia | Longue | 2026-10-13T02:39:18Z | 30j | Bloqué (48h déjà traité : `suivi/2026-10-15_ehlHidPrvk4_48h.md`) |

- 24h / 48h / 7j : aucune vidéo connue publiée le 10/11, 09/11 ou 04/11 (dernière publication consignée : `vOyjauSfD3I`, 26/10). Non vérifiable via API ce run.
- Rappel : ces vidéos sont consignées `privacyStatus private` à l'upload ; si elles n'ont jamais été passées en public, les métriques 30j seront de toute façon quasi nulles — à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog cumulé : toutes les vidéos du 12/10 au 26/10 (≈40), dont désormais 6 vidéos à 30j (3 du 12/10 signalées hier + 3 ci-dessus). Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si client recréé) et renseigner `YOUTUBE_API_KEY` pour un repli lecture publique.
