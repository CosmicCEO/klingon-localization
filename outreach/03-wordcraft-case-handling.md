# Draft: language-support issue on storytold/wordcraft

**Post as:** @cosmicceo
**Where:** https://github.com/storytold/wordcraft/issues/new
**Send after:** the craft-i18n issue (`01`) has a positive answer
**Title:** `Klingon (tlh): capital letters, sorting and plurals`

---

We're adding a Klingon (`tlh`) interface through craft-i18n (<LINK TO CRAFT-I18N ISSUE>). A few things in WordCraft would need a `tlh` exception, similar to the Polish `i` fix (#835):

1. **Capital letters change meaning.** `q` and `Q` are different letters, and so are `S`, `D`, `H` and `I` versus their lowercase forms. Klingon text shouldn't get:
   - AutoCorrect's sentence capitalization or CAPS LOCK fixes
   - the grammar check's missing sentence capital
   - Change Case

   (Typing two capitals in a row can be correct.)
2. **Sorting:** a b ch D e gh H I j l m n ng o p q Q r S t tlh u v w y '. `ch`, `gh`, `ng` and `tlh` are single letters, and `'` is a letter. Lowercase and uppercase versions sort as different letters.
3. **Interface list:** please add `tlh` to `LANGUAGES` in `crates/ui-egui/src/i18n/mod.rs` once the starter catalog merges. It uses Latin script; `editing_lang` can stay `None` until there's a spell checker.

Happy to test builds. Plan: https://github.com/CosmicCEO/klingon-localization

---
