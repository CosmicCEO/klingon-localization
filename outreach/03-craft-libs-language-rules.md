# Draft: comment on storytold/craft-libs#198 (suite language support)

**Post as:** @cosmicceo
**Where:** a comment on https://github.com/storytold/craft-libs/issues/198
**Send after:** the craft-i18n issue (`01`) is posted, so you can link it
**Why here:** sorting, search folding and plurals live in the shared `craft-i18n` runtime crate, so fixing them once fixes every app.

---

Hi! We're adding Klingon (`tlh`) across the Crafting Apps (<LINK TO CRAFT-I18N ISSUE>). Klingon has no standard locale data (CLDR/ICU4X), so it needs a few rules the runtime can't get from there. Raising them here since this plan covers sorting, search and plurals for every app:

1. **Sorting:** a b ch D e gh H I j l m n ng o p q Q r S t tlh u v w y '
   - `ch`, `gh`, `ng` and `tlh` are single letters; `'` is a letter
   - `q` and `Q` are different letters, as are `S`, `D`, `H` and `I`
2. **Search:** case-insensitive search shouldn't fold `q` into `Q` (or `S`/`s`, `D`/`d`, `H`/`h`, `I`/`i`) for `tlh` text, since that changes the word.
3. **Plurals:** no CLDR rule exists. Klingon interface strings work fine with one form, like Japanese. Could the runtime and the craft-i18n checker treat `tlh` as one form (`other`)?
4. **Numbers and dates:** plain digits and the root locale's formats are fine.

If a small custom collation table for `tlh` would help, I'm happy to write it and the tests. Plan and tracker: https://github.com/CosmicCEO/klingon-localization

---
