---
name: "slowfire-chapter-notes"
description: "Write or prune the ①② notes (注) at the end of a Chinese chapter of 阴燃 or a spin-off (火候, 明火, 火德…): note only what a non-Sichuan reader can't get from the page; Qwen judges borderline cases."
---

# Chapter notes (注)

A note is there for a reader who would otherwise misread a line or miss its point. It is not there to show what we know. When unsure, leave it out: the author would rather cut than wade.

## The reader
An adult mainland reader who likes novels. Not from Sichuan or the dialect region in question, and hasn't read the earlier volumes. Knows ordinary Chinese life, food, festivals and the internet.

## Format
- A circled number ①② goes right after the term in the text. The notes go in a section at the end of the tab: `---`, then `**注**`, then one paragraph per note, `① 词：解释。`
- Each term is noted once in the whole book, at its first appearance. Later chapters don't repeat it. Before writing, check the earlier tabs' 注 sections.
- One or two sentences. Cross-references take the form （见《阴燃·余烬》第二十九章）.
- Spoiler-safe: say only what the reader knows by that point.
- Check every real fact or date in a note (search, `datetime`, `lunardate`). Never write them from memory.

## What gets a note
- **Dialect** whose meaning can't be guessed, or that means something else in Mandarin: 冲壳子; 冰欠; 老汉儿 (father, not an old man); 老嬢儿. Also 嬢嬢, for its reading.
- **Specialist or local knowledge the scene turns on.** Cooking: 灯盏窝. Folk custom objects: 灶马子; 上天言好事, and why the 麻糖. Obscure foreign religious or cultural items: 圣犹达, pozole.
- **Real-world facts the fiction extends.** For example the 2025 connected-vehicle rule, the 'irreparable harm' standard, Stevenson's 2003 core-probe idea, China's robot training centres.
- **Series devices at their first appearance in each book**: the 未记录 · 没有说出口 block is a person's unspoken thought, often the side of them they don't show.
- **Book-world terms the page doesn't explain**: 摇篮, 一号提案, 子宫中心. Also characters carried over from earlier volumes (梅姐, 乐子), with a cross-reference.

## What doesn't: the author's cuts, the calibration set
The author cut these from 火候 chapter 1:
- 苍蝇馆子, 郫县豆瓣, 团年饭 (with the particles 嗦 噻 喃 哈), 钱又不烫手, 别个, 三十夜, 锅头炒起在的, a rosary (天主教念珠手串), 留起的, 郫都, 土 (旱地).

The pattern:
- **Dialect readable from context**, or close enough to Mandarin: 别个, 三十夜, 留起的, 锅头炒起在的, 钱又不烫手, sentence particles.
- **Widely known** food, dishes, places and customs: 苍蝇馆子, 郫县豆瓣, 团年饭, 郫都.
- **Common religious objects** the text already names.
- **Anything the sentence itself explains**, such as 土 in a passage about farmland. The same goes for a rule the narration states in the same breath.
- **A note that only restates the text.**

Whenever the author cuts more notes, add the terms to the calibration list in the book's index doc (`claude/<book>-index.md`, section 注释), and to this skill when the pattern changes.

## Procedure
1. **Mark candidates while drafting**, generously.
2. **Prune** against the two lists above.
3. **Start from the cold read** (slowfire-zh-check, step 1b). Anything Qwen couldn't follow is fixed in the text if possible, or noted. Anything it read without trouble needs no note.
4. **Ask Qwen about the borderline ones** (qwen-consult skill, the book's own chat). Send:
   - the reader profile;
   - the calibration cuts;
   - each remaining note with about 40 characters of its sentence;
   - the ask: one line each, 留 or 删 plus a reason of ten characters or less.

   Mark book-world notes （设定）, and ask only whether the page already explains them. Qwen's verdict is input, not instruction: decide yourself and log what was taken.
5. **Renumber after cutting.** Drop notes by number and remap the markers in order. Every marker must appear exactly once in the body, with its notes in the same order:
```python
import re
circ='①②③④⑤⑥⑦⑧⑨⑩⑪⑫⑬⑭⑮⑯⑰⑱⑲⑳㉑㉒㉓㉔㉕㉖㉗㉘㉙㉚㉛㉜㉝㉞㉟㊱㊲㊳㊴㊵㊶㊷㊸㊹㊺㊻㊼㊽㊾㊿'
def drop(path, nums):
    body, notes = open(path).read().split('\n---\n\n**注**\n\n')
    items = notes.strip().split('\n\n')
    assert all(body.count(circ[i]) == 1 for i in range(len(items)))
    keep = [i for i in range(len(items)) if i + 1 not in nums]
    mp = {circ[i]: circ[k] for k, i in enumerate(keep)}
    body = re.sub('[' + circ + ']', lambda m: mp.get(m.group(0), ''), body)
    new = [circ[k] + items[i][1:] for k, i in enumerate(keep)]
    open(path, 'w').write(body + '\n---\n\n**注**\n\n' + '\n\n'.join(new) + '\n')
```
6. **Publish**, then export the tab and diff it against the local draft (slowfire-zh-check).
7. **Report** in a line: how many notes, what was cut beyond the author's list, and anything Qwen said that you didn't take.

The annotated print edition (slowfire-print-edition) starts from these notes. A 注释本 may add notes for a new reader, but the same calibration applies.