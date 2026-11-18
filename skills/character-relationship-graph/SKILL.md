---
name: "character-relationship-graph"
description: "Draw and audit the 人物关系图 of a 阴燃 book or volume: people and ties taken from the text, typed and checked, laid out by place, published as an interactive page, with islands and thin threads reported."
---

# 人物关系图

Use when the author asks to see who is tied to whom in a volume, or when a volume is finished and its net should be checked. The picture is half the product. The other half is the short list it yields: who carries the book, who hangs by one thread, who is on no thread at all.

First run: 《火候》上部, 18 Nov 2026 (44 people, 74 ties; sources in `graph/data.py`, `graph/build.py`, `graph/page.html`; record in `claude/huohou-pdf.md`).

## 1. Scope and source
- One volume at a time unless the author says otherwise. State the chapters covered on the page.
- Build from the text, never from the Map, the index or memory. Make sure the local drafts match the doc first (block hashes from an outline read of every tab). Pending suggestion cards are not text.
- Use the index's cast section only to know who exists. A tie that only the plan states does not go on the graph.
- A doc owned by another chat (火候 下卷) is read, never edited.

## 2. People
- A node is a named person, or a fixed designation the narration itself uses (冉峥他妈, 老太太, 重庆老板).
- Young children of one household become one node and carry family ties only. One-mention names and cameos stay out. Record who was left out.
- Each node has a place (which side of the picture) and one line built from facts on the page: age, work, one detail. No judgement, nothing from a later volume, nothing about any real person behind the character.
- Count name mentions per chapter by script. Watch names inside names (琳 in 科琳), single-character names (文 needs a context pattern) and aliases (迦勒 / 优素福). Circle size is the mention count; the chapter strip shows where the name occurs. Call it 提到, not 出场.

## 3. Ties
- A tie is a relationship the book puts on the page, not a shared scene.
- Count shared sections per pair by script, but only to find candidates and to catch a tie you forgot. Then grep the lines and confirm every tie before it goes in.
- Types for 火候: 亲 (family, marriage), 情 (slept with, wants, spars), 手 (who drives whose body; an arrow from driver to body), 钱 (hire, rent, landlord, crew), 相识 (met or spoke). In another book, give its own sci-fi rule a type and a colour of its own; it is usually the most telling layer.
- One tie per pair: choose the strongest type and put the rest in the label.
- Label: about 25 汉字 at most, in the book's own words, a quoted line where there is one. The first clause must read alone, because the graph shows only that; the panel shows the whole label. No theme words.
- Mark what the book marks. In 火候 the two concealed liaisons are dashed.
- Sex and desire ties are between adults only. A child node never carries anything but a family tie.
- Legend names must read cold. A one-character type name was misread (交), so every type button carries a short gloss.

## 4. Layout and page
- Lay out by geography: one town per side, the gap between them drawn, so that ties crossing it can be counted by eye.
- Seed positions by household and workplace by hand. Render, look, and move nodes until no line runs through a third person's circle. Long cross-town ties are arcs; check what each arc passes (one family arc ran through another character and read as her tie).
- One self-contained HTML page, no library, data embedded by a build script. Nodes drag. Clicking a person dims the rest, shows the labels on their ties and fills a side panel: their line, the chapter strip, their ties grouped by type. Type buttons switch layers on and off.
- The resting panel says how to read the graph and lists the most-tied people, the people off the main net (connected components) and the number of ties crossing the gap.
- Take the palette from the book's own figure style, with light and dark tokens. Solid and hollow circles tell the two places apart.
- Screenshot with headless Chrome: the resting state and one selected person. Fix once, then publish as an artifact (check the artifact types first; none fits, so it is a hand-built page). Later versions republish the same artifact, labelled v1, v2.

## 5. What to report
Describe, do not prescribe.
- Who has the most ties, and any main character with few.
- Islands: people on no thread to the main net. One-thread people.
- Ties crossing the gap, by type.
- A pair with many shared sections and no tie. A tie with no shared section (asserted, never staged).
- Where the net differs from the threads the Map intends. If the author wants it fixed, that goes to story-idea-weave and plot-ledger.

## 6. Record
- In the book's index doc or its build note: the link, the counts, the findings, who was left out, where the data lives.
- Put the graph's sources in the same zip as the print sources.
- If the author asks what a mark or a word on the graph means, fix the page as well as answering.