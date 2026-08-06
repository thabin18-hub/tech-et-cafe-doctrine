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
  **Correction du processus appliquée** : v2 du prompt (script Python `produce_long_video.py` testé manuellement) a bien résolu le problème d'improvisation ffmpeg/TTS des runs précédents, mais ne peut pas résoudre un problème de provisioning d'environnement — ceci reste hors de portée de l'agent. Action requise côté humain : provisionner le `.env` (ou secrets manager équivalent) dans l'environnement utilisé par le trigger 18h GMT, avant le prochain déclenchement. Voir `echcafe-visual-library/diagnostic/2026-08-06-video-longue-v2-echec-env.txt` pour le détail complet et le diagnostic original du 04/08 (`diagnostic/2026-08-04-*.txt`).
  **Date** : 2026-08-06 (récidive du 04/08, non résolue).
  **Confirmation additionnelle** : 2026-08-06 ~11:36 UTC, nouveau run indépendant (nouvelle session, nouveaux clones des 2 repos) sur le même trigger v2 — recherche `.env` et variables d'environnement (YOUTUBE_REFRESH_TOKEN, GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET, TTS_API_KEY, DRIVE_REFRESH_TOKEN) refaite intégralement, même résultat : rien de provisionné, seul GITHUB_TOKEN présent. Confirme qu'il ne s'agissait pas d'un aléa ponctuel du run de 10:35 UTC. Le déclenchement planifié officiel du jour (trigger "Video longue quotidienne v2", cron 18h GMT, `next_run_at` ~18:08 UTC) échouera de la même façon tant que le `.env` n'est pas provisionné dans l'environnement `env_01HSHMsZ4P9qMXY84945xzQr` avant cette heure. À noter aussi : le trigger ponctuel "MAINTENANCE - Mise a jour tokens Google" du 04/08 a déjà tourné et rotate des tokens exposés en clair dans un ancien trigger (contenu depuis retiré par mesure de sécurité) — mais cette rotation n'a pas résolu le provisioning du `.env` dans l'environnement d'exécution de la routine vidéo longue.

## Historique des scores qualité (Guide de Production §12 + Guide SEO §15)
- **2026-08-06** — Aucune vidéo produite. Score global : N/A. Décision : **annulé** — bloqué en amont (voir Erreurs fréquentes ci-dessus, absence de `.env`/credentials dans l'environnement d'exécution). Aucun script ni sujet n'a été soumis à la production car l'échec de credentials est vérifiable dès l'étape de setup, avant tout appel API.
- **2026-08-06 (~11:36 UTC, run indépendant)** — Aucune vidéo produite. Score global : N/A. Décision : **annulé** — même cause racine confirmée à nouveau (voir ci-dessus). Aucune tentative de génération TTS ni d'upload YouTube pour éviter un appel réseau inutile avec des credentials absents.
