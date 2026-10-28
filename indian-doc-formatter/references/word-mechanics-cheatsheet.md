# Word Mechanics Cheatsheet (python-docx)

Read the docx skill first and prefer its patterns. These notes cover the legal-specific parts.

- **Multi-level numbering:** create one abstract numbering definition in `numbering.xml` with levels 0 to 4 (`1.`, `1.1`, `1.1.1`, `(a)`, `(i)`), link it to custom paragraph styles (Clause L1 to L5), and apply styles, never typed numbers. Set `w:isLgl` on levels 1 and 2 so "1.1" stays Arabic under a lettered parent.
- **Bookmarks:** wrap each clause heading in `w:bookmarkStart` / `w:bookmarkEnd` with a name like `_Ref_Clause_4_2`.
- **Cross-references:** insert a field `REF _Ref_Clause_4_2 \r \h` so Word shows the clause number and updates on renumbering.
- **TOC:** insert field `TOC \o "1-3" \h \z \u`; set `w:updateFields` to true in `settings.xml` so Word prompts to update on open.
- **Page X of Y:** footer with fields `PAGE` and `NUMPAGES`.
- **Signature blocks:** a borderless two-column table; keep each block together (`keep_with_next` on its rows' paragraphs, `cantSplit` on rows).
- **Page breaks before schedules and annexures:** `paragraph_format.page_break_before = True` on the Schedule heading style.
- **Block quotations:** custom style with left and right indent 1.27 cm, single spacing.
- **Keep headings with text:** `keep_with_next = True` on all heading styles.
