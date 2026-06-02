# IEEE Transactions Template Style Notes

Source template:
`Transactions-template-and-instructions-on-how-to-create-your-article-formatted (4).docx`

Bundled copy:
`assets/ieee-transactions-template.docx`

## Extracted Document Facts

- Paragraph count in source template: 229
- Table count in source template: 0
- Section count in source template: 2
- Page size: letter-style page, approximately 8.5 x 11 in
- Margins from template XML:
  - top: 0.70 in
  - bottom: 0.70 in
  - left: 0.65 in
  - right: 0.65 in

## Main Styles Found In The Template

- `Title`
- `Authors`
- `Abstract`
- `IndexTerms`
- `Heading 1`
- `Heading 2`
- `Text`
- `Equation`
- `Figure Caption`
- `Table Title`
- `References`
- `Reference Head`
- `Normal`
- `List Paragraph`

## Style Mapping

Use these semantic mappings when creating a formatted manuscript:

| Manuscript content | Word style |
| --- | --- |
| Article title | `Title` |
| Author line | `Authors` |
| Abstract paragraph | `Abstract` |
| Index terms / keywords | `IndexTerms` |
| Main sections | `Heading 1` |
| Subsections | `Heading 2` |
| Body paragraphs | `Text` |
| Display equations | `Equation` |
| Figure captions | `Figure Caption` |
| Table captions/titles | `Table Title` |
| References heading | `Reference Head` |
| Reference entries | `References` |

## Template Front Matter Pattern

The template begins with:

1. Title, using `Title`
2. Author-name line, centered
3. First-page footnote mark after the author line
4. Abstract paragraph beginning with `Abstract—`
5. Index terms paragraph beginning with `Index Terms—`
6. First main section, usually `I. INTRODUCTION`

Author affiliations, current addresses, support/funding statements, corresponding-author notes, and equal-contribution notes belong in the first-page footnote, not as ordinary paragraphs below the title.
The visible author-name line should not include affiliation markers such as `a,b,c,d`; keep only names and necessary contribution/corresponding-author symbols.
The front-matter section break belongs in a blank paragraph immediately after the author line. The first-footnote marker should be in the following paragraph, after that section break, so it belongs to the two-column section. This keeps only the title and author line in the single-column section while the abstract, index terms, first-page footnote display, and main text remain integrated in the two-column section.

## Template Heading Pattern

- Main section examples use `Heading 1`, centered, Roman-numbered:
  - `I. INTRODUCTION`
  - `II. Guidelines For Manuscript Preparation`
  - `III. MATH`
- Subsection examples use `Heading 2`, lettered:
  - `A. Abbreviations and Acronyms`
  - `B. Algorithms`

The first paragraph under `I. INTRODUCTION` uses a dropped capital for the initial letter. Preserve this template pattern when generating the formatted manuscript.

The source template's `Title` and `Authors` styles may contain Word `framePr` settings. Remove those settings in generated manuscripts so the title and author-name line appear as ordinary editable text, not as text boxes or floating frames.

## Citation And Reference Pattern

- In-text IEEE citations use bracketed numbers such as `[1]`.
- Reference entries use the `References` style.
- The source template's `References` style may contain automatic numbering. Remove `w:numPr` from the generated style and reference paragraphs so the final document shows only the IEEE bracket label, e.g. `[1]`, not `1.` plus `[1]`.
- Do not duplicate existing numeric labels. If a source reference already begins with `[1]` or `1.`, normalize it once to `[1]`.
- If a source manuscript uses author-year citations, map each cited source to a numeric IEEE reference and replace the in-text author-year citation with the assigned bracketed number.
- Add internal Word hyperlinks/bookmarks from in-text citation numbers to their corresponding reference entries when possible.

## Extracted Style Details

The template defines detailed font and paragraph properties internally. Use the template styles directly instead of recreating them. Important extracted style hints:

- `Title`: 24 pt, centered.
- `Authors`: 11 pt, centered.
- `Abstract`: 9 pt, justified, first-line indent, bold style flag in the template.
- `IndexTerms`: 9 pt, justified, first-line indent, bold style flag in the template.
- `Heading 1`: centered with spacing before/after.
- `Heading 2`: italic style flag, spacing before/after.
- `Text`: justified, first-line indent, approximately 1.05 line spacing.
- `Figure Caption`: 8 pt, justified.
- `Table Title`: 8 pt, centered.
- `References`: 8 pt, justified.

## Formatting Priorities

1. Preserve manuscript content exactly.
2. Use the bundled template as the base file.
3. Apply semantic styles from the template.
4. Use IEEE front matter labels: `Abstract—` and `Index Terms—`.
5. Keep references numeric when possible.
6. Flag any rich content that cannot be transferred automatically.
