---
name: "slowfire-figures"
description: "Make figures for a chapter of 阴燃 or a spin-off: pick the style, draw in code, check every numeral against the text, write the caption, place it in the doc and log it in the Map."
---

# Chapter figures

A chapter isn't finished until its figures are in, unless the author has said to wait (the author once had to say "you have forgotten to put figures").

## How many and which style
- 阴燃 Volumes 1–2: two figures a chapter, one style within a chapter. Volume Two picks from styles Volume One used; a new style only when the author agrees (oscilloscope art in ch32 was the one exception).
- Spin-offs follow the book's own rule; read its index doc. 《明火》: exhibit plates on cream paper, black ink, one flame red (#D9441E), gold only for 珀尔's lines, in the PDF only. 《火德》: Chinese-style figures. 《火候》 (author, 17 Nov): two a chapter. One shows a character, drawn realistically (photo-like or realistic manga, never cartoonish) with the waimao-to-image skill; the other has no people in it.
- Styles used so far: Bauhaus, cinematic realism (letterbox), impressionist, 父与子 strips, Art Deco, risograph, pop art, cubist (analytic and synthetic collage), ink wash with red seals, cyberpunk, Byrne's 1847 Euclid, cosmic, Disney-style or graphite over Parajanov colour, retro-futurist, flat editorial, Art Nouveau, pixel art, Op Art, postmodern collage, surrealist, Miyazaki-style, hand-painted animation background, oscilloscope art, vaporwave, dreamcore, steampunk.

## Rules for what's drawn
- Text-free, or numerals only.
- A style is fine; a known character, a recognisable artwork or a brand is not. No real person's face and no real public figure. Real places only as places.
- Every numeral and count in a figure must agree with the text (a Volume One figure once showed 41 after the text changed to 37). List them and check each against the chapter.
- Pick the moment the text only implies, not one it already describes in full.

## Making it
1. Draw in code (SVG or matplotlib) and keep the script, so a figure can be redrawn when the text changes (ch25 fig. 2 and ch33 fig. 1 were redrawn). A realistic figure, such as 火候's character figure, can't be drawn in code: make it with waimao-to-image and keep the prompt the same way you would keep a script.
2. Render to PNG at full size and look at it with Read before placing it. Fix what's wrong and look again.
3. Caption: one line, italic, in the narrator's voice (or the book's chosen voice: 凯's in 《明火》), in both languages when the book is bilingual. The Chinese caption goes through slowfire-zh-check.

## Placing and recording
- Upload the image to the chapter tab after the paragraph it belongs to (the docs connector's uploads guide says how), or keep it for the PDF when the book's plates live only there.
- Log the style and subject of each figure in the Map's chapter row and in the book's index doc.