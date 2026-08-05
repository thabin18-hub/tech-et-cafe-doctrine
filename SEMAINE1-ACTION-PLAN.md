# Semaine 1: Plan d'Action Immédiat
## De maintenant (01/08) à dimanche (04/08)

---

## 🎯 Objectif semaine

Valider que les **6 prompts** génèrent de la qualité sur cas réels + lancer Phase 1 infrastructure.

---

## 📅 Timeline détaillée

### ✅ Vendredi 01/08 (maintenant)

**TODO (30min):**
- [ ] Lis PROMPTS-STRATEGIQUES-PRODUCTION.md (comprendre les 6 prompts)
- [ ] Lis ORCHESTRATION-PROMPTS-PRODUCTION.md (comprendre l'intégration)
- [ ] Valide: tu es d'accord avec l'approche? ✓ Si oui → continue

**Décisions à prendre:**
- [ ] Approuves-tu les 6 prompts ou tu veux ajustements?
- [ ] Priorité: lancer avec Prompt #1 (Audit Niche) ou directement #2-6?

**Sortie:** Feedback Théo + validation design

---

### 📋 Samedi 02/08 (validation analytique dimanche)

**TODO:**
- [ ] Rien à faire (laisse routines tourner)
- [ ] Vers 23h59: Rapport analytique devrait être généré
- [ ] Vérifie: Fichier `rapport-2026-08-02.{docx,pdf,pptx}` existe?

**Sortie:** Rapport semaine 1 prêt pour directives lundi

---

### 🚀 Dimanche 03/08 (directives + test Prompt #1)

**TODO (2h total):**

1. **Matin (30min):** Valide directives du lundi (si générées)
   - [ ] Vérifier `directives-production-2026-08-03.yaml` existe
   - [ ] Vérifier contenu: angles privilégiés OK?

2. **Après-midi (1h30):** Run Prompt #1 (Audit Niche)
   ```
   Input: Niche Tech & Café (IA/Tech/Fondateurs)
   Agent: Claude (API ou direct chat)
   Prompt: Copie le prompt #1 depuis PROMPTS-STRATEGIQUES-PRODUCTION.md
   Output: 5 sous-niches + 3 concepts de chaîne + profil audience
   Sauvegarde: NICHE-AUDIT-2026.md
   ```

   **Commande rapide:**
   ```bash
   # Ouvre Claude chat ou API
   # Copie le texte du Prompt #1 (Tech & Café version)
   # Envoie
   # Sauvegarde réponse dans: livrables/youtube/.../NICHE-AUDIT-2026.md
   ```

3. **Soir (30min):** Crée structure dossiers
   ```bash
   mkdir -p livrables/youtube/2026-07-27.../prompts/
   cd livrables/youtube/2026-07-27.../prompts/
   
   # Crée fichiers vides (rempliras après)
   touch config.yaml
   touch 1-audit-niche.txt
   touch 2-titres-miniatures.txt
   touch 3-script-pro.txt
   touch 4-broll-decoupe.txt
   touch 5-seo-metadata.txt
   touch 6-monetization.txt
   ```

**Sortie:** NICHE-AUDIT-2026.md + dossier prompts créé

---

### 📝 Lundi 04/08 (test Prompts #2-3 + routine production)

**TODO (3h total):**

1. **10h00-10h30 (30min):** Routine production cloud démarre
   - Production génère 2 shorts (Prompts #2-4 pas intégrés encore, c'est normal)
   - Outputs: scripts + metadata dans videos_prod/2026-08-04/

2. **Après routine (1h):** Test Prompt #2 manuellement
   ```
   Input: Sujet du short généré aujourd'hui (ex: "Claude 3.5 Sonnet")
   Agent: Claude API
   Prompt: Copie Prompt #2 (titres + miniatures) depuis PROMPTS-STRATEGIQUES-PRODUCTION.md
   Output: 10 titres + 3 miniature specs
   Sauvegarde: videos_prod/2026-08-04/test-titles-thumbnails.md
   ```

   **Validation:**
   - [ ] 10 titres générés? ✓
   - [ ] Classés par psychologie (curiosité/bénéfice/contre-intuitif)? ✓
   - [ ] <60 caractères? ✓
   - [ ] 3 specs miniatures détaillées? ✓
   - [ ] Couleurs/émotions/contraste décrit? ✓

3. **Après Prompt #2 (1h30):** Test Prompt #3
   ```
   Input: Même sujet + Titre #1 généré (meilleur)
   Agent: Claude API
   Prompt: Copie Prompt #3 (script pro)
   Output: Script complet 50s avec hook + pattern interrupts
   Sauvegarde: videos_prod/2026-08-04/test-script.txt
   ```

   **Validation:**
   - [ ] Hook 15s percutant? ✓
   - [ ] Pattern interrupts ~90s? ✓
   - [ ] Langage simple + actif? ✓
   - [ ] Durée ~50s? ✓
   - [ ] CTA organique? ✓

4. **Soir (30min):** Review + feedback
   - Comparer titres générés vs celui produit par routine
   - Comparer script généré vs celui produit par routine
   - Questions: Qualité OK? Faut-il ajuster les prompts?

**Sortie:** Test results + feedback pour optimisation

---

### 🎬 Mardi 05/08 (test Prompts #4-5-6)

**TODO (3h total):**

1. **Matin (1h):** Test Prompt #4 (Découpage B-Roll)
   ```
   Input: Script généré lundi (Prompt #3)
   Agent: Claude API
   Prompt: Copie Prompt #4 (découpage technique)
   Output: Tableau CSV avec timecode/texte/visuels/B-roll/sound design
   Sauvegarde: videos_prod/2026-08-04/test-storyboard.csv
   ```

   **Validation:**
   - [ ] Tableau bien formé? ✓
   - [ ] Timecodes corrects? ✓
   - [ ] Pattern interrupts @~90s? ✓
   - [ ] Suggestions B-roll précises? ✓
   - [ ] Sound design descriptif? ✓

2. **Après-midi (1h):** Test Prompt #5 (SEO/Metadata)
   ```
   Input: Titre + Sujet
   Agent: Claude API
   Prompt: Copie Prompt #5 (description + tags + pinned)
   Output: Description 300w + 15 tags + pinned comment
   Sauvegarde: videos_prod/2026-08-04/test-seo-metadata.md
   ```

   **Validation:**
   - [ ] Description 300w? ✓
   - [ ] Keywords dans phrases 1-2? ✓
   - [ ] 15 tags pertinents? ✓
   - [ ] Pinned comment engageant? ✓

3. **Soir (1h):** Test Prompt #6 (Monétisation)
   ```
   Input: Sujet + Audience profile
   Agent: Claude API
   Prompt: Copie Prompt #6 (stratégie monétisation)
   Output: Affiliations recommandées + CTA placements
   Sauvegarde: videos_prod/2026-08-04/test-monetization.md
   ```

   **Validation:**
   - [ ] 3-5 affiliations proposées? ✓
   - [ ] Commissions + CTR estimés? ✓
   - [ ] High-ticket offers? ✓
   - [ ] CTA placements naturels? ✓

**Sortie:** Tous les 6 prompts testés + résultats documentés

---

### 📊 Mercredi 06-Jeudi 07/08 (Ajustements + Phase 2 Prep)

**TODO (2h total):**

1. **Analyse feedback** (30min)
   - Qualité prompt #1 (audit niche): Bon? À améliorer?
   - Qualité prompts #2-6 sur cas réels: Bon? À affiner?
   - Quels prompts besoin d'ajustements?

2. **Adjustments** (1h)
   - Si prompts OK: Aucun changement
   - Si prompts faibles: Affiner texte prompt (add examples, clarify, etc)
   - Versioning: v1.0 → v1.1 des prompts

3. **Prep Phase 2** (30min)
   - Créer fichiers `.txt` dans dossier `prompts/` avec texte exact de chaque prompt
   - Compléter `config.yaml` (timings, validations, etc)
   - Prep pour intégration Cloud routine

**Sortie:** Prompts finalisés v1.0 + dossier prompts rempli

---

### ✨ Vendredi 08/08 (Bilan semaine 1)

**TODO (1h):**

1. **Synthèse** (30min)
   - Quels prompts marchent? ✓
   - Quels prompts need tweaks? ⚠️
   - Timeline Phase 2 (cloud integration): Semaine prochaine OK?

2. **Documentation** (30min)
   - Créer WEEK1-RESULTS.md avec:
     - Examples d'output (3 meilleurs + 3 problématiques)
     - Feedback Théo
     - Adjustments pour v1.1
     - Timeline Phase 2

**Sortie:** Rapport semaine 1 + readiness check Phase 2

---

## 📋 Checklist Résumé

### Avant lundi (01-03/08)
- [ ] Lire PROMPTS-STRATEGIQUES-PRODUCTION.md
- [ ] Lire ORCHESTRATION-PROMPTS-PRODUCTION.md
- [ ] Run Prompt #1 (Audit Niche) manuellement
- [ ] Créer dossier prompts/

### Lundi-mardi (04-05/08)
- [ ] Test Prompts #2-3 (titres + script)
- [ ] Test Prompts #4-5-6 (découpage + SEO + monétisation)
- [ ] Valider output format

### Mercredi-jeudi (06-07/08)
- [ ] Analyser résultats
- [ ] Affiner prompts si besoin (v1.0 → v1.1)
- [ ] Remplir dossier prompts/ avec fichiers .txt

### Vendredi (08/08)
- [ ] Synthèse + Phase 2 readiness

---

## 🎯 Succès = Quoi?

**Fin semaine 1 (dimanche 04/08):**
- ✅ Audit Niche complété (5 sous-niches + 3 concepts)
- ✅ Prompts #2-6 testés sur cas réels
- ✅ Output format validé (parseable)
- ✅ Dossier prompts/ créé + rempli

**Si tout OK:** Prêt pour Phase 2 (Cloud integration) semaine prochaine

**Si problèmes:** Ajuster prompts v1.0 → v1.1, retester

---

## 📞 Questions fréquentes

**Q: Je dois tout faire en manuel (sans API)?**  
A: Oui cette semaine. Utilise Chat Claude direct (claude.ai). Phase 2 = API automation.

**Q: Et si Prompt #1 output n'est pas bon?**  
A: Normal première itération. Affine le texte prompt (add examples, clarify), reteste.

**Q: Timing réaliste?**  
A: 8-10h distribuées sur semaine (30min/jour).

**Q: Quand intégrer à la routine production cloud?**  
A: Phase 2 (semaine prochaine). Phase 1 = validation qu'output est bon.

---

## 🚀 TL;DR

**Cette semaine:** Test les 6 prompts manuellement, valide qualité, prépare infrastructure.  
**Semaine prochaine:** Intègre dans routine production cloud (auto tous les jours).  
**Impact attendu:** 30% gain productivité + 20% meilleure qualité scripts + +15% titre CTR.

---

**Ready? Allons-y! 🎬**

Confirmation:
- [ ] Oui, lance Phase 1
- [ ] Non, ajuste d'abord
