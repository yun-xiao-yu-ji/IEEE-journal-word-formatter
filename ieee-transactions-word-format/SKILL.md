---
name: ieee-transactions-word-format
description: Format existing manuscript Word documents into the bundled IEEE Transactions journal Word template. Use when Codex needs to convert, reformat, or generate a .docx article for IEEE Transactions/Journals style from an unformatted or institution-formatted SCI manuscript, including title, authors, abstract, index terms, sections, equations, figures, tables, acknowledgments, appendices, and references.
---

# IEEE Transactions Word Format

## Purpose

Use this skill to create an IEEE Transactions-style Word document from an existing manuscript. The source manuscript may already contain normal SCI-paper content such as title, authors, abstract, keywords, introduction, methods, experiments, conclusion, acknowledgments, and references, but may not follow IEEE Word formatting.

Always use the bundled official Word template in `assets/ieee-transactions-template.docx` as the formatting source. Do not recreate IEEE formatting from memory when the template is available.

## Required Assets

- `assets/ieee-transactions-template.docx`: the IEEE Transactions Word template copied from the user-provided official template.
- `references/template-style-notes.md`: style and structure notes extracted from the template.
- `scripts/format_ieee_transactions_docx.py`: helper script for converting a source `.docx` manuscript into a new IEEE-style `.docx`.

## Workflow

1. Inspect the user's source manuscript before converting.
   - Identify title, authors, abstract, index terms/keywords, major sections, subsections, equations, figures, tables, acknowledgments, appendices, and references.
   - Identify support/funding statements, corresponding-author notes, equal-contribution notes, author affiliations, and author e-mail addresses.
   - Identify the citation style used in the source manuscript: IEEE numeric citations such as `[1]`, numbered references without in-text links, or author-year citations such as `(Smith, 2020)` / `Smith et al. (2020)`.
   - Preserve scientific content. Formatting conversion must not rewrite claims, results, citations, equations, or references unless the user explicitly asks for editing.

2. Create the IEEE formatted document from the bundled template.
   - Prefer running `scripts/format_ieee_transactions_docx.py`.
   - Use the template as the base document so page size, margins, built-in styles, headers, footers, and IEEE-specific style definitions are inherited.
   - If the script misses unusual content, patch the generated document with `python-docx` while still using the same template and styles.

3. Apply template styles by semantic role.
   - Title: use ordinary Word text with IEEE title formatting. If the bundled template's `Title` or `Authors` style contains `w:framePr`, remove that frame setting in the generated output so neither the title nor author-name line is a text box/floating frame.
   - Authors: `Authors`; include only the author-name line below the title. Remove affiliation markers such as `a,b,c,d` from the visible author line, while preserving corresponding-author marks such as `*` when present.
   - Abstract: `Abstract`
   - Index terms or keywords: `IndexTerms`
   - Main numbered sections: `Heading 1`
   - Lettered subsections: `Heading 2`
   - Body text: `Text`
   - Equations: `Equation`
   - Figure captions: `Figure Caption`
   - Table titles: `Table Title`
   - References: `References`
   - Reference heading: `Reference Head`

4. Place author details and support information in the first-page footnote.
   - Do not place author affiliations, addresses, e-mail addresses, funding/support statements, corresponding-author notes, equal-contribution notes, or supplemental-material notes as ordinary paragraphs below the title.
   - Use the IEEE template's first footnote area for this content.
   - Put financial support first, then corresponding-author/equal-contribution notes, then current author affiliations and addresses.
   - If no submission date is provided, use a neutral placeholder such as `Manuscript received [date]; revised [date]; accepted [date].`
   - Move source `Funding` content into this first footnote instead of leaving it as an end-section.
   - Keep ordinary acknowledgments for non-financial thanks unless the user asks to remove them.

5. Enforce IEEE article order unless the user requests otherwise.
   - Title
   - Author names
   - First-page footnote containing author affiliations and support information
   - Abstract
   - Index Terms
   - Introduction
   - Main body sections
   - Conclusion
   - Appendix, if present
   - Acknowledgment, if present
   - References

   The first section should be single-column and contain only the title and author-name line. Put a continuous section break in a blank paragraph after the author line, then place the first-footnote marker at the start of the following two-column section before `Abstract—`. This lets the abstract, index terms, first-page footnote display, and main text integrate in the template's two-column area.

6. Format citations and references as IEEE.
   - If the source already uses numeric citations, preserve the citation numbers and do not duplicate reference numbers.
   - If the source references are unnumbered but in-text numeric citations exist, number the reference entries once in IEEE bracket form.
   - If the source uses author-year citations, map each author-year citation to a numbered IEEE reference entry and replace in-text citations with bracketed numbers, e.g. `[1]`.
   - Add internal hyperlinks from in-text numeric citations to the corresponding reference entry when generating `.docx`.
   - Use `References` style for reference entries, but remove any automatic numbering (`w:numPr`) inherited from the style or paragraph. The visible reference label must be text only, e.g. `[1]`, never Word auto-numbering plus `[1]`.
   - Avoid manually adding a second number when Word/list numbering or an existing bracketed number already exists.

7. Apply the IEEE drop-cap opening.
   - Keep only the title and author-name line in the single-column front section. The first-footnote marker, abstract, index terms, and `I. INTRODUCTION` must start in the following two-column continuous section.
   - For the first paragraph under `I. INTRODUCTION`, format the initial letter as a dropped capital following the template pattern.
   - Do not split the title or author-name line with text boxes or template frames; use ordinary Word paragraphs and direct/template text formatting.

8. Verify the output.
   - Confirm the output `.docx` opens with the expected paragraphs and styles.
   - Check that title, author-name line, first footnote, abstract, keywords, headings, body text, captions, equations, citation hyperlinks, and references are present.
   - Report any content that could not be preserved automatically, especially images, complex tables, embedded equations, comments, tracked changes, or cross-references.

## Script Usage

```bash
python scripts/format_ieee_transactions_docx.py input.docx output.docx
```

Optional metadata overrides:

```bash
python scripts/format_ieee_transactions_docx.py input.docx output.docx \
  --title "Article Title" \
  --authors "First A. Author, Second B. Author, and Third C. Author" \
  --abstract "Abstract text..." \
  --keywords "robotics, control, dynamics"
```

The script is intentionally conservative: it formats common manuscript text reliably and flags limitations for rich objects. For production submission, inspect the generated `.docx` visually and correct any source-specific figure/table/equation placement issues.

## IEEE-Specific Rules

- Use `Abstract—` and `Index Terms—` labels in the front matter.
- Number major body sections with Roman numerals when needed: `I. INTRODUCTION`, `II. METHOD`, etc.
- Number subsections with letters when needed: `A. Problem Formulation`, `B. Controller Design`, etc.
- Use `Fig.` for figure citations and captions.
- Use `Table` for table citations; table numbers should be Roman numerals.
- Place equation numbers in parentheses, e.g. `(1)`, and use the `Equation` style.
- Use IEEE numeric citations in square brackets, e.g. `[1]`, `[2]`.
- Convert unnumbered author-year citations to IEEE numeric citations unless the user asks to preserve a non-IEEE reference style.

## Limitations To Watch

The helper script uses `python-docx`, so it handles paragraph text and basic structure best. Embedded equation objects, drawings, linked images, complex tables, Word fields, tracked changes, comments, and reference manager fields may require manual post-processing. When these exist, preserve the source file, generate the formatted draft, and clearly tell the user what needs visual checking.
