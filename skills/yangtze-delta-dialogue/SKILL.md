---
name: "yangtze-delta-dialogue"
description: "Write and check 上海话, 苏州话, 常熟话, 杭州话 and 南京话 dialogue for 阴燃 books (火候 Volume Two onward) against a verified lexicon, sending Qwen only new or doubtful lines."
---

# Yangtze delta dialogue

The sister of sichuanese-dialogue, for the delta scenes the author added to 火候 Volume Two. The delta enters the book only where 燎原 and 火德 characters live (钱维岳 in 常熟, 乐子 in 杭州, 阿包's 上海 desk, optionally 江烈 at 乌江 across from 南京). The aim is dialect a native would accept, readable by a Mandarin reader, with as few Qwen round trips as the lexicon allows.

## Know which dialect is which
- **Wu (吴语, 太湖片):** 上海话, 苏州话, 常熟话, 杭州话. 杭州话 is Wu with heavy Mandarin layering (乐子 speaks Hangzhou-accented Mandarin, not full 杭州话, unless the author says otherwise).
- **江淮官话:** 南京话 (and 合肥话, which Lin and Mei's mother speaks). A 合肥 speaker follows 南京话 easily; a Chengdu operator follows neither Wu nor much of 南京话.
- Never let one Wu city's forms leak into another's speaker. When unsure which city a word belongs to, it is doubtful (below).

## The 2048 premise
- These dialects survive mostly in people over 60. The young understand some and answer in Mandarin. Dialect belongs to the ageing thread: the old want to be spoken to in it, and their care is often driven from Chengdu by operators who can't.
- So most dialect lines go to old speakers. A young character speaking full dialect needs a reason on the page (raised by a grandmother, a 评弹 family, a deliberate choice).

## Before writing
- Read the project doc `claude/delta-lexicon.md` (create it before the first delta scene, with the same tables as `claude/sichuanese-lexicon.md`: settled, rejected, disputed, and each speaker's register: age, place, how much dialect, tics).
- Until an entry is in the lexicon, it is not settled. Don't write from memory and call it checked.

## Writing
- **Dialect lives in dialogue.** Narration stays standard Mandarin. A light free-indirect touch only inside that speaker's POV.
- **Readable first.** One or two dialect words a line, glossed by context or by the listener's reaction, not by narration. A full sentence of 上海话 that a Mandarin reader cannot follow gets a reaction line (the operator asks again) or a chapter note per slowfire-chapter-notes.
- **Standard written forms** (the forms used in published dialect dictionaries and serious fiction such as 《繁花》 and 《海上花列传》), not homophone spellings and never 火星文.
- **No caricature.** No stock line used to stand for a whole city. Regional jabs live in characters' mouths and always get a comeback (roast-in-fiction).
- **Prefer the plain idiom** over a clever coinage; a quotable line is the author talking (character-voice).

## Checking
1. Script: pull every dialogue line spoken by a delta speaker, tagged by dialect.
2. Mark each line settled (every dialect element is in the lexicon's in-use tables), new, or doubtful (disputed in the lexicon, or you are unsure which city a form belongs to).
3. Replace rejected forms on sight, with no Qwen round.
4. Send new and doubtful lines to Qwen (qwen-consult) in one batch per chapter, grouped by dialect, with each speaker's age and city. Ask for each line: 地道／不太像／不像, what a native of that city and age would actually say, and the standard written form.
5. Qwen is input. For 常熟话 and other small varieties it may be thin or wrong; when it hedges, ask the author, who outranks it.

## After
- Add each settled, rejected or disputed item to `claude/delta-lexicon.md` the same day: form, meaning, dialect, speaker, source. Read the doc in full before writing it back.
- An author correction goes in as settled or rejected without asking Qwen.
- Record the round in the book's index doc (taken, not taken, why).