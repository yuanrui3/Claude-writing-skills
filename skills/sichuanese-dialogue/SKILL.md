---
name: "sichuanese-dialogue"
description: "Write and check 四川话 (Chengdu, Chongqing) dialogue for the novels against the project's verified lexicon first, sending Qwen only the new or doubtful lines, in one batch per chapter."
---

# Sichuanese dialogue

The aim is fewer Qwen round trips without worse dialect. The project doc `claude/sichuanese-lexicon.md` holds what the author and earlier Qwen rounds have already settled: particles, words, structures, rejected forms, disputed forms, and each speaker's register. A line built only from settled material needs no Qwen check.

## Before writing
- Read the lexicon (project_read). It's short.
- Note each speaker's register from its table: age, place, how much dialect, any tics (王鹏 insists on Mandarin; 汪蓉 says one thing once).

## Writing
- **Dialect lives in dialogue.** Narration stays standard, with at most a light free-indirect touch inside a Chengdu POV. Lafayette sections never.
- **Prefer the common blunt idiom** over a clever coinage. If a line sounds like a quotable 金句, it's the author talking; rewrite it in the speaker's plain words.
- **Don't salt every line with particles.** One 嘛, 噻 or 哈 where the speaker would put it, not one per clause.
- **Address terms follow age and relation:** 嬢嬢 for an older woman or a known lane figure, 大姐 between strangers of similar age, 老汉儿 for one's father.
- **Chengdu and Chongqing differ.** Chongqing is harder and louder (老子, 啷个); Chengdu is 软, ironic, 耙耳朵. Regional jabs always get a comeback (roast-in-fiction).

## Checking
1. Script: pull every dialogue line spoken by a Sichuan speaker.
2. Mark each line:
   - **settled:** every dialect element is in the lexicon's in-use tables;
   - **new:** it uses a word or structure not in the lexicon;
   - **doubtful:** it uses something listed as disputed, or something you're unsure of.
3. Rejected forms: replace them on sight, with no Qwen round.
4. Send only the new and doubtful lines to Qwen, in one batch per chapter (qwen-consult). Ask for each line: 地道／不太像／不像, plus what a Chengdu (or Chongqing) person would actually say. If the chapter also needs a cold read, put the batch in the same message.
5. Settle each answer at your own discretion. Qwen's word is input. It has been wrong before (错得板正 passed its check), so the author's word outranks it.

## After
- Add each newly settled or rejected item to the lexicon doc the same day: form, meaning, speaker, source. Read the doc in full before writing it back. This growing list is what saves future Qwen rounds.
- When the author corrects a line, that correction goes into the lexicon as settled (or rejected) without asking Qwen.