# Suivi 48h — YsULRGCtpYs
**Titre** : "Google IA Réserve Tes Vacances (Sauf En France)" (Short, 44,5s)
**Publié** : 2026-08-29T11:00:24Z · **Checkpoint** : 48h (traité le 2026-08-31, ~57,1h après publication) · `privacyStatus` : `public`

## Résultat
**66 vues (`videos.list`, temps réel), 1 like (1,5%), 0 commentaire, 0 abonné** — en hausse depuis le checkpoint 24h (55 vues, `suivi/2026-08-30_YsULRGCtpYs_24h.md`). **Première donnée Analytics disponible**, mais **fenêtre très partielle : un seul jour couvert (2026-08-29)** sur les 57h écoulées — le délai de traitement J−2 plafonne la fin de fenêtre au 29/08, jour de publication lui-même. **À traiter comme un instantané du tout premier jour, pas comme une mesure des 48h complètes.** Sur cette fenêtre : 53 vues Analytics, **rétention 48,67%**, 0 abonné, 1 like, 0 partage. Trafic : `SHORTS` 45 (84,9%), `YT_SEARCH` 8 (15,1%).

## Ce qui fonctionne
Part de trafic recherche déjà notable (15,1%) dès le premier jour — cohérent avec la clause géographique du titre ("Sauf En France") qui crée une recherche d'intérêt local. Volume correct pour un jour de données (53-66 vues).

## Ce qui doit changer
**Décrochage précoce sévère, l'un des plus marqués mesurés sur la chaîne** : la courbe de rétention détaillée montre `relativeRetentionPerformance` chutant de 0,201 à 0,5s à **0,081 dès 4,5s**, puis restant constamment sous 0,1 sur la quasi-totalité de la vidéo (minimum 0,057 vers 90% de la durée). Rétention absolue également faible (48,67%, dans la moyenne basse). **0 abonné, 1 seul like sur 53-66 vues** — engagement quasi nul.

## Hypothèse
Même diagnostic que pour `uMqET9___4Q` (traité le même run) : le titre annonce une capacité produit ("Réserve Tes Vacances") avant la restriction/tension réelle ("Sauf En France"), placée en fin de titre. Si le script suit la même structure (mise en contexte avant la restriction), cela correspond à l'hypothèse consolidée depuis le 28/08 sur la structure d'ouverture comme facteur discriminant du décrochage précoce. Cette vidéo est un 2e cas du run avec exactement le même gabarit de titre ("capacité Google/Apple + restriction France en fin de titre") et le même symptôme (décrochage sévère avant 5s) — renforce l'hypothèse plutôt que de la confirmer isolément.

## Action suivante
1. **Mettre à jour la Base de Connaissances** : regrouper ce cas avec `uMqET9___4Q` (même run, même gabarit "capacité + restriction France en fin de titre", même décrochage précoce) comme point de données supplémentaire, sans les compter séparément dans le décompte de confirmations si le lien de cause est bien la structure du titre et non le sujet lui-même.
2. **Recommandation de processus (SOP02/04)** : pour les titres qui contiennent une restriction géographique ou une objection ("Sauf en France", "Mais pas en France"), tester une structure où cette tension est nommée dès l'ouverture du script plutôt qu'en conclusion du titre seul.
3. Revenir au checkpoint 7 jours pour une mesure Analytics complète et confirmer si la rétention/conversion évolue.

## Score (Guide d'Analyse section 11)
Pondération : Rétention 30% / Engagement 20% / Conversion 15% / Sujet 20% / Packaging 15% (CTR indisponible) :

| Axe | Note | Justification |
|---|---|---|
| Sujet | 68/100 | Sujet Google IA pertinent, restriction géographique crée un enjeu local |
| Packaging (titre) | 55/100 | Tension principale reléguée en fin de titre, même limite que `uMqET9___4Q` |
| Rétention | 32/100 | 48,67% en absolu mais décrochage précoce sévère confirmé par la courbe (min 0,057) |
| Engagement | 20/100 | 1 like sur 53-66 vues, 0 commentaire, 0 partage |
| Conversion abonnés | 0/100 | 0 abonné généré |

**Score final : ~40/100** — décrochage précoce sévère et conversion nulle ; à recouper avec le checkpoint 7 jours avant conclusion définitive (fenêtre Analytics encore partielle à ce stade).
