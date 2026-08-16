# Suivi 7j — YqUmf9QEltE
**Titre** : "Inkling : le Modèle IA Gratuit de l'Ex-CTO d'OpenAI" (vidéo longue, 7:48)
**Publié** : 2026-08-09T20:30:08Z · **Checkpoint** : 7 jours (traité le 2026-08-16, ~167,6h après publication) · `privacyStatus` : `public`

## Résultat
**Changement de statut par rapport aux checkpoints précédents** : cette vidéo était restée à **0 vue absolue** (`videos.list` ET Analytics concordants) du checkpoint 24h (2026-08-10) au checkpoint 48h (2026-08-11), le pire résultat jamais enregistré pour une vidéo longue de la chaîne à ce stade (voir `BASE-DE-CONNAISSANCES.md`, Erreurs fréquentes / Observations factuelles). Au checkpoint 7 jours, `videos.list` affiche désormais **1 vue**. Côté YouTube Analytics, la requête par dimension `video` ne retourne aucune ligne pour cette vidéo sur la période complète, mais une requête par dimension `insightTrafficSourceType` retourne une ligne `NO_LINK_OTHER` à 0 vue — signal contradictoire/à la marge, cohérent avec un échantillon d'exactement 1 vue qui se situe à la limite de ce que l'API Analytics remonte de façon fiable. Impressions/CTR non disponibles (limitation API déjà documentée).

## Ce qui fonctionne
Rien à évaluer sérieusement sur un échantillon d'1 vue — aucune conclusion sur le contenu (script, hook, montage) n'est possible à ce stade.

## Ce qui doit changer
Rien à corriger côté contenu sur la base d'une seule vue. Le vrai sujet reste la découvrabilité : cette vidéo (avec `6VynsMUfd6M` et `42-QhuX2xmU`) fait partie du pattern documenté "vidéo longue publiée hors créneau 18:00 GMT → volume proche de zéro" — `YqUmf9QEltE` a été publiée à 20:30 UTC, hors créneau.

## Hypothèse
La sortie du 0 vue absolu strict (persistant sur 2 checkpoints complets) pourrait indiquer que la vidéo a fini par être indexée/découverte tardivement (probablement via une recherche `YT_SEARCH` isolée, cohérent avec le pattern déjà documenté pour les vidéos longues pédagogiques/thématiques sans reprise algorithmique), plutôt qu'un changement de politique de distribution. Échantillon bien trop faible (1 vue) pour trancher entre "started organically" et "artefact de comptage à la marge" — aucune conclusion ferme n'est possible.

## Action suivante
1. **Signaler à Théo** : premier signal de vie (1 vue) après 7 jours de 0 absolu — ne change pas l'urgence de la vérification manuelle déjà demandée les 11/08, 12/08 et 13/08 (persistance du pattern d'absence de distribution sur les vidéos longues hors créneau 18h GMT, désormais 4 cas avec `bihb_tCYC5U` documenté ce même run).
2. Aucune action de contenu à ce stade — échantillon trop petit pour tirer des conclusions (règle Guide d'Analyse §12).
3. C'est le dernier checkpoint prévu pour cette vidéo avant le 30 jours — la traiter à ce moment pour vérifier si un trafic `YT_SEARCH` tardif continue de s'accumuler (pattern "concept expliqué, découverte uniquement par recherche" déjà documenté sur d'autres vidéos longues).

## Score (Guide d'Analyse section 11)
Non calculable — échantillon d'1 vue, largement sous le seuil minimal pour un score significatif (règle Guide d'Analyse §12 : signaler plutôt que conclure hâtivement).
