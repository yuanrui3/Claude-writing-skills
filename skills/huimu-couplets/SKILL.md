---
name: "huimu-couplets"
description: "Write and place 回目 couplets under chapter titles in 阴燃 books, 章回体 style: parallel lines, 仄/平 endings, Qwen-checked, laid as hash-verified cards."
---

# 回目 couplets

Use when the author wants chapter couplets as a tribute to 海上花, 金瓶梅 and 张恨水 (张爱玲 kept them in her 海上花 translation), or when a book that already has them gets a new chapter.

## Form
- Two lines of equal length, 6 to 8 characters each, separated by a full-width space. Each chapter keeps its own title; the couplet sits on the next line.
- Parallel: matching parts of speech and structure position by position (person/person, place/place, verb-object/verb-object, number/number). Names against roles is a loose pair; avoid it where a better match exists.
- Tones: the upper line ends 仄, the lower ends 平. Entering-tone characters count as 仄 (七, 约, 色, 脉, 白). Swap the lines if needed; chapter order of events need not match.
- Content: who, where or how, and what, in the manner of 海上花 (人名 + 地点 + 事). One concrete image from the chapter beats a summary. A pun is welcome when it is true twice (生门: the fire exit and the pregnancy).
- Sex only as metaphor or object (报色, 落小雨); no child near any sexual hint; no spoiler the chapter itself doesn't deliver.
- The first and last couplets may announce the book's theme, as 金瓶梅's first does with 热结 and 冷遇.

## Steps
1. One-line summary of each chapter from the index doc.
2. Draft all couplets; tabulate each line's last character and tone, and mark any repeated character across the pair.
3. Qwen, one new chat (qwen-consult): send all couplets with short glosses for coined terms (blur sensitive content), and ask for each: 工整/尚可/不工, the problem, a fix. Take real mismatches; reject fixes that lose the chapter's image or are wrong about the book. Log what was taken and not.
4. Find each chapter's title block id (a search for 第N章 in its body).
5. Lay all couplets in one docs batch, one card per chapter: an insert after the title block with suggest true, as markdown.
6. Verify: for each body, a view read with sinceRev one below the ack's rev; compare the inserted block's h with sha256 of the couplet.
7. Record the full table in the book's pass log or index doc.