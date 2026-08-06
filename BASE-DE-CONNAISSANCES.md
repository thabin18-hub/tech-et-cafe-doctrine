# BASE DE CONNAISSANCES — TECH & CAFÉ

> Mémoire stratégique du Directeur de Production IA (SOP 12 / Guide d'Analyse des Performances section 9). Mise à jour par la routine de suivi quotidien et la routine de recommandations hebdomadaire. Ne pas éditer manuellement la structure, seulement lire pour contexte.

## Titres gagnants
_Aucune donnée pour le moment. Structure attendue par entrée : titre, vidéo, CTR obtenu, pourquoi ça a fonctionné._

## Hooks gagnants
_Aucune donnée pour le moment. Structure attendue par entrée : hook (texte), vidéo, rétention 30s obtenue, pourquoi ça capte l'attention._

## Miniatures performantes
_Aucune donnée pour le moment. Structure attendue par entrée : description miniature (couleurs, composition, élément visuel), vidéo, CTR obtenu._

## Sujets performants
_Aucune donnée pour le moment. Structure attendue par entrée : thème, angle, audience concernée, résultats._

## Formats performants
_Aucune donnée pour le moment. Structure attendue par entrée : durée, rythme, structure, résultats._

## Erreurs fréquentes
- **Erreur** : échec silencieux/bloquant de la routine vidéo longue quotidienne, aucune vidéo produite.
  **Cause** : le fichier `.env` (YOUTUBE_REFRESH_TOKEN, GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET, TTS_API_KEY, DRIVE_REFRESH_TOKEN) n'est pas provisionné dans l'environnement Claude Code Remote qui exécute la routine planifiée — confirmé absent du système de fichiers ET des variables d'environnement du shell (seul GITHUB_TOKEN est présent). Ce n'est pas un bug du script ni du prompt : la synthèse vocale (TTS_API_KEY) et l'upload YouTube ne peuvent tout simplement pas démarrer sans ces secrets.
  **Correction du processus appliquée** : v2 du prompt (script Python `produce_long_video.py` testé manuellement) a bien résolu le problème d'improvisation ffmpeg/TTS des runs précédents, mais ne peut pas résoudre un problème de provisioning d'environnement — ceci reste hors de portée de l'agent. **Mise à jour du même jour** : les credentials ont été fournies manuellement en cours de run (transmises directement dans la conversation de la session planifiée) — à noter que ce mode de transmission expose les secrets en clair dans l'historique de conversation, ce qui est exactement l'anti-pattern identifié lors de l'incident du 04/08 ("aucun secret en clair"). Recommandation pour Theo : provisionner durablement le `.env` au niveau de l'environnement Claude Code Remote (variables d'environnement de l'environnement, pas du prompt/chat) pour que ça ne se reproduise plus. Voir `echcafe-visual-library/diagnostic/2026-08-06-video-longue-v2-echec-env.txt`.
  **Date** : 2026-08-06 (récidive du 04/08, résolue manuellement en cours de run le même jour, pas au niveau infra).

- **Erreur** : miniature de mauvaise qualité — titre illisible (trop long, police auto-réduite jusqu'à devenir minuscule, en violation de la règle "max 3 mots" de GUIDE-MINIATURES.md) et artefact visuel de bandes horizontales (banding/interlacing) sur l'image de fond.
  **Cause** : (1) `produce_long_video.py` (`make_thumbnail()`) réutilise directement `--title` (le titre YouTube complet, ~60 caractères) comme texte de la miniature, sans argument séparé pour un accroche courte dédiée à la miniature — les deux contraintes (bon titre YouTube = descriptif, bonne miniature = 3 mots max) sont contradictoires et le script ne les distingue pas. (2) La frame utilisée pour la miniature est extrayée à un point fixe (30% de la durée totale de la vidéo) sans vérification de qualité ; ce run, elle est tombée sur un segment utilisant un asset de la bibliothèque (vidéo "robot qui court") qui produit un artefact de bandes horizontales visible dans le segment vidéo lui-même (confirmé en extrayant `thumbnail_frame.jpg` et en comparant à d'autres frames du montage, propres) — probablement un problème de pixel format/canal alpha sur cet asset spécifique, non lié au reste de la bibliothèque.
  **Correction du processus appliquée** : documentée pour amélioration du script, pas corrigée dans ce run (coût API réel à chaque nouvel appel TTS/upload, score global déjà correct sur le fond éditorial). Recommandations concrètes pour la prochaine itération de `produce_long_video.py` : ajouter un argument `--thumbnail-title` (court, 2-3 mots) distinct de `--title` ; wrap/reduction de police avec plancher minimum lisible (actuellement s'arrête à 72px, pourrait descendre en dessous sans rejet) ; logger l'asset source utilisé par segment (actuellement absent des logs, ce qui a rendu l'investigation plus lente) ; identifier et retirer/reconvertir l'asset "robot qui court" fautif de `assets/` si le problème se reproduit sur un prochain run.
  **Date** : 2026-08-06.

## Historique des scores qualité (Guide de Production §12 + Guide SEO §15)
- **2026-08-06** — **"AI Act 2026 : Ce Que la Loi Change Pour Toi Dès Maintenant"** (video_id `GV7uhte8lG4`, privacyStatus confirmé `private`, durée 7:59).
  Scores détaillés /100 : Sujet 92, Script 90, Valeur 90, Exactitude 93, Hook 85, Titre 82, Miniature 35, SEO 82, Chapitres 90, Montage 55.
  **Score global : 79/100.**
  Décision : **non publiée par l'automatisation** (reste privée conformément à `PRODUCTION-CONFIG.yaml` — privacy_policy.video_longue = private indéfiniment, décision Theo du 05/08 ; publication manuelle uniquement). Score sous le seuil de 90/100 du Guide de Production de toute façon : la miniature (35/100) et le montage (55/100) sont pénalisés par un défaut concret et localisé (voir Erreurs fréquentes ci-dessus — titre miniature illisible + un segment avec artefact visuel), pas par le fond éditorial du script qui est solide (sujet vérifié sur sources multiples : RTBF, Touteleurope, Commission européenne, Droit&Technologie ; exactitude et incertitudes clairement indiquées). Recommandation avant toute publication manuelle par Theo : régénérer/corriger la miniature à la main avant publication, ou attendre la prochaine itération du script qui corrigera le titre miniature et le choix de frame.
