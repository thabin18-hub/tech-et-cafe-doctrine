# Suivi performance — 2026-11-19 (run quotidien SOP 07/08) — CHECKPOINTS BLOQUÉS

**Statut : aucune analyse possible. 0 donnée récupérée, aucun score calculé, aucune conclusion tirée.**

## Cause du blocage (vérifié ce run, ~20h03 UTC)
- Échange `refresh_token -> access_token` (oauth2.googleapis.com/token) avec `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` sur `YOUTUBE_ANALYTICS_REFRESH_TOKEN` → HTTP 401 `disabled_client: The OAuth client was disabled.`
- `YOUTUBE_REFRESH_TOKEN` non testé ce run (hors périmètre de la routine de suivi ; même client OAuth, présumé bloqué).
- **10e run quotidien consécutif** avec la même panne (10/11 → 19/11), active depuis ~26/10 (~24 jours). Non résolue.
- Repli lecture publique impossible : `YOUTUBE_API_KEY` présente mais vide (longueur 0, vérifié sans afficher de valeur).

## Checkpoints dus aujourd'hui (identifiés depuis BASE-DE-CONNAISSANCES.md, faute d'API)
Fenêtre : 2026-11-19 ~20h UTC ±12h → 30j = publications du 20/10 ~08h UTC au 21/10 ~08h UTC.

| video_id | Titre | Format | publishedAt (log de prod) | Checkpoint | Statut |
|---|---|---|---|---|---|
| `BgK_9Dr5Ah0` | Liquid AI Lance Une IA Gratuite Qui Tourne Sur Ton PC | Short | 2026-10-21 ~02h00-02h30 UTC (horodatage exact non consigné) | 30j | Bloqué |
| `azcEY4ktt0A` | Gemini Passe Tes Appels À Ta Place | Short | 2026-10-21 ~02h11-02h30 UTC (horodatage exact non consigné) | 30j | Bloqué |
| `qXEKfjEHGAo` | Gemini Android Auto : L'IA Qui Lit Tes Mails Prend Le Volant | Longue | 2026-10-21 ~02h20-02h50 UTC (horodatage exact non consigné) | 30j | Bloqué |

- 24h / 48h / 7j : aucune vidéo consignée publiée le 18/11, 17/11 ou 12/11 (dernière publication consignée : 26/10). Non vérifiable via API ce run.
- Rappel : vidéos consignées `privacyStatus private` à l'upload. Si elles n'ont jamais été passées en public, les métriques 30j seront quasi nulles : à vérifier au rattrapage avant toute conclusion.

## Rattrapage (dès rétablissement du client OAuth)
Requêtes Analytics historiques (`startDate` = publication, `endDate` = publication + N jours) : les checkpoints ne sont pas perdus. Backlog 30j cumulé : **30 vidéos** (12/10 → 21/10, 3 par jour), plus les checkpoints 24h/48h/7j/30j non traités des vidéos du 22/10 au 26/10. Priorité : 30j, puis 7j.

## Action requise (humain)
Réactiver ou recréer le client OAuth Google Cloud associé à `GOOGLE_CLIENT_ID` (puis réémettre les refresh tokens si le client est recréé) et renseigner une valeur pour `YOUTUBE_API_KEY` (repli lecture publique). Constat annexe : aucune production consignée depuis le 26/10.
