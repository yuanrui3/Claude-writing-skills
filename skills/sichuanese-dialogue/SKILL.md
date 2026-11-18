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
- **Chengdu and Chongqing differ.** Chongqing is harder and louder (老子, 啷个); Chengdu is 软 and ironic. 耙耳朵 is an outsider's exaggeration (author, 18 Nov): Chengdu men don't wait on women, and don't want them submissive either; neither serves the other. Use it little, only in an outsider's mouth, and answered. Regional jabs always get a comeback (roast-in-fiction).

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

## Whole-book pass (the 海上花 standard)
Use when a volume is finished or the author wants the book to be a landmark of dialect fiction.
- **Standard first.** Keep a house standard doc (火候: claude/chengdu-standard.md): narration in 普通话, natives speak dialect in full (words and grammar, not particles stuck on Mandarin), one spelling per word, registers per speaker, and a 例言 for the front of the book (as 韩邦庆 wrote for 海上花), placed as its own tab before 第一章.
- **Extract.** Script every quote in the dialect sections (Lafayette sections never) and flag Mandarin markers: 呢, 什么, 怎么, 知道, 没有 as a verb, 谁, 别, 一下, 家里, 着 for states, 这么, 吧. Read each hit; skip speakers who speak Mandarin by design (王鹏, 铁子, 乐子, 何蔓 outside home).
- **Settled swaps need no Qwen:** 呢→喃, 着→起的 (门锁起的), 没有→没得, 哪里→哪点, X里→X头.
- **One Qwen batch** for new or doubtful forms, plus a 金句 check on any line that sounds like a slogan. Expect Qwen to flatten toward Mandarin or drop a pronoun the line needs; keep what carries meaning.
- **Cards**, one per line, minimal finds; read back by hash. The real drift is usually small and concentrated in one or two speakers; say so rather than inflating the pass.
- **Lexicon** updated the same day: settled, rejected, disputed, and a register line for every speaker touched.