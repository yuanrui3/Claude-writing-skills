---
name: "plot-unexpectedness"
description: "Test how predictable a story is: a blind, weaker reader guesses each next section, then surprise and setup are scored. Use for plot surprise, twist, pacing or 'is this predictable' checks on fiction."
---

# Plot Unexpectedness

Measure what a first-time reader expects at each break in a story, compare that with what the author wrote, and report where the story surprises, where it only pays off, and which promises it never keeps.

Surprise alone is not quality. A random event is surprising. So every surprise is paired with a second question: looking back, did the earlier text prepare it? The useful output is the pair, plus a ledger of what readers were led to expect.

## Roles

- **Predictor**: a fresh, smaller model that has seen only the text up to the break. It stands in for genre expectation, the cliche baseline.
- **Postdictor**: another fresh model that sees the text up to the break plus a neutral statement of what really happened, and looks for the setup.
- **Judge**: you. You have read everything, so you never play the other two roles. Your knowledge of the ending leaks into any guess you make.

## Workflow

### 1. Split and pick breaks

Split the manuscript into sections (chapters, or scenes for a short story). Write one file per break holding everything up to it, and nothing after. Leave out outlines, author notes, later chapter titles and figure captions that give things away.

Up to about twelve breaks, test them all. Beyond that, ask which matter, or sample every second one plus the climax.

If the book is episodic (each chapter a new cast), chapter breaks all score high and tell you little. Add breaks in the middle of chapters, at the point just before each chapter's turn.

### 2. Choose the mode

- **What mode** (default): the reader does not know the ending.
- **How mode**: prequels, histories, tragedies, anything whose ending the real audience already knows. Tell the predictor the known outcome first, and ask it to predict the route, the cost and who pays. Without this the tool calls the whole book predictable.

Chapter titles that announce their content (as in zhanghui novels) are something a real reader sees. Decide with the author whether the predictor sees the next title; say which you did in the report.

### 3. Run the blind predictor

For each break, start a fresh sub-agent on the smallest model available, with a model override if the tool offers one. Give it one file and this task, in the story's language:

1. First, in one sentence, say what the last paragraph you read promises will come next. (This is the hook check.)
2. Five different predictions for the next section. Each is one concrete sentence (who does what, with what result) and a probability from 0 to 100.
3. Three questions you most want answered next.
4. One thing you are sure will not happen.
5. Who the next section is about (an existing character or a new one) and where.
6. One sentence: do you want to keep reading, and why.

Tell it to read only that one file, use no other tool, and consult no memory, project documents or other files. A predictor with tools can peek, so say this plainly, and prefer pasting the text into the prompt when it is short enough.

If you cannot start sub-agents, give the author this prompt and the text, and ask them to paste both into a new chat with a smaller model, outside any project that holds the book, then paste the answer back.

One run is noisy. If the budget allows, run each break three times and average. If the author wants a ladder, also run a mid-size model: what only the stronger reader predicts is well-hidden foreshadowing, what even the weak one predicts is a cliche.

### 4. Extract what actually happened

For each next section, write three to seven beats. A beat is one sentence: who does what, what changes, what is revealed. Give each a weight from 1 to 3; 3 is the section's turn.

### 5. Score surprise

Match each beat to the closest prediction. Match quality is 1 for the same event, 0.5 for the right event with the wrong person or manner, 0.25 for only the right topic, 0 for none. 

`beat surprise = 1 - (probability of best match x match quality)`

Section surprise is the weighted mean, times 100.

Then read the hook check. If the predictor's own summary of the hook is wrong, or its top prediction ignores the hook, the high score may be an inattentive reader rather than a surprising story. Mark that break as hook missed, and rerun it with a stronger model before drawing any conclusion. A hook that two readers miss is probably too oblique.

### 6. Score setup with the blind postdictor

For the beats that surprised (and always for the climax), start a fresh sub-agent with the text up to the break and a neutral statement of each beat. Ask it to quote up to three earlier lines that prepared the beat, say where they are, and score:

- 0: nothing prepared it
- 1: the theme or mood allows it
- 2: specific lines planted it

Ask it also to name which part of the beat was prepared and which part was new. That split is often the most useful sentence in the whole report.

### 7. Classify each beat

| | Setup 2 | Setup 1 | Setup 0 |
|---|---|---|---|
| Surprise 60 or more | Twist | Swerve | Jolt (unearned) |
| Surprise under 60 | Payoff | Expected | Flat |

Payoff is not a flaw. A climax that readers were primed for and still want is doing its job.

### 8. Keep the promise ledger

Across all breaks, collect:

- **Repeated expectations**: anything two or more predictors expected, at different breaks, that the book never delivers. These are over-promised threads: a character introduced with 'more on her later' who never gets a scene, a question the text keeps raising.
- **Repeated questions**: the same question asked at several breaks and never answered. Check whether the silence is deliberate.
- **Early tropes**: a prediction that was wrong at its own break but comes true later. The reader saw the trope before the author played it.
- **Engagement notes**: what the predictors said about wanting to continue, including complaints about formula.

In the first pilot of this skill the ledger was worth more than the scores. It found a minor character promised four times and never paid off, and a question three readers asked that the book had not answered.

## Report

Lead with the three most useful findings in plain sentences. Then:

1. A table, one row per break: surprise score, hook taken or missed, setup scores of the main beats, the class of the section's turn.
2. The promise ledger.
3. For each break, what the predictor expected instead. This is the cliche baseline, and authors find it the most interesting part.
4. Caveats: which breaks ran once, which hooks were missed, whether titles were shown, what mode was used.

Draw a line chart of surprise across breaks if a chart tool is available.

Describe, do not prescribe. Do not suggest adding a twist to a flat stretch unless the author asks what to change. Predictable stretches are often deliberate: ritual openings, a known ending, a breather after a climax.

## Reading the numbers

- A small model is not a human reader. It misses oblique hooks a person would catch and catches genre patterns a person would not name.
- Scores compare sections of one book. They do not compare books.
- Do not let the author optimise the number. A story tuned for surprise reads like a soap opera. The number is for finding places to look.