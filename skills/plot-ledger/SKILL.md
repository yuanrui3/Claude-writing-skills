---
name: "plot-ledger"
description: "Keep a novel's money, information (who knows what, when), logistics (who is where, clocks, objects) and memory (callbacks, ages, promises) coherent: build ledgers from the text and check every new chapter against them."
---

# Plot ledgers

Readers forgive a strange world; they don't forgive a sum that doesn't add up, a secret a character couldn't know, or a man in two cities at once. Keep four ledgers per book and check every new or edited chapter against them before it goes to the author.

## The four ledgers

Keep them as tables in the book's Map (or a Ledger section of it), one row per fact, each with the chapter and paragraph it comes from.

1. **Money.** Every price, wage, fee, deposit, debt and payout: amount, currency, who pays whom, for what, when.
   - Run the arithmetic in code: units × price = total; tables × seats = guests; hours × rate = pay.
   - Check scale against the world's year and place (2048 prices, US vs China wages). Note who can afford what they do.
   - Follow the money: who profits from each event. It often shows a motive the text has left implicit.
2. **Intel.** A matrix: fact × character → when and how they learned it (saw, told, overheard, guessed), and whether they know the other knows.
   - Nobody acts on what they don't know. A secret spreads only through a channel shown on the page.
   - Record deliberate dramatic irony, so it isn't "fixed" by accident.
   - Example: Wen knows of Mei's test (found it in the trash, ch3); Lin doesn't. 蒲嬢嬢 told 老蒲 about the hug (ch1). 冉峥's mother knows nothing.
3. **Logistics.** Who is where at each section heading.
   - Clocks: compute both cities' times in code (火候: Chengdu = Lafayette + 13 h in February). Headings never run backwards.
   - Weekdays and festivals: compute with datetime and lunardate, never by hand.
   - Travel times, weather, daylight.
   - Objects: holder and place (the test stick, 老罗's key, a wristband).
   - Bodies: injuries, pregnancy week, who is asleep in a rented body.
4. **Memory.** What has already been said, so later chapters can call back and nothing contradicts.
   - Ages and birth years.
   - Promises and claims made in dialogue ("四十年，他问过我三回想吃啥子").
   - Names characters use for each other; recurring lines; what the narrator has already explained (don't explain twice).

## Workflow

1. **Build.** Extract candidate rows with scripts: grep numbers with units (元, 块, 美元, $, 公斤, 岁), clock headings, names and objects. Then read the text to confirm each row. Start from the Map's canon list.
2. **Check a chapter.** List every fact it adds or uses. Diff the list against the ledgers. Flag:
   - sums that don't add up;
   - timeline slips (weekday, age, clock);
   - knowledge leaks (acting on, or mentioning, what the character wasn't told);
   - objects that teleport;
   - a character at two places;
   - a figure numeral that disagrees with the text.
3. **Fix the smaller side.** Usually the new text gives way. When canon itself is wrong, say so and let the author decide. Use the smallest edit, and verify the publish.
4. **Optional outside check.** Give a fresh sub-agent (or Qwen) only the text so far and ask "who knows X?", "how much did Y pay?" Where its answer differs from the ledger, the page doesn't carry what the ledger claims: add a line, or accept the ambiguity on purpose.

## Known slips

- Qwen miscounts weekdays and ages.
- Ages drift against birth years across volumes.
- Per-unit price × count ≠ the total quoted.
- A time-zone offset applied in the wrong direction.
- Someone quotes a conversation they weren't in.
- A secret everyone suddenly knows.
- A figure shows 41 after the text changed to 37.

## Report

Update the ledgers the same day. Tell the author only the conflicts found and how each was fixed, one line each.