# Draft: new-language issue on storytold/craft-i18n

**Post as:** @cosmicceo
**Where:** https://github.com/storytold/craft-i18n/issues/new?template=new-language.yml (fill the template fields with the text below)
**Title:** `New language: Klingon (tlh)`

---

Hi! I'd like to add **Klingon (`tlh`)**, starting with WordCraft.

- **Locale code:** `tlh` (ISO 639-2/3), Latin script. A pIqaD version (`tlh-piqd`) may follow later.
- **Name in the language:** tlhIngan Hol
- **Apps:** WordCraft first, then the shared `common.tsv`
- **Plan and glossary:** https://github.com/CosmicCEO/klingon-localization

How we'll work:
- Every row written from the English meaning, following your clean-room rule. No strings from any earlier Klingon interface.
- Vocabulary from Marc Okrand's published works, plus a reviewed glossary for interface terms.
- AI tools may draft rows. Every row is checked by a person, and `ATTRIBUTION.md` will say so.

Questions:
1. **Plurals:** the standard plural tables have no Klingon entry. Is a single form (like Japanese) okay for `@plural` rows?
2. **WordCraft's `LANGUAGES`:** could `tlh` be added once a starter catalog lands? Klingon uses Latin letters, so no new fonts are needed.
3. **Capital letters:** in Klingon, `q` and `Q` are different letters. I'll raise the AutoCorrect and grammar side on the WordCraft repo, but wanted you to know.

I'll open a small starter PR (the language name plus the most visible strings) once you're happy with this.

Thanks!

---
