# Suivi 7 jours — XdmdZSKq3Mw
**Titre** : "Perplexity Bloque Tes Données Avant Le Cloud" (Short, 51s)
**Publié** : 2026-09-03T09:00:23Z · **Checkpoint** : 7 jours (traité le 2026-09-10, ~179,1h après publication) · `privacyStatus` : `public`

**Note méthode** : 1er rapport de suivi pour cette vidéo — les checkpoints 24h (04/09) et 48h (05/09) sont tombés dans la panne de 3 jours de la routine de suivi (04-06/09, documentée le 07/09) et n'ont jamais été traités. Ce 7 jours est donc le premier point de donnée disponible pour cette vidéo.

## Résultat
**47 vues (`videos.list`)**, **50 vues (Analytics)** — léger écart, sens inhabituel (Analytics > `videos.list`) mais dans la marge déjà documentée entre les deux sources. **Rétention 695,4%** (`averageViewDuration` 354s sur une vidéo de 51s) — valeur extrême attribuable au replay/boucle des Shorts (cf. `TV8jLECHVb0` 1 226%, doctrine du 20/08 : traiter comme "piste forte à confirmer", pas un fait établi). Signal plus fiable : la courbe `relativeRetentionPerformance` (percentile normalisé, non gonflé par le replay) **part à ~0,50 (médiane) sur les 80 premiers points puis monte fortement à 0,90-0,95 (90e-95e percentile) sur les 15 derniers points de la vidéo** — la seconde moitié de cette vidéo retient nettement mieux que les Shorts comparables sur YouTube. `audienceWatchRatio` reste stable entre 6,9 et 7,9 tout au long de la courbe (pas de décrochage précoce, boucle répartie sur l'ensemble du contenu). Trafic : `SHORTS` 42/50 (84,0%), `YT_SEARCH` 6/50 (12,0%), `YT_OTHER_PAGE` 2/50. **0 like, 0 commentaire, 0 abonné généré.**

## Ce qui fonctionne
Reprise Shorts forte (84%) combinée à un signal de rétention normalisé exceptionnel en seconde moitié (percentile 0,90-0,95) — parmi les meilleures courbes détaillées mesurées sur la chaîne à ce jour, cf. le précédent le plus proche (`dKChYEliXZk`, `dYNLzfArczE` restaient sous 0,25). Contrairement au pattern "décrochage avant 7-9s" documenté 12 fois sur d'autres Shorts, `audienceWatchRatio` ne chute jamais ici — signe d'un rythme/contenu qui retient au lieu de perdre l'audience.

## Ce qui doit changer
**0 engagement absolu** (0 like, 0 commentaire, 0 abonné) malgré une rétention exceptionnelle et un bon volume — écart notable entre qualité de rétention et conversion. Rejoint le pattern "rétention forte n'implique pas conversion" déjà documenté sur d'autres cas (ex. `lARzLbhyPeQ`), mais ici avec un signal de rétention nettement plus fort que la moyenne, ce qui rend l'absence totale de conversion plus surprenante.

## Hypothèse
Sujet produit (fonctionnalité de confidentialité Perplexity, traitement des données avant envoi au cloud) : probablement perçu comme une démonstration/information utile et regardée jusqu'au bout (voire en boucle), mais sans accroche de marque Tech & Café ni CTA suffisamment fort pour convertir en abonnement — cohérent avec Guide d'Analyse §6 ("beaucoup de vues + peu d'abonnés = CTA/identité de marque à renforcer"), ici amplifié par une rétention déjà très haute qui aurait dû, en théorie, favoriser la conversion.

## Action suivante
1. **Mettre à jour la Base de Connaissances (Hooks gagnants / Formats performants)** : nouveau cas de référence pour une courbe de rétention normalisée en forte progression en seconde moitié (percentile 0,50→0,95) — à comparer aux prochaines courbes détaillées pour identifier si le sujet (démonstration produit) ou la structure du montage explique ce pattern.
2. Sur les prochains sujets similaires à forte rétention démontrée, renforcer explicitement le CTA de fin (identité Tech & Café, incitation à s'abonner) pour tester si la conversion suit.
3. Réévaluer au checkpoint 30 jours pour confirmer la stabilité de ce signal sur cycle complet.

## Score (Guide d'Analyse section 11)
n=47-50, échantillon modeste mais cohérent. CTR non disponible :
Sujet 82/100, Packaging 80/100, Rétention 90/100 (signal normalisé exceptionnel en seconde moitié, prudence sur l'AVP absolu gonflé par le replay), Engagement 30/100 (0 like/commentaire malgré la rétention), Conversion abonnés 20/100 (0/47-50), Valeur long terme non pertinente à ce checkpoint (réservée au 30j).
**Score global indicatif : ~65/100** — tiré vers le haut par le signal de rétention le plus fort mesuré récemment, tiré vers le bas par une conversion nulle malgré ce signal.
