# Draft: new-language issue on storytold/craft-i18n

**Post as:** @cosmicceo
**Where:** https://github.com/storytold/craft-i18n/issues/new?template=new-language.yml (fill the template fields with the text below)
**Title:** `New language: Klingon (tlh), across the Crafting Apps`

---

Hi! I'd like to add **Klingon (`tlh`)** to craft-i18n, for every Crafting App over time.

- **Locale code:** `tlh` (ISO 639-2/3), Latin script. A pIqaD version (`tlh-piqd`) may follow later.
- **Name in the language:** tlhIngan Hol
- **Plan, glossary and tracker:** https://github.com/CosmicCEO/klingon-localization

**Order of work**, so the shared catalog pays off for every app:
1. `common.tsv`, `craft-launcher.tsv`, `wordcraft.tsv`
2. `pdfcraft.tsv` (and GridCraft and DeckCraft when they join)
3. `photocraft.tsv`, `vectorcraft.tsv`
4. `filmcraft.tsv`, `cadcraft.tsv`

We keep one Klingon glossary for the whole suite, so a term means the same thing in every app.

How we'll work:
- Every row written from the English meaning, following your clean-room rule. No strings from any earlier Klingon interface.
- Vocabulary from Marc Okrand's published works, plus a reviewed glossary for interface terms.
- AI tools may draft rows. Every row is checked by a person, and `ATTRIBUTION.md` will say so.
- PRs of about 300 rows, so reviews stay small.

Questions:
1. **Plurals:** the standard plural tables have no Klingon entry. WordCraft has no `@plural` rows, but PdfCraft, PhotoCraft, VectorCraft, CADCraft and the launcher do. Would a single form (like Japanese) pass the checker for `tlh`, or does it need a rule added? I'll raise the runtime side on storytold/craft-libs#198.
2. **App language lists:** each app offers only the languages in its own list. Is it best to ask each app as its catalog lands, starting with WordCraft's `LANGUAGES`? Klingon uses Latin letters, so no new fonts are needed.
3. **Capital letters:** in Klingon, `q` and `Q` are different letters. Sorting and search are on craft-libs#198; WordCraft's AutoCorrect I'll raise on the WordCraft repo.

I'll open a small starter PR (the language name plus the most visible shared strings) once you're happy with this.

Thanks!

---
