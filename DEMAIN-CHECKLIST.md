# Demain 02/08 - Checklist Rapide
## Ce qui va se passer et comment valider

---

## 🚀 Dimanche 02/08

### 23h59 GMT (= 01h59 lundi matin Paris)
Routine analytique génère **rapport-2026-08-02** dans 3 formats:
- `.docx` (Word)
- `.pdf` (PDF)
- `.pptx` (PowerPoint)

**Où vérifier:** `livrables/youtube/.../rapports/`

**Commande rapide:**
```bash
ls -la livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/rapports/
```

**Si fichiers là:** ✅ Rapport OK, passe à lundi  
**Si vide:** ❌ YouTube Analytics a échoué, check logs cloud Anthropic

---

## 📋 Lundi 03/08

### 9h00 GMT (= 11h Paris)
Routine recommandations lit le rapport et génère **directives-production-2026-08-03.yaml**

**Où vérifier:** `livrables/youtube/.../directives/`

**Commande rapide:**
```bash
ls -la livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/directives/
# Cherche: directives-production-2026-08-03.yaml
```

**Si fichier là:** ✅ Directives OK  
**Si vide:** ❌ Recommandations a échoué (probable: rapport absent)

### 10h00 GMT (= 12h Paris)
Routine production lit directives et génère **2 shorts pour 03/08**

**Où vérifier:** `livrables/youtube/.../videos_prod/2026-08-03/`

**Commande rapide:**
```bash
ls -la livrables/youtube/2026-07-27_chaine-youtube-tech-ia-automatisee/videos_prod/2026-08-03/
# Cherche: 2 fichiers metadata/script
```

**Si 2 shorts là:** ✅ Production lit directives = Tout OK!  
**Si vide ou erreurs:** ❌ Production n'a pas chargé directives

---

## 📚 Docs créés pour toi (01/08)

| Fichier | Utilité | Lire quand |
|---------|---------|-----------|
| **FLOW-ANALYTIQUE-PRODUCTION.md** | Vue d'ensemble complète (dimanche → lundi → quotidien) | Maintenant (pour comprendre) |
| **ROUTINE-RECOMMANDATIONS-PROMPT.md** | Prompt détaillé pour routine analytique | Si routine échoue (debugging) |
| **directives-production-2026-08-03.yaml** | Template exemple avec données réalistes | Lundi 09h30 (comparer avec généré) |
| **VALIDATION-ROUTINE-ANALYTIQUE.md** | Checklist détaillée validation dimanche + lundi | Dimanche soir (avant de dormir) |
| **PRODUCTION-CONFIG.yaml** (amélioré) | Config centrale, section directives_hebdomadaire ajoutée | Lundi 10h30 (vérifier production lit config) |

---

## 🎯 Résumé: Pourquoi cette amélioration?

**Avant 01/08:**
- Production générait 2 shorts/jour sans data
- CPM moyen ~1.5, pas d'optimisation
- Sujets = actu brute sans priorisation

**Après 01/08:**
- Rapport dimanche 23h59 → stats semaine (retention, CPM, abos)
- Directives lundi 9h → insights actionnables (angles, durée, hooks, CPM target)
- Production lundi 10h → read directives + priorise sujets rentables
- Impact: CPM +20-30% estimé, retention +5-10%

**Pour toi:**
- 0 action manuelle requise (tout automatisé)
- Directives générées auto = intelligence semaine précédente
- Feedback loop fermée: mauvaise semaine → directives améliorées → meilleure semaine

---

## ⚠️ Cas problèmes rapides

### Rapport absent lundi matin
- [ ] Vérifier YouTube Analytics API activée
- [ ] Vérifier token `YOUTUBE_ANALYTICS_REFRESH_TOKEN` dans `.env`
- [ ] Vérifier compte Google Cloud a facturation
- [ ] Workaround: copier `rapport-template.docx` → `rapport-2026-08-02.docx` (test)

### Directives absent lundi 10h
- [ ] Vérifier rapport du 02/08 existe
- [ ] Si existe, check routine recommandations logs (Anthropic)
- [ ] Workaround: copier `directives-production-2026-08-03.yaml` (template) en vrai fichier

### Production ignore directives lundi 10h
- [ ] Vérifier PRODUCTION-CONFIG.yaml section `directives_hebdomadaire`
- [ ] Vérifier path: `"directives/directives-production-YYYY-MM-DD.yaml"`
- [ ] Check logs production "Error loading directives"
- [ ] Workaround: hardcoder angles dans PRODUCTION-CONFIG.yaml pour jour

---

## 🔄 Après lundi (prochaines étapes)

**Mardi 04/08:** Observer production (2 shorts générés)
- [ ] Vérifier sujets ∈ angles_privilegier (pas crypto, pas memes)
- [ ] Vérifier durée ~50s
- [ ] Vérifier hooks "surprise/contre-intuitif"

**Vendredi 07/08:** Fin semaine 1
- [ ] 10 shorts générés (lun-ven, 2/jour)
- [ ] 2 shorts validés/publiés (optionnel: tu décides)

**Dimanche 09/08 23h59:** Rapport semaine 2
- [ ] Vérifier rapport du 09/08 existe
- [ ] Comparer avec rapport du 02/08 (progression?)

**Lundi 10/08 9h:** Directives semaine 2
- [ ] Vérifier directives du 10/08 générées
- [ ] Vérifier si angles/CPM/retention améliorés

**Succès = boucle fermée fonctionne!**

---

## 📞 Questions rapides avant demain?

- À quoi s'attendre si rapport vide?
- Comment accéder logs Anthropic si routine échoue?
- Workarounds: template de rapport/directives fournis → peux les utiliser pour tester

---

**TL;DR:**
- Dimanche 23h59: Rapport généré
- Lundi 9h: Directives générées
- Lundi 10h: Production lit directives + fait 2 shorts optimisés
- 0 action manuelle, tout auto

**Ressources:** Lire FLOW-ANALYTIQUE-PRODUCTION.md pour comprendre, VALIDATION-ROUTINE-ANALYTIQUE.md pour checklist détaillée.

**Prochaine update:** Lundi soir (01/08 22h) après validation première boucle.
