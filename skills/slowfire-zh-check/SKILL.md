---
name: "slowfire-zh-check"
description: "Proof a Chinese chapter of 阴燃 or a spin-off (火候, 明火, 火德, 燎原…) before and after publishing: 翻译腔, a Qwen cold read for comprehension, look-alike typos, canon names and terms, dates and clocks, 汉字 count."
---

# Checking a Chinese chapter

The author reads only the Chinese, so the Chinese gets the strict check. Run this on every new or edited chapter before handing it over, then again on the published tab. Don't wait for the author to catch slips.

## Before you start
- Read the book's index doc (`claude/<book>-index.md`) and the Map tab of its Claude doc for names, terms and the chronology. The full naming and term list for 阴燃 Volumes 1–2 is in `claude/novel-index.md`.
- Keep the chapter as a local draft (for example `/home/claude/<book>/chNN.md`). The published tab must match it.

## 1. Wording: read it as a native reader would
- 翻译腔: English word order, stacked 的, a 被 where Chinese would be active, 进行／作出 padding, literal images (a heavily pregnant woman is 像个球, not 大), misused jargon. Rewrite the sentence; don't patch one word.
- 成语、俗语 where that speaker would use them, never forced. Non-Chinese speakers get Chinese equivalents, as a good translator would give them.
- Short or incomplete sentences are welcome, but not everywhere.
- Ambiguous pronouns ("他背对着他说"): name one of them.
- Dialect (成都话, 合肥话, 丰县话…) only where the book allows it. Every dialect line goes to Qwen line by line (qwen-consult skill). A line Qwen passes is not proven: it passed 错得板正, and no Chengdu speaker says that. Prefer the common, blunt idiom (标准个铲铲) over a clever coinage.

## 1b. Cold read by Qwen: can a reader follow it?
A line-by-line dialect pass doesn't show whether the chapter reads. The author caught four things it missed in 火候 chapter 2:
- 吃的都是饭, a pun that didn't land;
- 躺舱, used before anything set it up;
- 未记录 · 没有说出口, never explained in that book;
- 错得板正, which no Chengdu speaker says.

So before publishing, and again after any large edit, send Qwen the whole chapter cold (qwen-consult skill, the book's own chat).
- **Strip** the note markers and the 注 section.
- **Give the reader profile:** an adult mainland reader who likes novels, isn't from the dialect region, hasn't read the earlier volumes, and has no notes.
- **Ask for one line per finding, quoting the text:**
  - 一, what it can't follow or might misread, and what it takes the words to mean;
  - 二, dialogue a local wouldn't say, with a natural version;
  - 三, anything that turns up without being set up earlier: a place, a device, a term, a rule, a person.
  
  Add direct questions about any line you're unsure of, such as a pun or a new dialect line.
- **Settle each finding** one of three ways, in this order of preference:
  - fix the text, by setting the thing up earlier or making the line plainer;
  - add a note (slowfire-chapter-notes);
  - keep it as it is, for a reason you can state.
  
  Qwen's word is input, not instruction.
- **Re-check late lines.** Lines added or changed after the read, including answers to the author's comments, go to Qwen in one batch before they land or right after.
- **Log** what was taken and what wasn't in the index doc.

## 2. Typos: by script, not by eye
- Grep every character name and key term from the name list and count each. A name that appears once where it should appear many times is usually a typo for another. Past slips: 凉峥 for 冉峥, 疑疑肉 for 粑粑肉, 耀朋友 for 耍朋友, 暖腔片 for 挡片.
- Escaped quotes (`\"`), stray Markdown, half-width punctuation (, . ? ! : ;) inside Chinese sentences, mixed quote styles.
- After publishing: export the tab (docs `create` a Markdown blob of the tab, then fetch the asset by id with the Artifact tool's read action) and diff it against the local draft. Every difference is either an edit to carry back to the draft or a bug.

## 3. Canon
- Names and terms exactly as listed. Standing examples: 第三档套餐, never T3; hall 7's 02:00 is 断电／拉闸／限电, never 放掉 or 释放; 阳光场, not 太阳场; Indiana is a 州 (州政府, 州议会), never 国家; 念念 in narration; real fab words (挡片, 控片), no coinages.
- Ages, weekdays, festival dates and clocks: compute them (python `datetime`, `lunardate`), never by hand. Clock headings never run backwards. In 火候 the two clocks in a heading differ by 13 hours (Chengdu ahead of EST; no daylight saving in February).
- Rules that hold in every book: real public figures appear only as objects, never as characters; UNRECORDED blocks (未记录 · 没有说出口) at most one or two a chapter; appearance written as physical facts plus one cutting detail, through the POV character's eyes; a rented body is driven by a licensed remote operator or a certified control model.
- Book rules from the index doc (火候: no cheating through rented bodies; Valentine's Day never remarked on; 周知行 out of scandal).
- Anything new the chapter fixes for later chapters (an age, a date, a place, a name) goes into the Map the same day.

## 4. Count
Count 汉字 with a script, not an estimate:
```python
import re
n = len(re.findall(r'[一-鿿㐀-䶿]', text))
```
Report it with and without captions and record it in the index doc.

## 5. Report
Tell the author in a line or two what changed and why, including what the cold read flagged and how each point was settled. Don't list every comma.