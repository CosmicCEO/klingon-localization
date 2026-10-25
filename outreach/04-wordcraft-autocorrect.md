# Draft: language-support issue on storytold/wordcraft

**Post as:** @cosmicceo
**Where:** https://github.com/storytold/wordcraft/issues/new
**Send after:** the craft-i18n issue (`01`) has a positive answer
**Title:** `Klingon (tlh): capital letters and the language list`

---

We're adding a Klingon (`tlh`) interface through craft-i18n (<LINK TO CRAFT-I18N ISSUE>). Suite-wide sorting, search and plurals are raised on storytold/craft-libs#198. Two things are specific to WordCraft:

1. **Capital letters change meaning.** `q` and `Q` are different letters, and so are `S`, `D`, `H` and `I` versus their lowercase forms. Like the Polish `i` fix (#835), Klingon text shouldn't get:
   - AutoCorrect's sentence capitalization or CAPS LOCK fixes
   - the grammar check's missing sentence capital
   - Change Case

   (Typing two capitals in a row can be correct.)
2. **Interface list:** please add `tlh` to `LANGUAGES` in `crates/ui-egui/src/i18n/mod.rs` once the starter catalog merges. It uses Latin script; `editing_lang` can stay `None` until there's a spell checker.

Happy to test builds. Plan: https://github.com/CosmicCEO/klingon-localization

---
