# Suivi 48h — sGalxgwwGlk
**Titre** : "Google Gemini Spark : l'agent IA passe de 100$ à 20$/mois" (vidéo longue, 7:14)
**Publié** : 2026-08-15T09:00:28Z · **Checkpoint** : 48h (traité le 2026-08-17, ~59,1h après publication) · `privacyStatus` : `public`

## Résultat
**4 vues (`videos.list`), mais seulement 1 ligne remontée par YouTube Analytics** (écart de 3 vues, cohérent avec le délai de traitement Analytics déjà documenté dans `BASE-DE-CONNAISSANCES.md`). Sur cette unique ligne Analytics : durée moyenne de visionnage 260s sur 434s (**rétention 60,04%**), 0 like, 0 commentaire, 0 abonné généré. Trafic : **SUBSCRIBER 1 (100%)** — l'unique vue mesurée provient d'un abonné déjà existant, aucune découverte organique (recherche, recommandation, flux Shorts) mesurée à ce stade. Impressions/CTR non disponibles (restriction API connue).

**Échantillon extrêmement petit (1 à 4 vues selon la source)** — les résultats ci-dessous sont directionnels, pas une confirmation statistique (Guide d'Analyse §12).

Cette vidéo est publiée à **09:00 UTC**, hors du créneau "18:00 GMT vidéo longue" documenté (Contexte Global §11 / SOP 06) — le même créneau associé à 4 cas indépendants de vidéos longues à 0 vue absolu (`YqUmf9QEltE`, `6VynsMUfd6M`, `42-QhuX2xmU`, `bihb_tCYC5U`).

## Ce qui fonctionne
Rétention forte sur l'échantillon disponible (60,04% sur une vidéo de 7 minutes) — dans la fourchette haute-moyenne pour un format long de la chaîne, cohérent avec le pattern déjà documenté "vidéo longue pédagogique/produit = rétention correcte à excellente une fois trouvée".

## Ce qui doit changer
**Volume quasi nul et 0 découverte organique** — même à 4 vues (`videos.list`), 100% du trafic mesuré vient d'un abonné existant, aucun signal de recommandation, recherche ou flux Shorts. **Nuance importante au pattern "vidéo longue hors créneau 18h GMT = 0 vue absolu"** : contrairement aux 4 cas déjà documentés (tous à 0 vue stricte), celle-ci a au moins quelques vues — mais elles restent quasi entièrement internes à la base d'abonnés déjà acquise, pas de découverte nouvelle. Le pattern plus large ("hors créneau 18h = volume et distribution très faibles") se confirme même si le cas extrême (0 vue absolu) ne se répète pas ici.

## Hypothèse
Publier hors du créneau habituel de la vidéo longue semble limiter fortement la portée au-delà de la base d'abonnés déjà acquise, quel que soit le sujet (ici Gemini Spark, un produit nommé et daté, contrairement aux sujets "concept expliqué" du pattern déjà documenté) — ce qui suggère que l'horaire/la notification aux abonnés pèse plus lourd que le type de sujet sur la distribution des vidéos longues.

## Action suivante
1. **Mettre à jour la Base de Connaissances** : ajouter cette vidéo comme nuance au pattern "vidéo longue hors créneau 18h GMT" — pas un 5e cas de 0 vue absolu, mais un cas supplémentaire de volume quasi nul et 100% trafic abonné, qui renforce le lien horaire/distribution plutôt que sujet/distribution.
2. Revoir au checkpoint 7 jours pour voir si les 3 vues manquantes côté Analytics apparaissent et si un signal de découverte organique (au-delà de SUBSCRIBER) finit par apparaître.
3. Confirmer avec Théo si le passage à 09:00 UTC pour certaines vidéos longues est voulu (anomalie de calendrier déjà notée dans `BASE-DE-CONNAISSANCES.md` pour plusieurs runs du 12-17/08) ou à corriger dans le prompt du trigger.

## Score (Guide d'Analyse section 11)
CTR non disponible (restriction API). **Échantillon trop petit pour un score fiable** (Guide d'Analyse §12) — score indicatif fourni à titre directionnel uniquement.

| Critère | Note /100 | Poids | Commentaire |
|---|---|---|---|
| Sujet | 85 | 15% | Score de production 90 (Historique) ; sujet produit daté, potentiel confirmé sur le fond |
| Packaging (titre+miniature) | 75 | 15% | Score de production Miniature 85 / Montage 62 (Historique) |
| CTR | N/A | — | Métrique indisponible (restriction API) |
| Rétention | 62 | 30% | 60,04% sur n=1 — directionnel, à confirmer sur plus de volume |
| Engagement | 35 | 20% | 0 like/commentaire, mais volume trop faible pour interpréter |
| Conversion abonnés | 35 | 20% | 0 nouvel abonné, trafic 100% abonnés déjà existants |

**Score indicatif : ~59/100** (échantillon insuffisant — ne pas traiter comme un score de performance confirmé).
