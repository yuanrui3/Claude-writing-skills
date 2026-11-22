---
name: "pianwen-yinlv-check"
description: "Check a 骈赋's 平仄 and 平水韵: map rhyme runs, find 仄/平 clusters, same-tone pair endings, 重韵 and -m/-n breaks; weigh outside 音律 reviews with Gemini, then quiz the author."
---

# 音律 check for a 骈赋

Use this when the author asks about rhyme, 平仄, 顺口 or 音律, or brings an outside 音律 review (for example from his own Codex project). The author holds to strict 平水韵. Underlined text is locked, and images are his (see pianwen-fu-writing).

## What to check
1. **Rhyme map.** For each paragraph, list the characters at strong pauses (；。：and paragraph end) with their 平水韵 部. A run should hold one 部 or change 韵 cleanly at a turn.
   - In 赋, 邻韵通押 among the -n groups (真文元寒删先) is acceptable.
   - The -ng groups (东冬江阳庚青蒸) stay apart from -n.
   - The -m groups (侵覃盐咸) do not mix with -n. Example: 衔 (十五咸) inside a 元 run is a real break. The author chose to keep 独木相衔 anyway.
2. **重韵.** The same character rhyming twice in one run is a fault. Example: 拉丁之后人 with 殆谓斯人 in the same paragraph; fixed with 拉丁之民.
3. **Paired clause endings.** In a 对句, the first clause should end 仄 and the second 平 at a rhyme. Two 平 endings flatten the pair (非采者所遗，实举手莫及其芳: 遗 and 芳 both 平).
4. **Tone clusters.** Flag four or more 仄 (or 平) in a row:
   - 灶火既举，竟日不熄 is eight 仄; fixed with 终日.
   - 八月晦、九月朔 is eight 仄; fixed with 之晦、之朔.
   - 不笑亦若笑 is five 仄; fixed with 不笑亦如笑.

   Count 入声 as 仄 even where Mandarin reads it 平 (一 七 八 十 石 白 竹 国 节 不 …).
5. **Polyphones.** Take the reading by the sense here, both for tone and for 注音:
   - 望: 平 (阳) or 去 (漾).
   - 汤汤: shāng.
   - 处 in the sense 居处: 上声.
   - 斓: 广韵 落干切 (寒). 集韵 has a second reading, so check before ruling it off-rhyme.
6. **Punctuation conventions.**
   - 领语 (于是、尔乃、若夫) run straight on without a comma, as in 哀江南赋 于是桂林颠覆.
   - A colon implies whole-to-parts. Example: 倍于前月： would make the snowplows part of 嬉雪之乐.

## Fixing without breaking meaning
A 音律 fix may change only sound. Test every fix against the sentence's image list (pianwen-fu-writing). Bad fixes seen:
- 众目不移 for 观者无一人目移. It loses the 观者/闻者 echo and the 无一人. The original already alternates 平仄 syllable by syllable.
- 案上笔齐. It breaks the 领无…案无… pair that 行不…言不… answers.
- 每讲皆至. It reads like a tally and loses her never missing a talk.
- 不笑如含笑. It turns a born upturn of the mouth into a deliberate smile.
- 灯灭 for 灭灯. He no longer turns it off; the lamp just goes out.
- 趋前 for 趋步. It makes three 平 pauses in a row and loses the echo of 步履轻扬. A comma after 趋步 did the job instead.

Prefer, in order:
1. Punctuation.
2. Adding or dropping an empty word (之、而、则).
3. A synonym with the needed tone that keeps the image.
4. Reordering clauses.

## Working with an outside review
1. Send Gemini the review and the current text (underlines marked 〖〗) as attachments. Ask it to:
   - verify every 韵部 and 平仄 claim (甲);
   - rule on each suggestion: agree, disagree, or a better fix, with reasons (乙);
   - add up to five problems the review missed (丙).
2. Check the factual disputes yourself; WebSearch or a dictionary for readings. Never assert a contested reading as settled. Say "probable" if you couldn't open the 平水韵 table.
3. Sort the results for the author into four groups:
   - factual errors in the review;
   - misses;
   - edits that fall in locked text;
   - matters of judgment.
4. **Quiz:**
   - single-select for rhyme choices (keep / fix A / fix B);
   - multiSelect for small fixes;
   - a separate multiSelect for review suggestions that Gemini and Claude would turn down.

   He may take those; apply them.
5. Apply and hash-verify in the doc, rebuild the PDF, and log in the record doc.

## Quick reference
- **Rhyme runs seen in 《拉法叶赋》:** 七阳, 五歌, 四支, 八庚, 一先, 十一真, 十三元, 十四寒, 十二侵, 五微, 六鱼, and 上声六语 (仄韵).
- **Turns into a 仄 short sentence** inside a run (过城未远而西折, 倍于前月) are normal 赋 pauses, not faults.