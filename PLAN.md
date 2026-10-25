# Klingon (tlh) Localization for WordCraft — Project Plan

**Owner:** [@cosmicceo](https://github.com/cosmicceo)
**Status:** Planning · last updated 2026-10-25
**Target app:** [WordCraft](https://github.com/storytold/wordcraft), the open-source Word clone (Rust, MIT OR Apache-2.0)
**Translations live in:** [storytold/craft-i18n](https://github.com/storytold/craft-i18n)
**Fallback target:** LibreOffice Writer

---

## 1. Goal

Ship a Klingon interface for WordCraft:

- standard Klingon (ta' Hol), written in Latin letters (`tlh`)
- reviewed by fluent speakers
- accepted upstream so it ships in official releases

The shared catalog also gives a head start on Klingon in the sibling apps (PdfCraft, PhotoCraft, VectorCraft and others).

## 2. Communication path

All project communication runs through **GitHub, under @cosmicceo**.

| What | Where |
|---|---|
| Project hub: this plan, glossary, status, decisions | [`CosmicCEO/klingon-localization`](https://github.com/CosmicCEO/klingon-localization) (public) |
| Questions, glossary debates, task tracking | GitHub Issues on the hub repo, labelled `tlh` |
| Upstream proposals and PRs | Opened by @cosmicceo on `storytold/craft-i18n` and `storytold/wordcraft` |
| Outreach to collaborators | Public GitHub issues or discussions, posted by @cosmicceo, each linking back to the hub |

Rules:
- Contact people only on GitHub, in public threads. Don't look up personal contact details.
- Every outreach post links to this plan, so anyone can see the whole picture.
- Record decisions (dialect, script, glossary terms) in the hub's `DECISIONS` section below, with the issue link.

## 3. Language and dialect

| Decision | Choice |
|---|---|
| Variety | **ta' Hol**, the standard dialect in Marc Okrand's works. Regional dialects are out of scope: they have too little vocabulary. |
| Locale code | `tlh` (ISO 639-2/3). A pIqaD version, if made later, would be `tlh-piqd`. |
| Script | Latin spelling first. pIqaD is not in standard Unicode (private-use area only), so it comes later. |
| Authorities | *The Klingon Dictionary*, *Klingon for the Galactic Traveler*, new words from each qep'a' gathering, the Klingon Language Institute (KLI). |
| Machine-readable data | [De7vID/klingon-assistant-data](https://github.com/De7vID/klingon-assistant-data) (Apache-2.0, matches WordCraft's license). |

**Legal guardrails**
- Paramount owns the "Klingon" and Star Trek trademarks. The dictionary text is copyrighted. No court has decided whether the language itself can be copyrighted.
- Use Klingon words. Don't copy dictionary definitions, and don't use Star Trek logos or branding.
- Name the pack plainly: "Klingon (tlh)".
- Get a short legal opinion before promoting a public release.

**craft-i18n copying rule:** write every translation from the meaning of the English text. Never copy another product's translated interface; earlier Klingon interfaces (Bing, Google) are off-limits. Dictionaries are references, not interfaces, so they're fine.

## 4. Why WordCraft

- **Small job:** about 3,650 strings in total (~1,260 shared, ~2,390 WordCraft-only). LibreOffice has tens of thousands.
- **Simple format:** one string per line, `context ⇥ English ⇥ translation`. Editable in GitHub's web editor.
- **Easy entry:** `tools/new_locale.py tlh "tlhIngan Hol" wordcraft` creates the starter files. Partial catalogs are accepted, and missing strings show in English.
- **AI-assisted translation accepted** if recorded in `ATTRIBUTION.md`.

**Risks**
- Pre-alpha (about 60% ready for real work by its own estimate), and strings change daily.
- Most of the work comes from one developer plus AI agents.
- Mitigation: keep the glossary in the hub repo, in a format that also works for LibreOffice.

## 5. People

| Role | Who | Why | How to reach |
|---|---|---|---|
| Project lead | @cosmicceo | Owns the plan, opens all upstream issues and PRs | — |
| **Co-author: Klingon glossary and review** (invited) | [@De7vID](https://github.com/De7vID) | Maintains the boQwI' dictionary data (6,200+ commits, Apache-2.0), has translation guidelines, long active in the Klingon community | Public issue on `De7vID/klingon-assistant-data` (draft in `outreach/02-de7vid-coauthor.md`) |
| Upstream gatekeeper | Martin Ball (craft-i18n maintainer) | Merges translation PRs; wrote the "Add a language" guide | The new-language issue on `storytold/craft-i18n` (draft in `outreach/01-craft-i18n-new-language.md`) |
| WordCraft developers (if code changes are needed) | WordCraft i18n contributors (Valentin Klein, Dmitrii Khlapov) | Made most of WordCraft's language changes | Issue on `storytold/wordcraft` (draft in `outreach/03-wordcraft-case-handling.md`) |
| Extra reviewers | Klingon Language Institute community | Fluent reviewers | KLI channels, linking to the hub |
| Translators | 2–3 fluent volunteers | Bulk translation | Recruited through the hub's Issues |

## 6. Phases

### Phase 0 — Set up and reach out (week 1–2)
- [ ] Create a `tlh` label and a pinned "Start here" issue in the hub repo
- [ ] Post the craft-i18n new-language issue for `tlh` (`outreach/01`)
- [ ] Invite @De7vID as co-author (`outreach/02`), linking the craft-i18n issue
- [ ] Ask WordCraft about Klingon's capital letters and plural forms (`outreach/03`)
- [ ] Request a short legal opinion on naming and dictionary use

**Exit:** craft-i18n maintainer agrees to accept `tlh`; co-author answer received (yes / no / reviewer only).

### Phase 1 — First pull request (week 2–3)
- [ ] Run `tools/new_locale.py tlh "tlhIngan Hol" wordcraft` in a fork of craft-i18n
- [ ] Translate the `@id language.name` row and the ~200 most visible strings (File, Home tab, save, open, print)
- [ ] Add the `tlh` row to `ATTRIBUTION.md` (translators, AI use, review status)
- [ ] Open PR `tlh: WordCraft catalog (starter)`. Ask for `tlh` in WordCraft's `LANGUAGES` list

**Exit:** starter PR merged; `tlh` selectable in a WordCraft build.

### Phase 2 — Glossary of new words (week 2–5, overlaps Phase 1)
- [ ] Extract the ~300–500 core interface terms (file, save, font, paragraph, undo…)
- [ ] For each term, in order of preference:
  1. an existing Okrand word
  2. a word built from Okrand's own roots and suffixes
  3. a short descriptive phrase
  4. never a new root word
- [ ] Debate each disputed term in a hub issue; the co-author has the final say
- [ ] Freeze glossary v1.0 in `glossary.tsv` at the repo root

**Exit:** glossary v1.0 frozen and reviewed by at least one fluent speaker.

### Phase 3 — Bulk translation (week 5–10)
- [ ] `common.tsv` first (every app uses it), then `wordcraft.tsv`
- [ ] AI may draft; a human checks every row against the glossary
- [ ] Klingon puts the object before the verb; check that `{placeholders}` still read correctly
- [ ] Open PRs in batches of about 300 rows, so reviews stay small

**Exit:** 100% of the WordCraft catalog translated; CI (`cargo test --workspace`) green.

### Phase 4 — Language support in the app (parallel, needs upstream developers)
- [ ] Capital letters: turn off auto-capitalization and the sentence-capital grammar check for `tlh` (q ≠ Q)
- [ ] Sorting: a b ch D e gh H I j l m n ng o p q Q r S t tlh u v w y ' (ch, gh, ng and tlh are single letters, and ' is a letter)
- [ ] Plurals: agree on a single plural form for `@plural` rows, since the standard plural tables have no Klingon entry
- [ ] Later: a Hunspell spell checker built from the boQwI' data (license permitting)
- [ ] Later: a `tlh-piqd` catalog plus a bundled pIqaD font

### Phase 5 — Review and release (week 10–12)
- [ ] Fluent reviewers check the running app: cut-off text, sorting, search, shortcuts
- [ ] Update `ATTRIBUTION.md` with the review status
- [ ] Translation appears in a release once WordCraft's `craft-i18n.rev` pin reaches the merge commit
- [ ] Announce through the hub and the KLI community

## 7. Fallback

If WordCraft stalls or declines:
1. Keep `tlh` in craft-i18n; it can wait there for the app.
2. Port the frozen glossary to LibreOffice: propose on `l10n@global.libreoffice.org`, translate in its Weblate.
3. Last resort: ship our own language pack from the hub repo.

## 8. Decisions log

| Date | Decision | Link |
|---|---|---|
| 2026-10-25 | Target WordCraft via craft-i18n; LibreOffice is the fallback | — |
| 2026-10-25 | Dialect ta' Hol, Latin script, code `tlh` | — |
| 2026-10-25 | All communication through @cosmicceo on GitHub | — |

## Sources
- WordCraft: https://github.com/storytold/wordcraft
- craft-i18n (format, new-language guide): https://github.com/storytold/craft-i18n
- boQwI' data: https://github.com/De7vID/klingon-assistant-data
- Coverage: https://decrypt.co/380991/developer-cloned-photoshop-ai-just-did-same-microsoft-office
