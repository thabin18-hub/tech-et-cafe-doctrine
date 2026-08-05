# 📋 Dossier Prompts - Tech & Café
## 6 Prompts Stratégiques Production YouTube

---

## 🎯 Utilisation Rapide

**Cette semaine (Phase 1):** Copie le contenu de chaque `.txt` → Colle dans Claude Chat

**Semaine prochaine (Phase 2):** API Claude automatisera les appels

---

## 📁 Fichiers

| Fichier | Prompt | Quand | Durée |
|---------|--------|-------|-------|
| **1-audit-niche.txt** | Audit Niche | 1x trimestriel | 30min |
| **2-titres-miniatures.txt** | Titres/Miniatures | Chaque vidéo | 5min |
| **3-script-pro.txt** | Script Pro | Chaque vidéo | 30min |
| **4-broll-decoupe.txt** | Découpage B-Roll | Chaque vidéo | 20min |
| **5-seo-metadata.txt** | SEO/Metadata | 24h avant pub | 10min |
| **6-monetization.txt** | Monétisation | Chaque 3-4 vidéos | 10min |
| **config.yaml** | Config centralisée | Référence | N/A |

---

## 🚀 Phase 1: Test Manual (Cette semaine 01-08/08)

**Dimanche 02/08:**
- Attendre rapport analytique (23:59 GMT)

**Lundi 03/08:**
- Attendre directives (9h GMT)
- Tester **Prompt #1** (Audit Niche)
  ```bash
  1. Ouvre Claude (claude.ai)
  2. Copie contenu de 1-audit-niche.txt
  3. Envoie
  4. Sauvegarde réponse → NICHE-AUDIT-2026.md
  ```

**Lundi-Mardi (04-05/08):**
- Teste **Prompts #2-3** (titres + script) sur sujet réel
  ```
  Sujet choisi (ex: "Claude 3.5 Sonnet")
  → Prompt #2: 10 titres + 3 miniatures
  → Prompt #3: Script complet 50s
  ```

**Mercredi-Jeudi (06-07/08):**
- Teste **Prompts #4-5-6** (découpage + SEO + monétisation)

**Vendredi (08/08):**
- Synthèse + Feedback
- Si tout OK: Go Phase 2
- Si problèmes: Ajuster prompts (v1.0 → v1.1)

---

## 🔄 Phase 2: Cloud Integration (Semaine 2, 11-18/08)

Intégrer dans routine production cloud (`trig_01QTPw2RxoroMRcD4E3FthPn`):

```python
# Pseudocode
for each_subject_lundi_10h:
    # Prompt #2
    titles = claude_api(prompts/2-titres-miniatures.txt, context=subject)
    
    # Prompt #3
    script = claude_api(prompts/3-script-pro.txt, context=subject + best_title)
    
    # Prompt #4
    storyboard = claude_api(prompts/4-broll-decoupe.txt, context=script)
    
    # Montage + Upload
    video = montage(script, storyboard)
    
    # Scheduled 24h before publication
    schedule_delayed_task({
        # Prompt #5
        seo_meta = claude_api(prompts/5-seo-metadata.txt, context=title+subject),
        # Prompt #6
        monetization = claude_api(prompts/6-monetization.txt, context=subject)
    })
```

---

## 📊 Performance Tracking

**After Phase 1 (08/08):**
- [ ] All 6 prompts tested
- [ ] Output format validated
- [ ] Quality acceptable
- [ ] Ready Phase 2

**After Phase 2 (18/08):**
- [ ] Routine auto-generates daily
- [ ] 10+ videos produced with prompts
- [ ] CTR/Retention/RPM measured

**After Phase 3 (25/08+):**
- [ ] +15% titre CTR
- [ ] +5-10% retention
- [ ] +80-120% RPM

---

## 🔧 Tweaking Prompts

If a prompt output isn't good:

1. **Identify problem** (e.g., "Titles too generic")
2. **Edit `.txt` file** (add examples, clarify instructions)
3. **Increase version** (v1.0 → v1.1)
4. **Retest** on same case study
5. **Verify improvement** before using on production

Example edit:
```diff
- "Génère 10 titres"
+ "Génère 10 titres ultra-spécifiques à audience tech entrepreneurs"
+ "Examples: 'Why Claude beats GPT-4o (CEO test)'"
```

---

## 📞 Troubleshooting

**Q: Prompt output en anglais, veux français?**  
A: Edit `.txt`, add "Réponds en français" après le contexte. Reteste.

**Q: Prompt trop court / pas assez de détails?**  
A: Add examples + clarify expected output format. Reteste.

**Q: Comment passer output à Claude API (Phase 2)?**  
A: Load `.txt` file → Pass context dict → Parse JSON output → Save to files

---

## 📚 Related Documentation

- [PROMPTS-STRATEGIQUES-PRODUCTION.md](../PROMPTS-STRATEGIQUES-PRODUCTION.md) — Explications détaillées chaque prompt
- [ORCHESTRATION-PROMPTS-PRODUCTION.md](../ORCHESTRATION-PROMPTS-PRODUCTION.md) — Comment chaîner les prompts
- [SEMAINE1-ACTION-PLAN.md](../SEMAINE1-ACTION-PLAN.md) — Timeline jour par jour
- [config.yaml](config.yaml) — Configuration centralisée

---

## ✅ Checklist Démarrage

**Phase 1 Preparation:**
- [ ] Lis PROMPTS-STRATEGIQUES-PRODUCTION.md (comprendre les 6 prompts)
- [ ] Lis SEMAINE1-ACTION-PLAN.md (timeline)
- [ ] Confirme: Tu es prêt à tester manuellement? ✓

**Dimanche 02/08:**
- [ ] Rapport analytique dispo? ✓

**Lundi 03/08:**
- [ ] Directives générées? ✓
- [ ] Lance Prompt #1 (Audit Niche)

**Lundi-Jeudi:**
- [ ] Teste Prompts #2-6 sur cas réels

**Vendredi 08/08:**
- [ ] Synthèse + Feedback

---

**Status:** ✅ Ready Phase 1  
**Créé:** 01/08/2026  
**Maintenue par:** Claude (versioning)
