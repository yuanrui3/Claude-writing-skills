---
name: "slowfire-zh-check"
description: "Proof a Chinese chapter of 阴燃 or a spin-off (火候, 明火, 火德, 燎原…) before and after publishing: 翻译腔, AI tells (去AI味), a Qwen cold read plus adversarial reviewers, look-alike typos, canon names and terms, dates and clocks, 汉字 count."
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

## 1a. AI tells (去AI味)
Adapted from story-deslop in oh-story-claudecode (MIT, github.com/worldwonderer/oh-story-claudecode). The signals below are things to judge in context, not banned words. Keep a form when it does work: a real contrast in an argument, a character's own voice, a motif such as Corinne's 不能多也不能少. Cut or rewrite only what fakes weight or says again what the reader already has. Never fake "realness" by adding micro-gestures, swearing or random sensory detail.

Check three layers.

**Expression.**
- 否定翻转: 不是A，是B, where the A nobody believed is knocked down only to announce B. 火候's 不是扇风，是扇时间 was one, an author's 金句 in a teahouse boss's mouth.
- 工整并列 that repeats one point.
- 万能状语 and stock voices: 带着一丝……, 声音不大，却不容置疑, 平静得像…….
- Scare quotes on ordinary words.
- Template metaphors and big abstractions: 命运的齿轮, 潮水般.
- Explanation chains: 这意味着, 他终于明白, 她这才意识到.
- Inflation and prophecy: 意义深远, 他不知道的是, 多年以后.
- Body parts that only label an emotion: 指节泛白, 指尖轻叩, 嘴角勾起.
- Genre stock lines. The 耗美 scent-marking 你身上还是我的味道 was replaced by a callback to the night itself.
- 电报体: facts reported one clause at a time when they are one cause chain.

**Weight.** Name in one line what each scene must make the reader live through. Then:
- compress routine process (opening doors, pouring water);
- don't let a summary swallow the turn (三言两语说清楚, 她终于想通了);
- cut states that circle without change;
- add the transition where a result arrives without one.

**Story logic.**
- Each choice rests on what the character knows (plot-ledger).
- Each result has its cause on the page.
- The other side has its own interest.
- Solutions are set up earlier.
- What happened changes what comes next.
- Rules of the world hold (scifi-world-check).

Searchable signals, for the first pass:
```python
import re
SIG = r'不是[^，。？！]{1,12}，(?:而)?是|没有[^，。]{1,8}，没有[^，。]{1,8}，只有|带着一丝|声音不大，却|不容置疑|毫无波澜|平静得像|这意味着|真正重要的是|由此可见|终于明白|这才意识到|不知道的是|殊不知|多年以后|冥冥之中|仿佛预示|命运|宿命|齿轮|意义深远|恰到好处|恰如其分|指节泛白|指尖轻叩|嘴角勾起|眸|眼底闪过|心头一紧|呼吸一滞'
for m in re.finditer(SIG, text):
    print(text[max(0, m.start()-20):m.end()+20])
```
Judge each hit in its sentence. Lines a character must say well also go to Qwen with the question "俗不俗套？" (the author asked exactly that twice in 火候).

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

## 1c. Adversarial readers (after oh-story-claudecode's story-review)
For a new chapter, or a rewrite of a turning point, add fresh readers that haven't seen you write it. Each gets only the chapter text and the canon excerpts it needs, and the rule: 审查是找问题，不是验证正确性.

Use sub-agents where the session allows, or separate Qwen messages. Give each one brief:
- **Structure and pace:** does a relationship move by a real event; does the chapter end on a hook; which beat is predictable (plot-unexpectedness for a full test).
- **Character and voice:** does each person act from their own interest, and speak as themselves rather than as the author.
- **Line:** the 1a signals, 翻译腔 and 金句.
- **Consistency:** the plot ledgers and the world rules.

Each finding comes back as a quote, the problem and a fix. Settle them as in 1b and log them the same way.

## 2. Typos: by script, not by eye
- Grep every character name and key term from the name list and count each. A name that appears once where it should appear many times is usually a typo for another. Past slips: 凉峥 for 冉峥, 疑疑肉 for 粑粑肉, 耀朋友 for 耍朋友, 暖腔片 for 挡片.
- Escaped quotes (`\"`), stray Markdown, half-width punctuation (, . ? ! : ;) inside Chinese sentences, mixed quote styles.
- After publishing, check the tab against the local draft by hash. Every doc block carries h = the first 8 hex of sha256 of its UTF-8 plain text. Read the tab with the outline view, copy the h values into a file, hash the local paragraphs the same way (strip Markdown: headings, **, italics), and compare. Every local paragraph missing from the doc is either the author's own edit (carry it back to the draft) or a bug (fix it, then confirm the new h).
- Why hashes and not a search: payloads typed by hand can turn a rare character into a near neighbour (噻 became 嘻 in 火候 ch2), and a search typed by the same hand repeats the slip. The hash comparison is the only check that doesn't depend on retyping.
- Write Chinese characters directly in payloads and comment replies; never hand-type \u escapes. A hand-escaped reply turned 耽 into 耗 in a 火候 comment thread.

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