# Klingon (tlh) Localization for the Crafting Apps — Project Plan

**Owner:** [@cosmicceo](https://github.com/cosmicceo)
**Status:** Planning · last updated 2026-10-25
**Target:** the storytold Crafting Apps, starting with [WordCraft](https://github.com/storytold/wordcraft), the open-source Word clone (Rust, MIT OR Apache-2.0)
**Translations live in:** [storytold/craft-i18n](https://github.com/storytold/craft-i18n), one shared repo for every Crafting App
**Fallback target:** LibreOffice Writer

---

## 1. Goal

Ship a Klingon interface across the Crafting Apps:

- standard Klingon (ta' Hol), written in Latin letters (`tlh`)
- reviewed by fluent speakers
- accepted upstream so it ships in official releases

WordCraft comes first. The other apps follow in waves (section 6).

## 2. Why one language pack covers many apps

The Crafting Apps don't each keep their own translations. They all read from **storytold/craft-i18n**:

- `locales/tlh/common.tsv` holds the strings two or more apps share (Save, Open, Undo, Zoom, Export…). **Translate it once and every app shows it.**
- `locales/tlh/<app>.tsv` holds the strings only one app has.
- Missing strings fall back to English, so a partial pack is still useful.

What that means for us:

1. **`common.tsv` is our highest-value file.** About 1,280 strings, used by all seven apps already connected.
2. **One glossary for the whole suite.** A term like "layer" or "export" is decided once and used the same way everywhere.
3. **New apps arrive almost free.** When a new app joins craft-i18n, its shared strings already show in Klingon. That includes the Excel and PowerPoint clones, GridCraft and DeckCraft, so a full Klingon office suite is in reach.
4. **One upstream relationship.** One repo, one maintainer, one way of working, instead of a separate negotiation per app.

### The apps today (from craft-i18n, 2026-10-25)

String counts come from the most complete existing translation of each catalog.

| Catalog | Strings | What it is | Status in craft-i18n |
|---|---|---|---|
| `common.tsv` | ~1,280 | Shared by every app | — |
| `craft-launcher.tsv` | ~285 | The launcher that opens the apps | catalogs moved, app wiring pending |
| `wordcraft.tsv` | ~2,850 | Word clone | **already reads from craft-i18n** |
| `pdfcraft.tsv` | ~2,290 | PDF editor | catalogs moved, app wiring pending |
| `cadcraft.tsv` | ~1,165 | CAD | catalogs moved, app wiring pending |
| `filmcraft.tsv` | ~3,070 | Video editor | catalogs moved, app wiring pending |
| `photocraft.tsv` | ~3,360 | Photo editor | catalogs moved, app wiring pending |
| `vectorcraft.tsv` | ~5,330 | Vector illustration | catalogs moved, app wiring pending |
| **Total** | **~19,600** | | |

**Not yet in craft-i18n** (planned for later): GridCraft (Excel clone), DeckCraft (PowerPoint clone), FigCraft, LightCraft, DesignCraft, EffectCraft, SoundCraft. We don't translate these directly. They pick up `common.tsv` when they join, and we add their own catalogs then.

## 3. Communication path

All project communication runs through **GitHub, under @cosmicceo**.

| What | Where |
|---|---|
| Project hub: this plan, glossary, status, decisions | [`CosmicCEO/klingon-localization`](https://github.com/CosmicCEO/klingon-localization) (public) |
| Questions, glossary debates, task tracking | GitHub Issues on the hub repo, labelled `tlh` plus one label per app (`wordcraft`, `pdfcraft`…) |
| Translation PRs | Opened by @cosmicceo on `storytold/craft-i18n` |
| Suite-wide language rules (sorting, plurals) | A comment by @cosmicceo on [storytold/craft-libs#198](https://github.com/storytold/craft-libs/issues/198) |
| App-specific fixes and adding `tlh` to each app's language list | Issues by @cosmicceo on each app's repo |
| Outreach to collaborators | Public GitHub issues or discussions, posted by @cosmicceo, each linking back to the hub |

Rules:
- Contact people only on GitHub, in public threads. Don't look up personal contact details.
- Every outreach post links to this plan, so anyone can see the whole picture.
- Record decisions (dialect, script, glossary terms) in the decisions log below, with the issue link.

## 4. Language and dialect

| Decision | Choice |
|---|---|
| Variety | **ta' Hol**, the standard dialect in Marc Okrand's works. Regional dialects are out of scope: they have too little vocabulary. |
| Locale code | `tlh` (ISO 639-2/3). A pIqaD version, if made later, would be `tlh-piqd`. |
| Script | Latin spelling first. pIqaD is not in standard Unicode (private-use area only), so it comes later. |
| Authorities | *The Klingon Dictionary*, *Klingon for the Galactic Traveler*, new words from each qep'a' gathering, the Klingon Language Institute (KLI). |
| Machine-readable data | [De7vID/klingon-assistant-data](https://github.com/De7vID/klingon-assistant-data) (Apache-2.0, matches the Crafting Apps' license). |

**Legal guardrails**
- Paramount owns the "Klingon" and Star Trek trademarks. The dictionary text is copyrighted. No court has decided whether the language itself can be copyrighted.
- Use Klingon words. Don't copy dictionary definitions, and don't use Star Trek logos or branding.
- Name the pack plainly: "Klingon (tlh)".
- Get a short legal opinion before promoting a public release.

**craft-i18n copying rule:** write every translation from the meaning of the English text. Never copy another product's translated interface; earlier Klingon interfaces (Bing, Google) are off-limits. Dictionaries are references, not interfaces, so they're fine.

## 5. People

| Role | Who | Why | How to reach |
|---|---|---|---|
| Project lead | @cosmicceo | Owns the plan, opens all upstream issues and PRs | — |
| **Co-author: suite glossary and review** (invited) | [De7vID](https://github.com/De7vID) | Maintains the boQwI' dictionary data (6,200+ commits, Apache-2.0), has translation guidelines, long active in the Klingon community | Public issue on `De7vID/klingon-assistant-data` (draft in `outreach/02-de7vid-coauthor.md`) |
| Upstream gatekeeper | Martin Ball (craft-i18n maintainer) | Merges translation PRs for every app | New-language issue on `storytold/craft-i18n` (`outreach/01`) |
| Suite language rules | aiongg (author of craft-libs#198) | Leads sorting, plurals and number formatting for all apps | Comment on craft-libs#198 (`outreach/03`) |
| WordCraft developers | WordCraft i18n contributors (Valentin Klein, Dmitrii Khlapov) | Made most of WordCraft's language changes | Issue on `storytold/wordcraft` (`outreach/04`) |
| Extra reviewers | Klingon Language Institute community | Fluent reviewers | KLI channels, linking to the hub |
| Translators | 2–3 fluent volunteers, ideally one per wave's subject area | Bulk translation | Recruited through the hub's Issues |

Pitch for recruiting: this is a Klingon interface for a whole office and creative suite, not one app.

## 6. Phases

### Phase 0 — Set up and reach out (week 1–2)
- [ ] Create labels (`tlh`, one per app) and a pinned "Start here" issue in the hub repo
- [x] Post the craft-i18n new-language issue for `tlh`, covering all apps (`outreach/01`)
- [x] Invite De7vID as co-author of the suite glossary (`outreach/02`), linking the craft-i18n issue
- [ ] Raise Klingon sorting, plurals and capital letters on craft-libs#198 (`outreach/03`)
- [ ] Ask WordCraft about AutoCorrect and its language list (`outreach/04`)
- [ ] Request a short legal opinion on naming and dictionary use

**Exit:** craft-i18n maintainer agrees to accept `tlh`; co-author answer received (yes / no / reviewer only).

### Phase 1 — Starter pull request (week 2–3)
- [ ] Run `tools/new_locale.py tlh "tlhIngan Hol" wordcraft craft-launcher` in a fork of craft-i18n
- [ ] Translate the `@id language.name` row and the ~200 most visible strings, **taken from `common.tsv` first** (Save, Open, Undo, Copy, Paste, Zoom), then WordCraft's File and Home tabs
- [ ] Add the `tlh` row to `ATTRIBUTION.md` (translators, AI use, review status)
- [ ] Open PR `tlh: starter catalog (common, WordCraft)`. Ask for `tlh` in WordCraft's `LANGUAGES` list

**Exit:** starter PR merged; `tlh` selectable in a WordCraft build.

### Phase 2 — Suite glossary (week 2–6, overlaps Phase 1)
- [ ] Build `glossary.tsv` in this repo. Columns: `area`, `English`, `Klingon`, `how it was formed`, `status`, `issue`
- [ ] Areas: **core** (terms in `common.tsv`), **documents** (Word, PDF, later GridCraft and DeckCraft), **image** (Photo, Vector), **video** (Film), **CAD**
- [ ] Decide **core** first, about 300 terms. Other areas are decided just before their wave starts
- [ ] For each term, in order of preference:
  1. an existing Okrand word
  2. a word built from Okrand's own roots and suffixes
  3. a short descriptive phrase
  4. never a new root word
- [ ] One term means one thing across every app. If an English word has two meanings (WordCraft's "Open" spacing preset versus File › Open), give each its own term
- [ ] Debate disputed terms in hub issues; the co-author has the final say
- [ ] Freeze **core v1.0** before bulk translation of `common.tsv`

**Exit:** core glossary v1.0 frozen and reviewed by at least one fluent speaker.

### Phase 3 — Translation in waves

Each wave: freeze that area's glossary, translate, open PRs of about 300 rows, keep CI (`cargo test --workspace`) green, then ask that app to add `tlh` to its language list.

| Wave | Catalogs | Strings | Why this order | When |
|---|---|---|---|---|
| **1. Core** | `common`, `craft-launcher`, `wordcraft` | ~4,400 | `common` lifts every app; the launcher is the first screen users see; WordCraft is the goal and already connected | week 5–10 |
| **2. Documents** | `pdfcraft`; later `gridcraft`, `deckcraft` | ~2,300 now | Reuses most of WordCraft's vocabulary; completes a Klingon office suite as the other office apps join | week 10–13 |
| **3. Image** | `photocraft`, `vectorcraft` | ~8,700 | Largest wave, but the two apps share image vocabulary (layer, brush, selection, path) | week 13–20 |
| **4. Specialist** | `filmcraft`, `cadcraft` | ~4,200 | Narrow technical vocabulary; may need a translator who knows the field | week 20–24 |

**Before wave 2:** settle Klingon plurals. WordCraft has no plural strings, but PdfCraft, PhotoCraft, VectorCraft, CADCraft and the launcher do. CI checks the number of plural forms against the standard plural tables, which have no Klingon entry. A `tlh` plural rule, or an exception, must be agreed on craft-libs#198 first (`outreach/03`).

Checks in every wave:
- AI may draft; a human checks every row against the glossary
- Klingon puts the object before the verb; check that `{placeholders}` still read correctly
- Translate strings shared by two or more apps in `common.tsv`, never separately in each app file

### Phase 4 — Language support in the apps

**Suite-wide (craft-libs, benefits every app):**
- [ ] Sorting: a b ch D e gh H I j l m n ng o p q Q r S t tlh u v w y ' (ch, gh, ng and tlh are single letters, ' is a letter, and q/Q are different letters)
- [ ] Search: case-insensitive search must not treat q and Q as the same letter for `tlh`
- [ ] Plurals: a `tlh` rule (likely a single form) the checker and the apps agree on
- [ ] Numbers and dates: plain digits, neutral date format

**App by app:**
- [ ] WordCraft: no auto-capitalization, sentence-capital grammar check or Change Case for `tlh`
- [ ] Each app: add `tlh` to its own language list once its catalog lands (tracked in section 7)
- [ ] Later: a Hunspell spell checker from the boQwI' data, for WordCraft first (license permitting)
- [ ] Later: a `tlh-piqd` catalog plus a bundled pIqaD font

### Phase 5 — Review and release (after each wave)
- [ ] Fluent reviewers check each app running in Klingon: cut-off text, sorting, search, shortcuts
- [ ] Update `ATTRIBUTION.md` with the review status
- [ ] Translations appear in an app's release once its craft-i18n pin reaches the merge commit
- [ ] Watch craft-i18n's open decision on release builds. Until release workflows embed the catalogs, some app releases may ship English-only even when our catalog is merged
- [ ] Announce each wave through the hub and the KLI community

## 7. Per-app tracker

| App | Catalog translated | `tlh` in app's language list | In a release |
|---|---|---|---|
| (shared) `common` | ☐ | — | — |
| craft-launcher | ☐ | ☐ | ☐ |
| WordCraft | ☐ | ☐ | ☐ |
| PdfCraft | ☐ | ☐ | ☐ |
| PhotoCraft | ☐ | ☐ | ☐ |
| VectorCraft | ☐ | ☐ | ☐ |
| FilmCraft | ☐ | ☐ | ☐ |
| CADCraft | ☐ | ☐ | ☐ |
| GridCraft (not yet in craft-i18n) | ☐ | ☐ | ☐ |
| DeckCraft (not yet in craft-i18n) | ☐ | ☐ | ☐ |

## 8. Risks

| Risk | Mitigation |
|---|---|
| Pre-alpha apps; strings change daily | Translate `common.tsv` first (most stable); small PRs; re-sync before each wave |
| Most work comes from one developer plus AI agents | Keep the glossary here, in a format that also works for LibreOffice |
| No standard Klingon plural or sorting data | Raise on craft-libs#198 in Phase 0, before wave 2 needs it |
| Some apps not wired to craft-i18n yet | Our catalogs wait in craft-i18n and show once the app connects |
| Release builds may not embed catalogs yet | Track craft-i18n's open decision; test release builds, not just dev builds |
| ~19,600 strings is a lot for volunteers | Waves let us stop after any wave with a useful result; wave 1 alone delivers a Klingon WordCraft |

## 9. Fallback

If the Crafting Apps stall or decline:
1. Keep `tlh` in craft-i18n; it can wait there for the apps.
2. Port the frozen glossary to LibreOffice: propose on `l10n@global.libreoffice.org`, translate in its Weblate.
3. Last resort: ship our own language pack from the hub repo.

## 10. Decisions log

| Date | Decision | Link |
|---|---|---|
| 2026-10-25 | Target WordCraft via craft-i18n; LibreOffice is the fallback | — |
| 2026-10-25 | Dialect ta' Hol, Latin script, code `tlh` | — |
| 2026-10-25 | All communication through @cosmicceo on GitHub | — |
| 2026-10-25 | Scope widened to every Crafting App via the shared catalog; `common.tsv` first; one suite glossary; four waves | — |

## Sources
- craft-i18n (format, apps, roadmap): https://github.com/storytold/craft-i18n
- Suite language-support plan: https://github.com/storytold/craft-libs/issues/198
- WordCraft: https://github.com/storytold/wordcraft
- boQwI' data: https://github.com/De7vID/klingon-assistant-data
- Coverage: https://decrypt.co/380991/developer-cloned-photoshop-ai-just-did-same-microsoft-office
