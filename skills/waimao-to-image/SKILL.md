---
name: "waimao-to-image"
description: "Turn a character's 外貌描写 from 阴燃 or a spin-off into a realistic figure (photo-like or realistic manga, never cartoonish) with Qwen-Image in the author's Chrome, checked against the text and placed in the chapter."
---

# 外貌描写 to image

This is the inverse of photo-to-waimao: the words come first, and the picture has to agree with them. Use it when a chapter needs its character figure, or when the author wants to see what someone looks like. In 火候 every chapter has two figures, and one of them shows a character (author, 17 Nov).

## Style
- **Realistic.** Either a cinematic still with a photographic feel, or realistic manga (剧画: inked lines, screentone, seinen proportions). Never chibi, cute anime, 3D cartoon or caricature. The author's words: like a real person, not too cartoonish.
- **One look per chapter.** Choose one look for the chapter and keep both figures in it unless the author says otherwise.
- **No text.** No words, signs or logos anywhere in the image. Numerals only where the scene needs them, and they must match the chapter.

## Hard rules
- **Faces are invented.** The prompt is built only from the fictional 外貌描写, written after masking (slowfire-real-people). Never use a real person's name, a look-alike, or a photo of a real person, the author's prototypes included.
- **Nothing borrowed.** No real public figure, no known character, no brand, no recognisable artwork. Real places appear only as places.
- **Never sexualise.** Characters in sex threads are drawn clothed, in ordinary moments.
- **Children** appear only in plain, clothed, everyday scenes, never near a sexual thread. Draw them through clothes and action, with no attention to attractiveness.
- **No ethnic caricature.** Skin, features and hair exactly as the text gives them.

## Building the prompt
1. **Collect the portrait** from the chapter or the Map's portraits: age, build, face, hair, hands, clothes, and the cutting detail. Add place, season and weather from the Map. For 火候: a Chengdu winter is about 10 °C, overcast and seldom raining; Lafayette is 0–2 °C with snow.
2. **Pick the moment** the text only implies (slowfire-figures).
3. **List the visible details that must match.** For 老蒲: the left eyebrow gone, forearms thicker than calves with white burn scars, glasses pushed up on the forehead, a blue gas flame.
4. **Write the prompt in Chinese**, in this order:
   - the style line: “写实电影剧照，真实摄影质感，绝对不要卡通” or “写实漫画（剧画），黑白墨线加网点，不要Q版、不要萌系”;
   - the person, built from the portrait's facts;
   - the setting and the light;
   - always last: “画面中不要出现任何文字、招牌字或商标”.

## Generating with Qwen-Image (Chrome)
- **Chat.** Use one chat on chat.qwen.ai for the book's figures. Record its URL in the book's index doc and reuse it; it is separate from the book's review chat.
- **Settings.** Click “+”, then Create Image. Keep the model Qwen-Image and set the aspect, usually 3:2.
- **Send.** Put the prompt in with the textarea setter (qwen-consult) and click send. Generation takes about a minute.
- **Full size.** The chat shows a copy resized by an `x-oss-process` URL parameter. The same URL without that parameter gives the full image, 2528×1696 at 3:2. Fetch it inside the page.
- **Check every listed detail** with a zoomed screenshot. If one is wrong, regenerate with the fix stated plainly, up to three tries; after that, tell the author what is still off.
- **Watermark.** Qwen stamps a small “Qwen” mark in the bottom-right corner. Crop it off by keeping the top-left 94% of the width and height, which keeps the aspect.

## Getting it into the doc
The shell can't reach Qwen's CDN, and the image URL is signed: never work around the browser tool's redaction of tokens. The file travels through the author's computer instead.
1. **Ask once per batch** for permission to download, naming the files, the source (Qwen) and their size.
2. **Save from the page.** Draw the cropped image on a canvas 1600 px wide and export a JPEG at quality 0.85. Save it with an `<a download>` click named `<book>_chNN_figN.jpg`; it lands in the author's Downloads folder.
3. **Bring it into the workspace.** Request access to Downloads once (device_request_folder_access), then use device_stage_files. Copy the file into `/home/claude/<book>/figs/` and look at it with Read.
4. **Place it.** Run upload_asset on the doc's artifact, create a blob from the asset id, and insert `![alt](blob/<id>)` with a one-line italic caption after the paragraph it belongs to (docs uploads guide). The caption goes through slowfire-zh-check.
5. **Log it** in the Map's chapter row and the index doc: the style, the subject, and the prompt itself, so the figure can be redrawn when the text changes.

## Cast sheet
Once the author accepts a character's face, keep its prompt in the index doc as that character's cast entry. Reuse the same wording for every later figure of that character, so the face stays recognisably the same across chapters.