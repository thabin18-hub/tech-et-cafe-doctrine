# Suivi performance — 2026-11-23 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` → HTTP 401 `disabled_client: The OAuth client was disabled.` sur **les deux** refresh tokens (`YOUTUBE_ANALYTICS_REFRESH_TOKEN` et `YOUTUBE_REFRESH_TOKEN`).
- **14e run quotidien consécutif** avec la même panne (10/11 → 23/11), active depuis ~26/10 (~28 jours). Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` et `GOOGLE_API_KEY` toujours vides (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-23 ~20h UTC ±12h → 30j = publications du 24/10 ~08h UTC au 25/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `ner1invS6go` | Amazon Bedrock AgentCore : Une Faille Pouvait Pirater Tous Les Agents IA D'un Coup | Longue | 2026-10-25T02:52:46Z | 30j | Bloqué |
| `Ab0__HCpfu8` | Il Dit Non À Intel Et Qualcomm Pour Défier Nvidia | Short | non consigné (run shorts matinal du 25/10) | 30j (probable) | Bloqué |
| `R6OpjLz1wRk` | Amazon Lance Un Bracelet IA Qui T'écoute Pour 75 Dollars | Short | non consigné (run shorts matinal du 25/10) | 30j (probable) | Bloqué |
| `C2ssmtZcvCQ` | ChatGPT Verrouille Tes Chats Avec Un Code À 4 Chiffres | Short | non consigné (> 03h09 UTC le 24/10) | 30j hier ou aujourd'hui | Bloqué (reporté du 22/11) |

- `publishedAt` exact absent du log de production pour `Ab0__HCpfu8` et `R6OpjLz1wRk` (4e et 5e occurrences de ce défaut). Les runs shorts se déclenchent habituellement vers 02h UTC, donc checkpoint 30j très probablement aujourd'hui. À confirmer au rattrapage.
- 24h / 48h / 7j : aucune vidéo consignée publiée le 22/11, 21/11 ou 16/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles ne sont jamais passées en public, métriques 30j quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **41 vidéos** (12/10 → 25/10), plus les 30j dus les 24/11 et 25/11 (vidéos du 25/10 restantes et du 26/10, dont `AnllqK0aJgo`, `vUrGqeGLQAE`, `vOyjauSfD3I`). Priorité : 30j, puis 7j ; `PatL4gDO1C4` (échéance datée 11/12/2026) en tête.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10 (28 jours).
