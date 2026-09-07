# Suivi performance — Checkpoint 48h

**Vidéo :** Microsoft Bat OpenAI Et Google Sur La Transcription IA
**ID :** ubuaaxgURAY | **Format :** Short (53s)
**Publiée :** 2026-09-05 09:31 GMT | **Âge au moment du run :** ~58,6h · `privacyStatus` : `public`

## Résultat

**132 vues dans la fenêtre Analytics (162 en temps réel, Data API), 4 likes, 0 commentaire, 0 abonné généré.** Rétention moyenne **26,55%** (14s/53s) — sous la moyenne habituelle de la chaîne pour un Short. Trafic massivement porté par le flux Shorts : **95,5% `SHORTS`** (126/132), 2,3% `YT_SEARCH`, 2,3% `YT_OTHER_PAGE`. Reprise algorithmique nette, cohérente avec le titre comparatif chiffré ("bat OpenAI et Google").

**Courbe de rétention détaillée** (`elapsedVideoTimeRatio`, 100 points) : `relativeRetentionPerformance` ouvre à 0,376 (1%) et **ne chute jamais sous le seuil ~0,15 des cas de décrochage sévère avant 31%** (0,130 à 31%) — l'ouverture est donc correcte, contrairement au pattern dominant de la chaîne. La courbe **creuse ensuite en milieu de vidéo** (minimum 0,062 vers 56%, ~30s), avant une **remontée nette en fin de vidéo** (0,223 à 81%, 0,496 à 100%).

## Ce qui fonctionne

L'ouverture ne décroche pas — 4e ou 5e contre-exemple documenté au pattern "décrochage avant 7-9s" (après `dxjOMygjD98`, `nd_k65RrXH8`, `gSYRWsjJZgQ`, `-A3JYclGdag`), et la fin de vidéo retient bien (remontée à 0,496, l'une des meilleures valeurs finales mesurées). Reprise Shorts quasi totale (95,5%) : le packaging/titre comparatif chiffré fonctionne pour l'attractivité initiale.

## Ce qui doit changer

**Nouveau sous-profil de courbe non encore typé précisément** : contrairement aux profils déjà documentés ("décrochage précoce", "creux initial + remontée fin", "bonne ouverture + érosion 2e moitié sans remontée"), cette vidéo montre une bonne ouverture **suivie d'un creux au milieu de la vidéo** (pas à l'ouverture) puis d'une forte remontée en fin. Le milieu de la vidéo (le développement du comparatif Microsoft/OpenAI/Google, probablement la partie la plus "démonstrative"/technique) est la zone qui perd le plus d'audience relative, pas l'ouverture. Rétention absolue faible (26,55%) malgré ce profil de courbe pas trop mauvais en relatif — à interpréter avec prudence (`relativeRetentionPerformance` est un percentile, pas une garantie de rétention absolue correcte).

## Hypothèse

Le titre comparatif ("bat OpenAI et Google") capte l'attention en ouverture et donne envie de voir la conclusion (remontée finale), mais le développement du milieu — probablement l'explication du comparatif lui-même — retient moins bien que l'accroche et la chute. Cohérent avec l'hypothèse déjà posée pour `UPTmgkPwncw` (27/08, sujet B2B/infrastructure) : le développement manque de bénéfice personnel direct pour le spectateur, même quand l'accroche et la conclusion fonctionnent.

## Action suivante

1. Documenter ce nouveau sous-profil "bonne ouverture + creux médian + forte remontée finale" dans la Base de Connaissances (Hooks gagnants), à confirmer sur d'autres cas avant de le généraliser.
2. Pour les prochains scripts de type comparatif, resserrer la partie développement/démonstration (milieu de vidéo) — c'est la zone qui perd le plus d'audience relative ici, pas l'ouverture ni la fin.
3. Réanalyser au 7 jours pour confirmer la stabilité de cette courbe et vérifier si la conversion abonnés s'améliore avec le volume.

## Score (Guide d'Analyse section 11)
Pondération Rétention 35% / Engagement 20% / Conversion 20% / Sujet 15% / Packaging 10% (CTR/impressions indisponibles) :

| Axe | Note | Justification |
|---|---|---|
| Sujet | 75/100 | Comparatif produit IA chiffré, actualité datée |
| Packaging (titre) | 78/100 | Titre comparatif clair, a généré une reprise Shorts quasi totale (95,5%) |
| Rétention | 45/100 | 26,55% en absolu faible, mais courbe relative sans décrochage sévère à l'ouverture ni en fin |
| Engagement | 40/100 | 4 likes / 132 vues (3,0%), correct sans être remarquable |
| Conversion abonnés | 0/100 | 0 abonné généré sur la fenêtre mesurée |

**Score final estimé : ~48/100** — bon packaging et bonne reprise algorithmique, mais le développement du comparatif perd de l'audience et la conversion abonnés reste à 0 malgré le volume.
