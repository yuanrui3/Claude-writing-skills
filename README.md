# Claude writing skills

Skills for [Claude](https://claude.ai) that help with writing fiction, mostly Chinese fiction. Each one is a folder with a
`SKILL.md` that tells Claude when to use it and how.

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
| [`slowfire-zh-check`](skills/slowfire-zh-check/SKILL.md) | Proofs a Chinese chapter before and after publishing: 翻译腔, a cold read by Qwen as a reader who hasn't read the earlier books, look-alike typos found by script, canon names and terms, dates and clocks computed rather than guessed, and a scripted 汉字 count. |
| [`slowfire-chapter-notes`](skills/slowfire-chapter-notes/SKILL.md) | Writes and prunes a chapter's ①② notes: only what a reader from outside the dialect region can't get from the page, calibrated against the notes the author cut, with Qwen judging the borderline ones and a script to renumber after cuts. |
| [`slowfire-figures`](skills/slowfire-figures/SKILL.md) | Makes a chapter's figures: picks the style the book allows, draws in code so it can be redrawn, checks every numeral against the text, writes the caption, places the figure and logs it. |
| [`waimao-to-image`](skills/waimao-to-image/SKILL.md) | The reverse of `photo-to-waimao`: turns a character's 外貌描写 into a realistic figure with Qwen-Image, checks every visible detail against the text, and keeps the prompt as the character's cast entry so the face stays the same across chapters. Faces are always invented; never a real person. |
| [`slowfire-print-edition`](skills/slowfire-print-edition/SKILL.md) | Builds an A5 Chinese PDF, plain or 注释本, from a book's Claude doc: export, spoiler-safe notes, plates, pandoc and xelatex, then checks that the PDF's text matches the doc exactly. |
| [`slowfire-real-people`](skills/slowfire-real-people/SKILL.md) | Turns real people the author knows into characters nobody can pick out: keep behaviour and voice, change every identifying label, move telling details to other characters, split or merge into the existing cast, test the result, and record only the fiction. This public copy has its examples made generic; it names no characters. |
| [`story-idea-weave`](skills/story-idea-weave/SKILL.md) | Folds a new idea into a book already under way (a theme, a social issue, a character type): turns it into a question the cast answers differently, gives it to three to six characters, ties it to the plot's clock, schedules seed, turn and payoff across chapters, and keeps it shown, never preached. |
| [`plot-ledger`](skills/plot-ledger/SKILL.md) | Keeps four ledgers per book (money, who knows what and when, who is where and when, and what has already been said) and checks every new chapter against them: sums done in code, clocks and weekdays computed, knowledge leaks and teleporting objects flagged. |
| [`roast-in-fiction`](skills/roast-in-fiction/SKILL.md) | Puts the [roast-anything](https://github.com/yuanrui3/AI-benchmark-for-roasting/blob/main/.claude/skills/roast-anything/SKILL.md) method in a character's mouth: 吐槽, quarrels, toasts and satirical narration built on the book's own facts, in that character's voice, where the roast changes the scene and someone answers back. |

## Using them

- **Claude Code:** copy a skill's folder into `~/.claude/skills/` (for all your projects) or into a project's
  `.claude/skills/`. Claude picks it up in the next session and uses it when a request matches its description.
- **claude.ai:** zip a skill's folder and upload it as a skill in your account's skill settings.

`qwen-consult` and `waimao-to-image` need Claude in Chrome and a signed-in Qwen account in that Chrome;
`slowfire-zh-check` and `slowfire-chapter-notes` call `qwen-consult`, and `waimao-to-image` also needs access to the
author's computer to move the image files. `plot-unexpectedness` works best where Claude can start sub-agents on a smaller model; without them it
tells you how to run the predictor by hand. `slowfire-print-edition` needs pandoc, xelatex and CJK fonts (Noto Serif
CJK SC) where it runs.
