---
name: "pianwen-notes-zhuyin"
description: "Annotate a 骈文 for modern readers: 注 entries with bold keys, 注音 on the hard-to-read characters chosen with Gemini and Qwen, and a 致敬篇目, all kept in sync with the doc and the PDF."
---

# Notes, 注音 and 致敬篇目 for a 骈文

Use this when adding or revising the 注, the 注音 or the 致敬篇目 of the author's 骈赋 (《拉法叶赋》: notes in the doc's 注 section, local copy `pdf/notes.md`, tribute list `pdf/tribute.md`).

## Notes (注)
- **Layout:** one note paragraph per text paragraph, in text order. Each entry is `**key**：gloss`, and the key is bold in the body at its first appearance.
- **Glosses:** short and plain. For an allusion, give the book, the chapter and the original line, then one clause on how it is used here. Check every fact.
- **When a revision removes a phrase:**
  - Remove or rewrite its note.
  - Check that every key still appears in the text.
  - Check that every phrase the 致敬篇目 quotes still exists.

## 注音
- **Format** (keep to the existing notes):
  - The whole key is hard → `**汤汤**：读 shāng shāng，…`.
  - One character is hard → `**问难**：难读 nàn，…`.
  - The pinyin with tone marks goes right after the colon.
- **No note key for the word:** either add a key, or ride on a nearby note (`**浮圈**：…；相属，属读 zhǔ，…`).
  - A new key in plain text gets bolded in the body by a markdown replace.
  - A key inside underlined text can't be bolded by the doc tool without losing the underline. Leave it unbolded in the doc; the PDF bolds note keys itself.
- **Choosing the characters.** Don't choose alone; the author wants Gemini and Qwen consulted.
  - The standard is a college-educated mainland reader who doesn't specialise in classical literature.
  - Ask both, independently, for about 25 characters ranked by difficulty: 词语｜字｜此处读音｜难在哪（生僻／此处取不常用音／古音通假）｜难度1–5. List a character twice if it has two readings in the text.
  - Ask both to check the existing list: wrong readings, too-easy ones, and gaps harder than what's there.
  - For Qwen, load the prompt file into the page with the hidden-input trick and send it in a new chat; record the chat URL in the record doc.
- **Categories to cover:**
  - Rare characters: 隰 裼 旃 螽 蕈 戢 芟 槎 啮 抟 嵯峨 迤逦 ….
  - Readings that hold only in this sense: 星宿 xiù, 雨 yù (verb), 度 duó, 干 gàn (trunk), 殷 yǐn (thunder) and yān (dark red), 汤汤 shāng, 阿 ē (高处), 潦 lǎo, 莞尔 wǎn, 相属 zhǔ, 间 jiàn, 檐溜 liù, 辩难/问难 nàn, 皆中 zhòng, 卒读 zú, 褶 zhě, 柞 zuò.
- **Lesson:** the author expected 槎 (乘槎) to be annotated. Mid-rare literary characters count. When in doubt, put a character in the quiz rather than leave it out.
- **Quiz the borderline and disputed ones.** If a standard reading is unsettled (菌: 现代汉语词典 jùn for mushrooms, everyday jūn), offer the readings. His stated range (for example 6–17) is a guide; he may go over.
- **Verify** every reading against a dictionary sense, not by memory of the common reading.

## 致敬篇目
- **Groups:** 赋与文, 诗, 经史子, 域外.
- **Each entry:** the work, where it is used, and the quoted line.
- **Reversals** (反用) are listed with what they reverse.
- **After every revision:** check that every 赋 phrase quoted here still exists in the text.

## Applying and verifying
1. **Doc:**
   - Edit the notes with find-replace ops: find `key：gloss-start`, replace as markdown with `**key**：…`.
   - Check the doc hasn't changed first (`view` with `sinceRev`).
   - Hash-verify each changed note paragraph, sha256(plain)[:8].
2. **Local:** patch `notes.md` with a regex that allows `**` only between characters. A trailing optional `**` swallows the next key's opening marker. Then confirm that no old key was lost and that the new keys are present.
3. **PDF:**
   - Rebuild, including the `--plain` build.
   - Check `pdftotext` for every body paragraph, every note sentence and every pinyin.
   - Grep the xelatex log for "Missing character" (tone marks).
   - Look at one rendered notes page.
4. **Log** the round in the record doc: what was annotated, what the author chose and what was left out.