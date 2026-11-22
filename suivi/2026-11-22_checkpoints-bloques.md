# Suivi performance — 2026-11-22 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` → HTTP 401 `disabled_client: The OAuth client was disabled.` sur **les deux** refresh tokens (`YOUTUBE_ANALYTICS_REFRESH_TOKEN` et `YOUTUBE_REFRESH_TOKEN`).
- **13e run quotidien consécutif** avec la même panne (10/11 → 22/11), active depuis ~26/10 (~27 jours). Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` toujours vide (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-22 ~20h UTC ±12h → 30j = publications du 23/10 ~08h UTC au 24/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `jrGDf-lwopQ` | Microsoft Copilot Finit Ta Présentation Sans Toi | Short | 2026-10-24T02:17:32Z | 30j | Bloqué |
| `922ngQtrekM` | ChatGPT Accusé De Mettre Des Mineurs En Danger : 8 États Poursuivent OpenAI | Longue | 2026-10-24T03:09:27Z | 30j | Bloqué |
| `C2ssmtZcvCQ` | ChatGPT Verrouille Tes Chats Avec Un Code À 4 Chiffres | Short | non consigné (run postérieur à 03h09 UTC le 24/10) | 30j (probable) | Bloqué |

- `publishedAt` exact de `C2ssmtZcvCQ` absent du log de production (3e occurrence de ce défaut après `9uYYwwZNPmU` et `axlnAGh2IeU`). Le run a détecté la longue de 03h09 « après coup », donc publication > 03h09 UTC le 24/10 ; si avant ~08h UTC → checkpoint 30j aujourd'hui, sinon demain. À trancher au rattrapage.
- 24h / 48h / 7j : aucune vidéo consignée publiée le 21/11, 20/11 ou 15/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si jamais passées en public, métriques 30j quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **38 vidéos** (12/10 → 24/10), plus les 30j dus du 23/11 au 25/11 (vidéos du 25/10 et 26/10). Priorité : 30j, puis 7j ; `PatL4gDO1C4` (échéance datée 11/12/2026) en tête.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10 (27 jours).
