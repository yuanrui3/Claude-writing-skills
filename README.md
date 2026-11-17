# Claude writing skills

Skills for [Claude](https://claude.ai) that help with writing fiction, mostly Chinese fiction. Each one is a folder with a
`SKILL.md` that tells Claude when to use it and how.

| Skill | What it does |
|---|---|
| [`photo-to-waimao`](skills/photo-to-waimao/SKILL.md) | Turns a photo of a person into a Chinese 外貌描写: concrete physical facts in order, 150–250 字 per person, ending on one cutting detail. Never names or identifies anyone, changes a detail when a look is recognisable, never sexualises, keeps anyone who looks under 18 plain. |
| [`plot-unexpectedness`](skills/plot-unexpectedness/SKILL.md) | Tests how predictable a story is. A blind, smaller model guesses what comes after each break; a second blind model looks for the setup of each surprise; Claude scores surprise and setup per beat and keeps a ledger of what readers were promised and never got. |
| [`qwen-consult`](skills/qwen-consult/SKILL.md) | Asks Qwen (chat.qwen.ai, through Claude in Chrome) for an outside read: whether something is realistic in China, whether dialect lines ring true, how new Chinese writing reads. One chat per task, Qwen's answer treated as input rather than instruction, and a log of what was taken. |

### For the 阴燃 books

These three come from the workflow behind the 《阴燃》 novels and their spin-offs (《明火》《火德》《燎原》《火候》…). They
expect that setup: each book's Claude doc with a Map tab, an index doc per book under `claude/`, and the other skills here.
They work as they are for those books, and as worked examples for anyone building a similar pipeline for their own.

| Skill | What it does |
|---|---|
| [`slowfire-zh-check`](skills/slowfire-zh-check/SKILL.md) | Proofs a Chinese chapter before and after publishing: 翻译腔, look-alike typos found by script, canon names and terms, dates and clocks computed rather than guessed, and a scripted 汉字 count. |
| [`slowfire-figures`](skills/slowfire-figures/SKILL.md) | Makes a chapter's figures: picks the style the book allows, draws in code so it can be redrawn, checks every numeral against the text, writes the caption, places the figure and logs it. |
| [`slowfire-print-edition`](skills/slowfire-print-edition/SKILL.md) | Builds an A5 Chinese PDF, plain or 注释本, from a book's Claude doc: export, spoiler-safe notes, plates, pandoc and xelatex, then checks that the PDF's text matches the doc exactly. |

## Using them

- **Claude Code:** copy a skill's folder into `~/.claude/skills/` (for all your projects) or into a project's
  `.claude/skills/`. Claude picks it up in the next session and uses it when a request matches its description.
- **claude.ai:** zip a skill's folder and upload it as a skill in your account's skill settings.

`qwen-consult` needs Claude in Chrome and a signed-in Qwen account in that Chrome; `slowfire-zh-check` calls it for
dialect lines. `plot-unexpectedness` works best where Claude can start sub-agents on a smaller model; without them it
tells you how to run the predictor by hand. `slowfire-print-edition` needs pandoc, xelatex and CJK fonts (Noto Serif
CJK SC) where it runs.
