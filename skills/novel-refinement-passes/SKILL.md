---
name: "novel-refinement-passes"
description: "Run the no-human-judge refinement passes on a finished 阴燃 volume or spin-off: continuity, tics, dialect, voices, imagery, 冷热 pacing, intimate scenes, threads, figures, print."
---

# Refinement passes for a finished volume

Use when a volume is drafted and the author wants it refined without a human reader ("what can you do without a human judge", "perform these"). Each pass finds problems by script or rule first, then judges by hand. Most passes end with few or no changes; that is a result, not a failure.

## Ground rules
- Read the book's index doc and Map first. Check whether the author still enforces a word cap (火候 dropped it on 17 Nov); if not, never cut to meet one.
- Rewording of existing text goes in as suggestion cards, one card per line, in a single docs batch. Exact fixes (a fact, a count, a name) and new content are plain edits.
- Quote only the changed words in a card's find; check each find is unique in the local draft first.
- After every write, verify: plain edits by the ack's block h (first 8 hex of sha256 of the plain text); cards by a view read with sinceRev one below the ack's rev, comparing the inserted block's h.
- Local drafts lag the doc whenever the author accepts cards or edits by hand; carry accepted cards into the draft before using it as the source of anything.
- Log every pass in a dated pass log doc in the project (what was checked, what changed, what was left and why).

## The passes, in order
1. **Continuity:** clock headings never run backwards (two clocks, fixed offset); lunar dates by lunardate; running numbers (latency, seat counts, money) only move one way; objects consistent (keys, strings, scars).
2. **Canon:** grep every name and term from the name list; a name appearing once where it should appear many times is a typo.
3. **Tics:** count 像, 很久, 看了一眼, 没答, 看了一会儿, 半天, 过了一会儿, 没说话 per chapter; cut where the next action carries the beat; keep refrains that are deliberate (list them in the log).
4. **Dialect:** the sichuanese-dialogue skill's whole-book pass.
5. **Voices:** scan dialogue for aphorism shapes (X是X，Y是Y; 不是…是…; 是…出来的，不是…出来的); a line that reads like a poster is the writer's 金句 in a character's mouth. Check net-speak stays with its licensed speakers and register rules hold (e.g. 铁子's 嗷 at most once a line).
6. **Imagery:** extract every 像 simile with chapter and section; each must come from the POV character's world. Repeats are fine when they are callbacks to the same person or object; flag stock images and near-duplicates for different people.
7. **Pacing and 冷热:** every chapter ends on a hook or held image; one real relationship event per chapter; heat (stove, bed, quarrel) alternates with cold (cold store, snow, ICU, death). A climax run may stay hot if it carries cold insets.
8. **Intimate scenes** (scenes no outside reader saw): the intimate-scenes checklist (a shift, imperfect bodies, an object or joke in the room, an aftermath line, implicit acts unnamed, positions varied). Script every underlined section and list any child named in it, then read each hit: no child may be present in a sex section in any form, including on a TV screen or in the same section before or after. Fix by object swap or a new time heading. Write a scene log table (chapter, pair, position, what shifts, aftermath, protection).
9. **Threads:** grep each payoff in the next volume's brief for its seed; add threads the text seeds but the brief lacks.
10. **Figures:** no text in drawn figures; every count a figure shows (rows, tables, burners, objects) checked against the text. Redraw by editing the figure script, re-render, look at it, upload the asset, create a blob, replace the media block with guards, update the alt text and the figure log.
11. **Print PDF:** only after the open cards are decided, so it prints final text verified against the doc (slowfire-print-edition).

## Reporting
Tell the author per pass in one line: what was checked, what changed (cards or edits), what was deliberately kept, and any decision that is theirs.