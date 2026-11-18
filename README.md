# Claude writing skills

Skills for writing serious fiction with [Claude](https://claude.ai): literary novels in Chinese with science-fiction
elements, where a careful reader has to be able to trust every sentence, date and dialect line. They were built while
writing the [《阴燃 · The Slow Fire》](https://slowfire-novel.github.io/Slow-fire-novel/) series and its spin-offs, and
most of their rules come from a mistake caught in those books. Each skill is a folder with a `SKILL.md` that tells
Claude when to use it and how.

## How this differs from Oh Story

[Oh Story](https://github.com/zenstory-ai/oh-story-claudecode) is a popular skill pack for Chinese web fiction: it
scans the Qidian and Fanqie charts, takes bestsellers apart, and writes to proven tropes. If that's what you write, use
it; it's built for that. These skills aim the other way:

- **Away from the trope, not toward it.** `plot-unexpectedness` has a weaker model guess what comes next. What it
  predicts is the cliché to avoid, and every surprise has to be set up earlier in the text.
- **Checked against the real world.** Dialect lines and realism go to a second model (Qwen) as an outside reader;
  dates, clocks, ages and sums are computed in code; every real fact in a note is checked.
- **Craft from literature, not formula.** Each relationship beat is carried by a move from a named work and tested
  on the page, with 言情 and 网文 tells searched out (`serious-lit-relationships`); every simile has to come from the
  character's own world (`in-world-imagery`), and every line from that character's mouth (`character-voice`).
- **Ideas shown, never preached.** A theme becomes a question several characters answer differently
  (`story-idea-weave`), and satire is spoken by characters and built on the book's own facts (`roast-in-fiction`).
- **Ethics written in.** Real people are disguised until nobody who knows them could pick them out
  (`slowfire-real-people`); portraits never identify anyone, and faces never come from a photo.
- **Made for the finished book.** Spoiler-safe notes, figures checked numeral by numeral against the text, and an
  annotated print edition whose text is verified identical to the manuscript.

Both keep a book's continuity in files and both strip AI-sounding prose; `slowfire-zh-check`'s AI-tells and
adversarial-reader steps are adapted from Oh Story's `story-deslop` and `story-review` (MIT). The difference is what
the book is for.

**中文简介：** 一套用 Claude 写严肃文学的技能，面向带科幻设定的中文长篇，是在写《阴燃》系列的过程中一条条攒下来的。和面向起点、番茄的网文技能包
Oh Story 不同，它不追套路，而是先测出读者猜得到的套路，再避开；方言和现实细节交给另一个模型（通义千问）冷读，日期、钟点、钱数用代码算；主题交给人物去争，不让叙述去讲；真人原型改到熟人认不出；最后出的是带注释、配图、和稿子逐字一致的印刷版。

| Skill | What it does |
|---|---|
| [`photo-to-waimao`](skills/photo-to-waimao/SKILL.md) | Turns a photo of a person into a Chinese 外貌描写: concrete physical facts in order, 150–250 字 per person, ending on one cutting detail. Never names or identifies anyone, changes a detail when a look is recognisable, never sexualises, keeps anyone who looks under 18 plain. |
| [`plot-unexpectedness`](skills/plot-unexpectedness/SKILL.md) | Tests how predictable a story is. A blind, smaller model guesses what comes after each break; a second blind model looks for the setup of each surprise; Claude scores surprise and setup per beat and keeps a ledger of what readers were promised and never got. |
| [`qwen-consult`](skills/qwen-consult/SKILL.md) | Asks Qwen (chat.qwen.ai, through Claude in Chrome) for an outside read: whether something is realistic in China, whether dialect lines ring true, how new Chinese writing reads. One chat per task, Qwen's answer treated as input rather than instruction, and a log of what was taken. |

### For the 阴燃 books

These come from the workflow behind the 《阴燃》 novels and their spin-offs (《明火》《火德》《燎原》《火候》…). They
expect that setup: each book's Claude doc with a Map tab, an index doc per book under `claude/`, and the other skills here.
They work as they are for those books, and as worked examples for anyone building a similar pipeline for their own.

| Skill | What it does |
|---|---|
| [`slowfire-zh-check`](skills/slowfire-zh-check/SKILL.md) | Proofs a Chinese chapter before and after publishing: 翻译腔, AI tells (去AI味) judged in context, a cold read by Qwen as a reader who hasn't read the earlier books, adversarial readers who look only for problems, look-alike typos found by script, canon names and terms, dates and clocks computed rather than guessed, and a scripted 汉字 count. |
| [`sichuanese-dialogue`](skills/sichuanese-dialogue/SKILL.md) | Writes and checks 四川话 dialogue (Chengdu, Chongqing) against the project's own verified lexicon first, and sends Qwen only the new or doubtful lines, one batch per chapter; every settled or rejected form goes back into the lexicon ([the 火候 lexicon](skills/sichuanese-dialogue/sichuanese-lexicon.md) is included). A whole-book pass holds a finished volume to the 《海上花列传》 standard: natives speak full dialect, one spelling per word, and a 例言 at the front. |
| [`yangtze-delta-dialogue`](skills/yangtze-delta-dialogue/SKILL.md) | The same method for 上海话, 苏州话, 常熟话, 杭州话 and 南京话: knows which forms belong to which city, keeps dialect mostly in older speakers' mouths for a story set in 2048, writes standard dialect forms rather than homophone spellings, and checks only new or doubtful lines with Qwen. |
| [`serious-lit-relationships`](skills/serious-lit-relationships/SKILL.md) | Writes relationships the way serious fiction does, not 言情: each relationship beat is carried by a move from a named work (《繁花》's 不响, 王小波, 谷崎, Duras, Munro, Carver, Ernaux, Ferrante, Rooney…) with a test on the page, and 言情 and 网文 tells are searched for and fixed. |
| [`character-voice`](skills/character-voice/SKILL.md) | A voice card for each speaker, a cover test (hide the tags: could two people swap lines?), and a check for the writer's own quotable lines leaking into a character's mouth. |
| [`in-world-imagery`](skills/in-world-imagery/SKILL.md) | Audits every simile: each image must come from the point-of-view character's own trade, place or body, one a paragraph at most; the future shows in one line someone handles, never a paragraph of mechanism. |
| [`slowfire-setting-2048`](skills/slowfire-setting-2048/SKILL.md) | Sets scenes in real places checked against Chinese sources, never pins a scandal on a real business, makes each place pay off something already on the page, and shows 2048 daily life (paying, eating out, hospitals, elder care, transport) in one line anchored to a checked 2026 fact. |
| [`chapter-pace-braid`](skills/chapter-pace-braid/SKILL.md) | Plans a chapter: one real relationship event at least, four to seven braided sections under two clocks, detail spent on people rather than logistics (measured paragraph by paragraph), contrast cuts, and a last line that turns. |
| [`intimate-scenes`](skills/intimate-scenes/SKILL.md) | Sex and flirting in adult literary fiction: blended into the plot rather than set apart, something shifts between the two people every time, bodies specific and imperfect, consent shown in BDSM, blank paragraphs for a reticent partner, implicit scenes that never name the act, an outside read of the scenes by a second model, and hard limits (never minors, never anyone real). |
| [`netspeak-dialogue`](skills/netspeak-dialogue/SKILL.md) | Today's Chinese internet speech (抽象话, 东北整活) for named characters only, from a vetted lexicon, aged for a story set in 2048; real streamers appear only as quoted clips, and slurs, parent insults and mockery of the dead are out. |
| [`slowfire-chapter-notes`](skills/slowfire-chapter-notes/SKILL.md) | Writes and prunes a chapter's ①② notes: only what a reader from outside the dialect region can't get from the page, calibrated against the notes the author cut, with Qwen judging the borderline ones and a script to renumber after cuts. |
| [`huimu-couplets`](skills/huimu-couplets/SKILL.md) | Writes a 回目 couplet under each chapter title, in the manner of 《海上花》《金瓶梅》 and 张恨水: two parallel lines, the upper ending 仄 and the lower 平, one concrete image from the chapter, checked by Qwen and laid as suggestions. |
| [`slowfire-figures`](skills/slowfire-figures/SKILL.md) | Makes a chapter's figures: picks the style the book allows, draws in code so it can be redrawn, checks every numeral against the text, writes the caption, places the figure and logs it. |
| [`waimao-to-image`](skills/waimao-to-image/SKILL.md) | The reverse of `photo-to-waimao`: turns a character's 外貌描写 into a realistic figure with Qwen-Image, checks every visible detail against the text, and keeps the prompt as the character's cast entry so the face stays the same across chapters. Faces are always invented; never a real person. |
| [`slowfire-print-edition`](skills/slowfire-print-edition/SKILL.md) | Builds an A5 Chinese PDF, plain or 注释本, from a book's Claude doc: export, spoiler-safe notes, plates, pandoc and xelatex, then checks that the PDF's text matches the doc exactly. |
| [`slowfire-real-people`](skills/slowfire-real-people/SKILL.md) | Turns real people the author knows into characters nobody can pick out: keep behaviour and voice, change every identifying label, move telling details to other characters, split or merge into the existing cast, test the result, and record only the fiction. This public copy has its examples made generic; it names no characters. |
| [`story-idea-weave`](skills/story-idea-weave/SKILL.md) | Folds a new idea into a book already under way (a theme, a social issue, a character type): turns it into a question the cast answers differently, gives it to three to six characters, ties it to the plot's clock, schedules seed, turn and payoff across chapters, and keeps it shown, never preached. |
| [`plot-ledger`](skills/plot-ledger/SKILL.md) | Keeps four ledgers per book (money, who knows what and when, who is where and when, and what has already been said) and checks every new chapter against them: sums done in code, clocks and weekdays computed, knowledge leaks and teleporting objects flagged. |
| [`novel-comprehension-test`](skills/novel-comprehension-test/SKILL.md) | Tests whether a finished volume gets its characters and plots across: Qwen reads it cold, chapter by chapter, says who is who and what happened, then retells each arc; the answers are scored against an answer key written beforehand, and lost threads are fixed with the smallest change. |
| [`character-relationship-graph`](skills/character-relationship-graph/SKILL.md) | Draws a volume's 人物关系图 from the text alone: people and typed ties confirmed line by line, laid out by place, published as a self-contained interactive page, with a short report of who carries the book, who hangs by one thread and who is on none. |
| [`novel-refinement-passes`](skills/novel-refinement-passes/SKILL.md) | Eleven passes over a finished volume that need no human judge: continuity, canon, verbal tics, dialect, voices, imagery, hot and cold pacing, intimate scenes, threads, figures and the print PDF. Each finds problems by script or rule first, then judges by hand; changes to published text go in as suggestions for the author to accept. |
| [`roast-in-fiction`](skills/roast-in-fiction/SKILL.md) | Puts the [roast-anything](https://github.com/yuanrui3/AI-benchmark-for-roasting/blob/main/.claude/skills/roast-anything/SKILL.md) method in a character's mouth: 吐槽, quarrels, toasts and satirical narration built on the book's own facts, in that character's voice, where the roast changes the scene and someone answers back. |

## Using them

- **Claude Code:** copy a skill's folder into `~/.claude/skills/` (for all your projects) or into a project's
  `.claude/skills/`. Claude picks it up in the next session and uses it when a request matches its description.
- **claude.ai:** zip a skill's folder and upload it as a skill in your account's skill settings.

`qwen-consult` and `waimao-to-image` need Claude in Chrome and a signed-in Qwen account in that Chrome;
`slowfire-zh-check`, `slowfire-chapter-notes`, the two dialect skills and `novel-comprehension-test` call `qwen-consult`, and `waimao-to-image` also needs access to the
author's computer to move the image files. `plot-unexpectedness` works best where Claude can start sub-agents on a smaller model; without them it
tells you how to run the predictor by hand. `slowfire-print-edition` needs pandoc, xelatex and CJK fonts (Noto Serif
CJK SC) where it runs.
