# Suivi 7 jours — sGalxgwwGlk
**Titre** : "Google Gemini Spark : l'agent IA passe de 100$ à 20$/mois" (vidéo longue, 7:14)
**Publié** : 2026-08-15T09:00:28Z · **Checkpoint** : 7 jours (traité le 2026-08-22, ~179,1h après publication) · `privacyStatus` : `public`

## Résultat
**7 vues (`videos.list`), 5 vues remontées par YouTube Analytics** (écart de 2, cohérent avec le délai de traitement Analytics déjà documenté — écart en réduction par rapport aux 3 vues manquantes au checkpoint 48h). Sur les 5 vues Analytics : 9 minutes vues au total, durée moyenne de visionnage 117s sur 434s (**rétention 26,99%**), 0 like, 0 commentaire, 0 abonné généré, 0 partage. Impressions/CTR non disponibles (restriction API documentée).

**Trafic (5 vues)** : `YT_SEARCH` 2, `SUBSCRIBER` 1, `EXT_URL` 1, `PLAYLIST` 1 — **premier signal de découverte non-abonné mesuré sur cette vidéo** (4 vues sur 5 viennent de sources autres que la base d'abonnés existante), à l'inverse du checkpoint 48h où 100% du trafic mesuré (n=1) venait de `SUBSCRIBER`.

**Échantillon toujours très petit (5-7 vues)** — directionnel, pas une confirmation statistique (Guide d'Analyse §12).

## Ce qui fonctionne
**Apparition d'un filet de découverte organique entre le 48h et le 7 jours** (`YT_SEARCH` + `EXT_URL` + `PLAYLIST`, 3 sources différentes sur seulement 5 vues) — cohérent avec la nuance déjà documentée le 19/08 pour `42-QhuX2xmU` ("un filet de trafic recherche finit parfois par apparaître à 7 jours pour une vidéo longue hors créneau"), et en contraste avec `bihb_tCYC5U` qui restait à 0 découverte stricte sur cycle complet. Nouvelle donnée dans un débat déjà ouvert en base : le rattrapage tardif n'est pas systématique, mais n'est pas non plus un cas isolé.

## Ce qui doit changer
**Rétention en forte baisse par rapport au 48h** : 26,99% à 7 jours contre 60,04% au 48h (n=1 à l'époque). La chute est cohérente avec l'arrivée de nouveaux spectateurs de découverte (recherche, lien externe, playlist) qui n'ont pas le même niveau d'engagement préalable qu'un abonné déjà familier de la chaîne — mais reste un signal faible sur un score aussi bas pour une vidéo longue pédagogique (le format obtient historiquement des rétentions correctes à excellentes une fois trouvé, cf. Base de Connaissances section Hooks gagnants). **0 conversion abonné malgré la diversification du trafic** — cohérent avec la règle du Guide §6 (bonne découverte ≠ conversion automatique), mais confirme que le CTA de fin ne convertit pas ce format hors créneau.

## Hypothèse
Le filet de recherche/lien externe qui apparaît à 7 jours attire probablement des spectateurs moins qualifiés (recherche générique sur "Gemini Spark" ou clic depuis une playlist/lien externe sans connaissance préalable de la chaîne) que les abonnés qui avaient regardé jusqu'à 60% au 48h — d'où la chute de rétention moyenne malgré une légère hausse du volume. Le cycle de vie de cette vidéo confirme la nuance déjà en base : hors créneau 18:00 GMT ne bloque pas totalement la distribution à long terme, mais la limite à un filet minimal et tardif, avec une qualité d'audience plus diluée.

## Action suivante
1. **Mettre à jour la Base de Connaissances** (Hooks/Distribution) : ajouter ce cas comme 2e confirmation (après `42-QhuX2xmU`) qu'un filet de découverte tardif (recherche/externe/playlist) peut apparaître à 7 jours pour une vidéo longue hors créneau, sans que cela se traduise par une rétention ou une conversion fortes — nuance à la nuance du 19/08.
2. Aucune action de production nécessaire sur le contenu lui-même : le sujet et le script ne sont pas mis en cause par ce résultat (cf. score de production 85,1/100, Historique des scores qualité).
3. Ce cas est désormais clos (dernier checkpoint, 30 jours hors du cycle actuel de suivi rapproché — sera revu au checkpoint 30 jours si programmé).

## Score (Guide d'Analyse section 11)
CTR non disponible (restriction API). Échantillon petit (5-7 vues) — score indicatif uniquement.

| Critère | Note /100 | Poids | Commentaire |
|---|---|---|---|
| Sujet | 85 | 15% | Score de production 90 (Historique) ; sujet produit daté, confirmé pertinent |
| Packaging (titre+miniature) | 80 | 15% | Score de production Titre 88 / Miniature 85 (Historique) |
| CTR | N/A | — | Métrique indisponible (restriction API) |
| Rétention | 42 | 30% | 26,99% sur n=5 — en repli net depuis le 48h, échantillon toujours faible |
| Engagement | 30 | 20% | 0 like/commentaire/partage sur 5 vues |
| Conversion abonnés | 30 | 20% | 0 nouvel abonné malgré diversification du trafic |

**Score indicatif : ~50/100** (échantillon insuffisant pour un score confirmé — le signal le plus solide de ce checkpoint est l'apparition d'un trafic de découverte, pas la performance d'engagement).
