# Suivi 7 jours — whV_FhPIeKI
**Titre** : "ChatGPT Publicité Gratuite : Ce Qui Change Le 24 Août (Et Comment L'éviter)" (vidéo longue, 8:10)
**Publié** : 2026-08-21T10:30:33Z · **Checkpoint** : 7 jours (traité le 2026-08-28, ~177,6h après publication) · `privacyStatus` : `public`

## Résultat
**2 vues (`videos.list`, temps réel), 0 like, 0 commentaire.** YouTube Analytics n'a traité que jusqu'au 26/08 au moment de ce run : sur cette fenêtre, **1 vue, 0 min regardée (arrondi), rétention 0,24%, 0 abonné généré**, trafic **`EXT_URL` 1 (100%)**. **Échantillon extrêmement faible (1-2 vues sur 7 jours complets)** — aucune conclusion forte possible (Guide d'Analyse §12/13), ce rapport se limite à documenter les faits mesurés.

Ce cas rejoint la série déjà extensivement documentée du pattern "vidéo longue hors créneau 18:00 GMT → distribution quasi nulle" (17-18 cas indépendants au 26/08) : publiée à 10:30 UTC, hors créneau. Historique de cette vidéo précise : 0 vue absolu à 24h (22/08), 1 vue à 48h (23/08, sortie de la catégorie "0 absolu"), et maintenant 2 vues à 7 jours — confirme le profil "volume quasi nul avec trickle tardif" déjà documenté sur d'autres cas (`42-QhuX2xmU`, `sGalxgwwGlk`) plutôt qu'un blocage total permanent.

## Ce qui fonctionne
Rien à isoler sur un échantillon de 1-2 vues.

## Ce qui doit changer
**Confirmation supplémentaire (n+1) du pattern hors créneau sur cycle de vie complet** : cette vidéo n'atteint jamais une distribution normale sur ses 7 premiers jours, malgré un score de production correct (82,7/100, déjà documenté) et un sujet chiffré/daté ("24 août", cohérent avec le gabarit `angles_privilegier`). La cause reste structurelle (horaire de publication / cron non corrigé), pas éditoriale.

## Hypothèse
Identique à l'hypothèse déjà consolidée sur les 17-18 cas précédents : le cron réel du trigger vidéo longue (`02:06 UTC`) reste désaligné du créneau doctrinal documenté (18:00 GMT), ce qui prive systématiquement ces vidéos de la fenêtre de notification/découverte optimale. La source de trafic unique mesurée (`EXT_URL`) est cohérente avec un trafic externe résiduel plutôt qu'une reprise algorithmique.

## Action suivante
1. Aucune action spécifique à cette vidéo — le diagnostic et la recommandation (corriger `cron_expression` à `0 18 * * *` ou acter le créneau réel) sont déjà transmis à Théo à plusieurs reprises depuis le 09/08, toujours non appliqués selon la documentation disponible au 28/08.
2. Ce cas s'ajoute au faisceau de preuves déjà réuni — pas de nouvelle piste à ouvrir sur cette seule mesure.
3. Voir aussi `suivi/2026-08-28_IeC8-ARMz8o_24h.md` (nouveau cas du même pattern, checkpoint 24h, traité le même jour).

## Score (Guide d'Analyse section 11)
**Non noté individuellement** — échantillon de 1-2 vues sur cycle complet, largement insuffisant pour une note fiable sur 100 (Guide d'Analyse §12/13). Documenté uniquement comme point de données supplémentaire pour le pattern transversal "hors créneau" déjà consigné dans la Base de Connaissances.
