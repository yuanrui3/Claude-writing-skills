---
name: "novel-comprehension-test"
description: "Test whether a finished volume of 阴燃 or a spin-off delivers its intended characters and plots: Qwen reads it cold chapter by chapter, retells the arcs, scored against the Map."
---

# Comprehension test for a finished volume

Use when a volume, or a large revision of one, is done and the author asks whether readers get the characters and plots the Map intends, or whether the book is too jumpy. Not for line edits (slowfire-zh-check) or single-passage realism (qwen-consult).

## 1. Write the answer key first
- From the book's Map and index: for each main character, two or three lines of intended arc (who they are, what they want, what changes, where the volume leaves them); the main plot in five lines; each thread's seeds and payoffs with chapter numbers.
- Keep it in a scratch file. Never send it to the reader.

## 2. Prepare the text
- Take each chapter from the local draft (chNN.md), chapter notes stripped. Check first that the draft matches the published tab (the author may have edited the tab).
- Sex scenes (the underlined paragraphs) become one neutral bracket line that keeps the plot: 〔两人亲热，略〕, or 〔两人在车里亲热，其间她说……〕 when dialogue inside carries plot. Never send a sex scene.
- Blur known filter triggers and keep a list of every substitution, so answers can be mapped back. Known for 火候: a church turned mosque, surrogacy, abortion clinics, BDSM, affairs, the US–China ban ("a special arrangement", "a procedure out of state", "the cross-border work stops on the 14th").
- One chapter per message, at most about 5,000 汉字. A long message can trip the filter even when every part passes alone.

## 3. Run it (qwen-consult mechanics: Chrome, the javascript paste, one chat per task)
- New chat; write its URL into the book's index at once.
- First message: the premise in one paragraph (time, places, the one sci-fi rule), the cast list with one tag each, and "你是第一次读这本书的读者，不评文笔，只按文本回答". Ask for 收到.
- Each chapter message ends with the same three questions, short answers:
  1. 这一章出现的人，各是谁，跟谁什么关系（只写能从文中确定的）
  2. 这一章发生了什么（三句以内）
  3. 你猜下一章会发生什么；哪条线你跟丢了
- Blocked message: the chat's history is now poisoned. Start a new chat, resend the premise plus a five-line recap of its earlier answers, then split the blocked chapter in halves to find the trigger and blur it.
- After the last chapter ask for: (a) each main character's arc in two or three lines; (b) the main plot in five lines; (c) threads it thinks were dropped; (d) where it was most lost; (e) whether the volume jumps too much, and where.

## 4. Score against the answer key
- Each character: delivered / partly / missed / wrong, with the chapter where the reader went astray.
- Each thread: seed noticed? payoff noticed? A missed seed is usually fixed earlier and smaller (a re-entry half-line, an object, a name) rather than with more explanation at the payoff.
- Count "who is this" moments per chapter; three or more marks a jumpy chapter.
- Its "next chapter" guesses double as a predictability check (plot-unexpectedness).
- Discount Qwen's known failure modes: it objects to canon premises, miscomputes dates and ages, reads kind characters as mean, states wrong facts confidently, and flatters in its closing verdict.

## 5. Fix and record
- Smallest change first: re-entry half-lines for anyone back after three or more chapters, merging same-thread sections, hinging cuts on a shared sound, object or number. Never add a character or a speech that explains the theme.
- Log in the book's index: date, chat URL, chapters read, a one-line scorecard per character, what was taken and not taken and why.
- Tell the author in a few lines which characters and threads didn't land and what will change.