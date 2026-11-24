# Suivi performance — 2026-11-24 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- **15e run quotidien consécutif** avec la même panne (10/11 → 24/11), active depuis ~26/10 (~29 jours). Non résolue.
- **Fait nouveau** : `YOUTUBE_API_KEY` est désormais **renseignée** dans l'environnement (longueur non nulle, valeur non affichée) — elle était vide jusqu'au 23/11. Le repli lecture publique (Data API v3 `videos.list`/`playlistItems`) **n'a pas été exécuté** ce run : l'appel a été refusé par le contrôle de permissions de la session, ce prompt de suivi n'autorisant explicitement que les tokens OAuth. Même si ce repli fonctionne, il ne donne que des compteurs publics (vues/likes/commentaires totaux, `privacyStatus`, `publishedAt`) — **pas** les métriques Analytics fenêtrées (rétention, durée moyenne, abonnés générés) exigées par le Guide d'Analyse. Il ne remplace donc pas le rétablissement OAuth.

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-24 ~20h UTC ±12h → 30j = publications du 25/10 ~08h UTC au 26/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `vOyjauSfD3I` | YouTube Lance Ask YouTube, Son Nouveau Chatbot IA | Longue | 2026-10-26T02:40:35Z | 30j | Bloqué |
| `vUrGqeGLQAE` | Des Hackers Piratent OpenCode Et Volent 1700 Dollars | Short | non consigné (run shorts ~02h UTC le 26/10) | 30j (probable) | Bloqué |
| `AnllqK0aJgo` | Mistral Lance Une IA Qui Parle Plus De 50 Langues | Short | non consigné (run shorts ~02h UTC le 26/10) | 30j (probable) | Bloqué |

- `publishedAt` exact absent du log de production pour les deux shorts (6e et 7e occurrences de ce défaut). Checkpoint 30j très probablement aujourd'hui ; à confirmer au rattrapage.
- 24h / 48h / 7j : aucune vidéo consignée publiée le 23/11, 22/11 ou 17/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Ces 3 vidéos sont les **dernières** publications consignées : à partir de demain, plus aucun checkpoint 30j n'est attendu tant qu'aucune nouvelle production n'a lieu.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles ne sont jamais passées en public, métriques 30j quasi nulles — à vérifier au rattrapage avant toute conclusion (ne pas interpréter un 0 comme un échec de sujet/packaging).

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **44 vidéos** (12/10 → 26/10) — backlog désormais **complet** (plus aucune vidéo n'entrera dans la file). Priorité : 30j, puis 7j ; `PatL4gDO1C4` (échéance datée 11/12/2026) en tête.

## Action requise (humain)
1. Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé).
2. Si le repli par clé API doit être utilisé par cette routine, l'autoriser explicitement dans le prompt de suivi (actuellement limité aux tokens OAuth) — utile uniquement pour identifier les checkpoints et vérifier `privacyStatus`.
3. Constat annexe : aucune production consignée depuis le 26/10 (29 jours).
