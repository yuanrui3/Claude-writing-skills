---
name: "pianwen-fu-writing"
description: "Write or revise a 骈赋/骈文 with the author: Gemini drafts, Claude checks every image and meaning, the author decides by quiz. Covers 四六, 对仗, 骈散 balance, 典故 and his taste."
---

# Writing and revising a 骈赋 with the author

Use this for any work on a 骈赋 or other 骈文 the author is writing (first: 《拉法叶赋（并序）》, kept in a Claude Doc, record in project doc `claude/lafayette-fu-pdf.md`). Read that record first; it holds every past round, what was taken and what was turned down.

## The author's standing rules
- **Underlined text is his and stays verbatim.** Never change or split it; edits go only before or after it. Mark it 〖〗 when sending text to another model.
- **Most nature and people images are his.** Any change to an image, even a small one, goes to him by quiz first. Changing syntax is fine; changing what is seen is not.
- **Strict 平水韵** at the rhyme positions (see pianwen-yinlv-check).
- **Taste:**
  - Feeling is carried by an image or a law of nature, never stated. No 乃悟、微惜、余笑-type lines.
  - Short, compressed lines.
  - The literal sense must be readable without knowing the source.
  - No name-stacking, argument, obscurity, the macabre or exaggeration.
  - Every scene must be real to the place.
  - Tone 平淡, 不作危苦之辞.
- **Process:** Gemini does the heavy lifting; Qwen gives outside reads. The author decides by multiple-choice quiz. Talk to him in English.

## Form targets
- 序 may run as prose; 乱曰 is a short verse.
- The body is mostly 四六 and 隔句对, led by 领字: 夫、若夫、尔乃、于是、既而、是月也. One or two 散句 per paragraph is normal in 赋 and need not be removed.
- Watch the portraits: they drift into 笔记 or 《世说》-style prose sketches. Scenery paragraphs usually hold 骈 form better.
- The piece is a 骈散兼行 mix near 洛神赋, about 60–70% parallel lines (哀江南赋 is over 90%). Don't push toward 哀江南 density unless he asks; it wears away the people's life and humour.
- **Direct quotes:**
  - Keep short, lively ones. Precedent: 枯树赋 quotes 桓温.
  - Turn report-like or explanatory quotes into reported speech.

## Workflow
1. **Brief Gemini** (Chrome, the book's Gemini chat).
   - Send the full current text with underlines marked, the rules above, and one job with numbered items and a fixed output shape.
   - Ask for a diagnosis first (per paragraph: fine / slight drift / clear drift), then edits.
   - Long material goes as file attachments, not pasted (hidden-input trick below).
2. **Require an 意象清单** for every rewrite: each noun image, action and number in the original sentence, mapped to the words of the rewrite. Nothing on the list may go missing, and nothing new may be added. Ask it to say 原句可留 where the original is already good, and to change as little as possible (能少动就少动).
3. **Check Gemini's output yourself, line by line.** Typical failures seen:
   - Meaning changed:
     - 不顾人之视己 → 目不顾人.
     - 九事皆中 → 九已施行.
     - 循礼 moved from the wife onto the sons.
     - 一岁将终 misread as one match ending.
   - Key image dropped:
     - 一闪 in 皓齿一闪.
     - 灯烛县道.
   - Image added: 丰神自盈, 县道雪深, 呼声, 野炊, 绝顶 for an indoor wall.
   - Ambiguity created:
     - 有白皙少年二十二 reads as twenty-two youths.
     - 步者乘轮 merges two kinds of people.
   - Humour lost: dropping the 曰 that makes a line her own words; dropping 尤 in 口尤捷.
   - Bad Chinese: 习为常年.
   - Repeats: a phrase the author just removed coming back (中度 after 中人之度); a line he rejected earlier (与星相争).

   Send numbered objections back and ask for a second pass. The second pass is usually conservative and usable.
4. **Quiz the author** (AskUserQuestion).
   - Group by paragraph, with multiSelect and before/after previews.
   - Add a "Keep as is" option. Each question must stand on its own.
   - Say plainly where Gemini, an outside review and Claude disagree, then let him choose. He may take items both models argued against; apply them without re-arguing.
5. **Apply to the doc** (see Doc editing below). Then:
   - Update the local text (fu_finalN.md).
   - Rebuild the PDF (slowfire-print-edition).
   - Log the round in the record doc: what was taken, what was not, and why.
6. **The reading site** (Slow Fire): push only on the author's word.

## 典故
- **Portraits:** when asked, use a pair of allusions per portrait.
  - Chinese first; foreign and modern figures are allowed (Vermeer, myth, stars).
  - They must be famous enough to read without the note, and must fit a specific detail of the person: hair, gait, a habit.
- **Watch the side-shading:**
  - 梁鸿/孟光 implies a plain wife.
  - 狐死首丘 reads as homesickness even when negated.
  - 故人 means an old friend, not the ancestors (先人).
- **Reversals (反用)** carry a stance: 不作危苦之辞 against 庾信; 何必吾土 against 王粲.
- Every allusion gets a note with book, chapter and the original line (pianwen-notes-zhuyin).

## Outside reads
Use a Qwen blind read: a new chat, the full text with no notes, and four open questions:
1. Who is 余, and what is his situation?
2. What feelings come through, strongest first, with lines?
3. Any unspoken 心事?
4. What is unclear?

Compare its answers with the threads the author intends (for example the climate and AGI threads, which Qwen missed twice). Report what came through and what didn't; let him decide whether to make a thread more legible.

## Doc editing (Claude Docs)
- **Edits:** use find-replace ops. With `"as":"markdown"`, re-spell the bold of annotated terms (`**term**`).
  - Markdown can't express underline. Never let a replace span underlined text; split the op around it.
  - Text inserted right after underlined text can inherit the underline: delete it and re-insert with a markdown replace.
  - A find-anchored insert creates a new block; fix it with a `join` op.
- **Verify:** hash every changed paragraph, sha256(plain text)[:8] == the doc's `h`. Check that every underlined segment still exists and that every note key still appears in the text. Count 汉字.
- **Characters:** type Chinese literally. \\u escapes have produced wrong characters (霽 for 霁, 遑 for 遽).
- **Staleness:** before editing, read `{"kind":"view","sinceRev":N}` to see whether the author changed anything.

## Gemini mechanics (Chrome)
- **Send:**
  1. Put text into `.ql-editor` with `document.execCommand('insertText')`, using 〔分段〕 for newlines.
  2. Click send at the bottom right of the input.
- **Read:** take `[...document.querySelectorAll('model-response')].at(-1).innerText` into a window variable and read it in slices of about 1,200 characters (longer slices get truncated). Poll in ≤40-second JS calls.
- **Attach files without passing them through Claude's context:**
  1. Create a hidden `<input type=file multiple>` with an aria-label.
  2. `find` its ref, then `file_upload` (origin https://gemini.google.com).
  3. Dispatch `new ClipboardEvent('paste',{clipboardData:dt})` on `.ql-editor`.

  The same hidden input on chat.qwen.ai lets a page read a long prompt file (`await file.text()`) into the textarea.