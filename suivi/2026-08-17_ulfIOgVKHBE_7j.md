# Suivi 7 jours — ulfIOgVKHBE
**Titre** : "ByteDance (TikTok) double la durée de ses vidéos IA" (Short, 54s)
**Publié** : 2026-08-10T08:15:13Z · **Checkpoint** : 7 jours (traité le 2026-08-17, ~179,9h après publication) · `privacyStatus` : `public`

## Résultat
**43 vues (Analytics et `videos.list` concordants), 2 likes (4,65%), 0 commentaire, 0 abonné généré, 0 partage.** Durée moyenne de visionnage 21s sur 54s (**rétention 39,7%**). Répartition du trafic : **SHORTS 40 (93,0%)**, NO_LINK_OTHER 2 (4,7%), YT_SEARCH 1 (2,3%). Impressions/CTR non disponibles (restriction API connue, documentée dans `BASE-DE-CONNAISSANCES.md`).

**Comparaison au checkpoint 48h (2026-08-12)** : 41 vues, rétention 40,34%, 92,7% Shorts, 0 abonné. Entre le 48h et le 7j, le volume n'a progressé que de **+2 vues en 5 jours** (41 → 43) — la reprise Shorts initiale (92-93% du trafic) s'est arrêtée quasiment immédiatement après la fenêtre de distribution des 48 premières heures. Rétention quasi inchangée (40,34% → 39,7%).

## Ce qui fonctionne
La reprise Shorts initiale a bien eu lieu (93% du trafic cumulé), cohérente avec le gabarit "sujet produit IA + chiffre/fait concret sur marque reconnue" déjà documenté. Le titre ("double la durée") est compréhensible immédiatement et repose sur une marque connue (ByteDance/TikTok).

## Ce qui doit changer
**Plateau de volume quasi total après 48h** — la vidéo n'a quasiment plus été poussée par l'algorithme après la fenêtre initiale, contrairement aux meilleurs cas de la chaîne qui continuent de croître significativement entre 48h et 7 jours (ex. `M8MD4mlxkBs` : de plusieurs centaines à 1029 vues). **0 abonné généré sur 43 vues et un cycle complet de 7 jours** malgré une distribution correcte — confirmation supplémentaire, désormais sur cycle complet, du pattern "distribution Shorts forte ≠ conversion abonnés" (Guide d'Analyse §6).

## Hypothèse
Le sujet et le titre (fait concret sur marque reconnue) suffisent à déclencher une reprise Shorts initiale, mais l'absence de bénéfice personnel direct explicite pour le spectateur (contrairement à "qui bosse pour toi" ou "moitié prix pour presque le même niveau") limite à la fois la rétention (39,7%, moyenne-basse pour la chaîne) et la durée de vie de la distribution algorithmique — l'algorithme semble arrêter de pousser la vidéo une fois le potentiel initial exploré, faute de signaux d'engagement forts (0 abonné, 0 partage, seulement 2 likes) pour la relancer.

## Action suivante
1. **Mettre à jour la Base de Connaissances** : nouvelle confirmation indépendante, sur cycle complet, du pattern "distribution Shorts forte + 0 conversion abonné" — et premier cas documenté de plateau de volume aussi marqué et aussi rapide (quasi arrêt total dès le 48h).
2. Pour les prochains titres de ce type (fait produit sur marque reconnue, sans bénéfice personnel direct), tester systématiquement l'ajout d'un bénéfice concret pour le spectateur en plus du fait, pour vérifier si cela prolonge la fenêtre de distribution au-delà des 48 premières heures.

## Score (Guide d'Analyse section 11)
CTR non disponible (restriction API) — poids reporté sur Rétention et Engagement.

| Critère | Note /100 | Poids | Commentaire |
|---|---|---|---|
| Sujet | 75 | 15% | Marque reconnue (ByteDance/TikTok), fait produit concret |
| Packaging (titre+miniature) | 72 | 15% | Fait concret mais sans bénéfice personnel direct explicite |
| CTR | N/A | — | Métrique indisponible (restriction API) |
| Rétention | 52 | 30% | 39,7% — moyenne basse pour la chaîne, stable depuis le 48h |
| Engagement | 45 | 20% | 2 likes (4,65%) sur cycle complet, 0 commentaire, 0 partage |
| Conversion abonnés | 25 | 20% | 0 abonné sur 43 vues et cycle complet de 7 jours |

**Score global : ~56/100** (moyenne pondérée). Distribution Shorts initiale correcte mais plateau rapide et conversion nulle sur cycle complet — sujet à retester avec un bénéfice personnel explicite plutôt qu'abandonner le format.
