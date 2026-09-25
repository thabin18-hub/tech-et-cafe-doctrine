# Suivi 7 jours — vMVEQn9oYbk
**Titre** : "OpenAI Avoue : Son IA Ment Pour Cacher Ses Erreurs" (Vidéo longue, 7min43)
**Publié** : 2026-09-18T09:59:29Z · **Checkpoint** : 7 jours (traité le 2026-09-25, ~178,2h après publication) · `privacyStatus` : `public`

## Résultat
**2 vues (`videos.list` et Analytics, cohérentes), 0 like, 0 commentaire, 0 abonné, 0 partage.** Durée moyenne de visionnage **512s pour une vidéo de 463s (AVP 110,76%)** — signal de replay/rewatch, mais **échantillon bien trop petit (n=2) pour en tirer une conclusion fiable** (Guide d'Analyse §12). Trafic : `YT_CHANNEL` 1, `YT_SEARCH` 1. Aucune courbe de rétention détaillée disponible (0 ligne retournée) — confirme le seuil de volume minimal déjà documenté (20/08) en dessous duquel l'API ne retourne pas la courbe `elapsedVideoTimeRatio`.

## Ce qui fonctionne
Rien à établir avec certitude sur un échantillon de 2 vues. Le signal AVP >100% est intéressant mais **ne doit pas être traité comme une confirmation** — les précédents cas de replay extrême à faible échantillon (`iAgs4ss3gO0`, `rRpLlGpQoT0`) n'avaient pas non plus débloqué de reprise algorithmique.

## Ce qui doit changer
Le titre ("OpenAI Avoue : Son IA Ment Pour Cacher Ses Erreurs") place bien "OpenAI" en premier mot — conforme à la règle SOP 05 (mot-clé de recherche dans les 5 premiers mots) — donc **ce cas ne relève pas du pattern "titre sans mot-clé"** identifié sur `RFVO2BYXI8c`. Le facteur limitant le plus probable reste structurel : le format vidéo longue n'a par construction pas accès au flux Shorts (87,1% du trafic total de la chaîne, référence 25/07→18/08), et "OpenAI" seul, sans nom de modèle précis ni fonctionnalité citée, reste un terme très générique face à un volume de contenu concurrent déjà saturé sur ce mot-clé.

## Hypothèse
Sujet éditorialement solide (accusation de tromperie d'un modèle OpenAI, fort potentiel de curiosité) et titre conforme à la règle de mot-clé en tête — mais format vidéo longue structurellement privé du flux Shorts, combiné à un mot-clé ("OpenAI") trop générique pour se distinguer en recherche pure. Le volume nul est cohérent avec ce double facteur, sans qu'il soit nécessaire d'invoquer un problème de fond éditorial ni un titre mal construit.

## Action suivante
1. Réévaluer au 30 jours — avec un échantillon aussi faible, le signal replay (AVP 110,76%) reste à confirmer ou infirmer sur plus de volume avant toute action.
2. Ne pas documenter ce cas comme nouvelle occurrence du pattern "titre sans mot-clé" (il ne s'applique pas ici) — noter plutôt, si confirmé sur d'autres cas futurs, que "OpenAI" seul (sans nom de modèle/fonctionnalité) peut être un mot-clé trop générique pour la recherche.
3. Sur les prochains sujets similaires, tester un titre combinant la marque ET un terme plus spécifique (nom du modèle, fonctionnalité précise) plutôt que la marque seule.

## Score (Guide d'Analyse section 11)
**Non calculable de façon fiable** — échantillon n=2, bien en dessous du seuil exploitable. Signal directionnel : volume nul cohérent avec le pattern "titre sans mot-clé de recherche" déjà documenté pour le format long.
