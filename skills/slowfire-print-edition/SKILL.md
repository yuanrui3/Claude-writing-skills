---
name: "slowfire-print-edition"
description: "Build the A5 Chinese PDF, plain or annotated (注释本), of a 阴燃 volume or spin-off from its Claude doc: export, spoiler-safe notes, plates, pandoc + xelatex, text verified identical to the doc."
---

# Print edition of a volume

Past builds: 阴燃 第一卷 注释本 (301 A5 pages, 493 notes), 第二卷《余烬》注释本 (256 pages, 450 notes), 《焦线》 plain and annotated, 《明火》 (85 pages, plates in the PDF only), 《火德》 (Chinese-style figures). Read the book's index doc first (`claude/<book>-index.md`, `claude/minghuo-pdf.md`, `claude/vol2-annotated-edition.md`); it may record the last build and where its sources went. The cloud workspace does not keep files between sessions, so expect to rebuild from the doc.

## 1. Get the text without pasting it through the chat
For each tab: docs `create` a Markdown blob of the tab, then fetch the asset by id with the Artifact tool's read action. One file per chapter. Write down the doc revision you exported.

## 2. Notes (注释本 only)
- Short Chinese notes for a new reader: people, terms, real-world facts, the borrowed manner of a chapter.
- Spoiler-safe: a note explains only what the reader knows at that point. Never name a thing before the chapter that reveals it (Volume One: the 7f family, the voting and the unsigned stay unnamed before chapter 12; tally and Cradle are described, not defined). A glossary that covers the whole volume goes at the back, with a warning.
- Markers: circled ①… restarting each chapter, so they never clash with the chapters' own ¹ notes.
- Every real fact or date in a note is checked, not written from memory.

## 3. Figures
- Use the doc's figures at print resolution, or draw plates in code (matplotlib, vector PDF) when the figures live only in the PDF, as in 《明火》 (see slowfire-figures).
- Place each plate by an anchor phrase inside its chapter. If a rewrite touches the anchor paragraph, update the anchor.

## 4. Build
- pandoc `-f markdown-smart-superscript-subscript+raw_attribute --wrap=none` to LaTeX, inside a hand-written preamble; xelatex twice.
- A5. Fonts: check for xeCJK (`kpsewhich xeCJK.sty`); if missing, fontspec with Noto Serif CJK SC and `\XeTeXlinebreaklocale "zh"`. Machine voices (【…】) and quoted screens in Noto Sans CJK SC; code in Noto Sans Mono CJK SC.
- `\interfootnotelinepenalty=10000`, so no note splits across pages.
- Front matter as the book needs: title page with the author's name exactly as he gave it, 目录, 读前说明 or 导读, 人物, 词语; the AI-assistance statement where the book carries one.

## 5. Verify before sending
- Extract the PDF's text (`pdftotext`, notes stripped) and diff it against a fresh export: identical in every chapter. Any later change to the doc means re-export and rebuild.
- Render a few pages to PNG and look at them: the TOC, a figure page, a page dense with notes, a page with machine voice or dialect.
- Count pages, notes and 汉字.

## 6. Deliver and record
- Send the PDF with SendUserFile. Zip the sources (build.py, figs.py, src.md, notes) as `<book>_sources.zip` and send that too.
- Write the build record (doc revision, pages, notes, 汉字, what changed since the last build) into the book's index doc or `claude/<book>-pdf.md`.