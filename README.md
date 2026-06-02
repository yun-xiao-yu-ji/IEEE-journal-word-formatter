# IEEE-journal-word-formatter
## Project Overview
A lightweight LLM-based skill tailored for academic researchers across engineering and natural science fields, which automatically standardizes unformatted Word manuscripts to comply with official IEEE journal formatting specifications via large language model dialogue invocation. This project is developed as an embedded skill module instead of standalone installable desktop software, no program setup, EXE packaging or environment pre-deployment is required; users can directly load and call this skill in compatible large model platforms to finish tedious IEEE typesetting revisions in one conversation.

The skill covers mainstream IEEE formatting rules including reference citation styles, paragraph indentation, figure & table caption specification, abstract/keyword layout, header-footer rules and journal-specific manuscript margin constraints, drastically cutting down the manual typesetting workload before journal submission.

## Core Position Description
> Important note: This repository only contains prompt engineering scripts, configuration rules and auxiliary specification documents for LLM-oriented skill, **not independent desktop application software**. This skill is specially built for Codex and homologous large model platforms; users only need to import the skill into the large model runtime to complete paper format modification through dialogue interaction.

## Project Background & Core Pain Points (Original demand for developing this skill)
1. Different pre-submission format requirements between IEEE journals and most other academic journals: The vast majority of non-IEEE academic journals allow authors to submit completely unformatted raw manuscripts, with uniform typesetting processed by editorial offices after paper acceptance. However, all IEEE-indexed journals mandate strict standardized layout before initial submission, and unfinished format compliance will lead to direct desk rejection at the preliminary review stage.
2. Extremely time-consuming manual IEEE typesetting: Researchers spend hours or even whole days manually adjusting reference styles, page margins, figure/table captions, paragraph indentation and abstract layout to match IEEE official rules repeatedly. Relying on this Codex skill, users can upload unarranged original drafts and finish full IEEE standard formatting within merely 3 minutes, eliminating redundant manual revision work.
3. Fragmented formatting specifications across IEEE sub-journals: IEEE Transactions, Letters and Magazine branches each carry subtle differentiated layout clauses without a unified universal standard, which requires continuous optimization of built-in prompt rules to adapt to diverse sub-journal formatting demands.
4. Chaotic formatting of user source manuscripts: Authors’ original drafts often include disordered line breaks, mixed Chinese-English typography and references written in inconsistent GB/T, APA or Harvard formats, so the skill needs flexible prompt logic to identify and normalize messy input contents automatically.

## Detailed User Tutorial
Complete step-by-step deployment & operation guides for this skill are published exclusively on our official WeChat Official Account.
> Follow our WeChat Official Account: **区域地面沉降研究前沿** to access full tutorials, skill update announcements and follow-up technical support content.

## Target Users
Postgraduates, doctoral candidates and professional researchers who need to submit papers to IEEE-indexed journals.

## Authors
Yunxiao Liu(2240902154@cnu.edu.cn, Capital Normal University), Mingliao Gao (Capital Normal University)
