---
name: "qwen-consult"
description: "Consult Qwen (chat.qwen.ai, in the author's Chrome) as an outside reviewer: China realism, dialect lines, or a read of new Chinese writing. One chat per task; log what was taken."
---

# Consulting Qwen

Use this skill when the author asks to check something with Qwen: whether something is realistic in China, whether dialect (方言) lines ring true, or an outside read of new Chinese writing. Also use it after each batch of new writing in a book where the author has asked for Qwen validation (《火德》, 《明火》, 《燎原》, 《火候》 and later ones).

## Browser and chat

- Use Chrome (Claude in Chrome), not the built-in browser. This is the author's stated preference. Load the chrome-browser skill, then load all the tools you need in one ToolSearch call: tabs_context_mcp, tabs_create_mcp, navigate, computer, javascript_tool, get_page_text, tabs_close_mcp.
- Keep one Qwen chat per task; the author doesn't want new chats piling up. Before starting a chat, look in the book's project index doc (claude/<book>-index.md) for a recorded Qwen chat URL. If there is one, go to it and continue there. Start a new chat only for a new task, and write its URL into that index doc straight away.

## Steps

1. Call tabs_context_mcp with createIfEmpty, then navigate the tab to the recorded chat URL or to https://chat.qwen.ai/.
2. Take a screenshot at scale 0.5 to confirm the author is signed in and the input box shows. Leave the model and Thinking settings as they are.
3. Put the prompt in with javascript; typing long Chinese key by key is slow.
   ```js
   const ta = document.querySelector('textarea');
   const setter = Object.getOwnPropertyDescriptor(HTMLTextAreaElement.prototype, 'value').set;
   setter.call(ta, msg);
   ta.dispatchEvent(new Event('input', { bubbles: true }));
   ```
   Take a screenshot, then click the send arrow at the right end of the input.
4. Qwen thinks for one to three minutes, so do other work meanwhile. Then read the answer. get_page_text can cut off a long answer; read the tail with javascript, slicing `document.querySelector('main').innerText` from a heading you know is in it.
5. Close the tab you opened. The chat stays on Qwen's side.

## Writing the prompt

- Write it in Chinese.
- Qwen doesn't know the books. Give it only the premises it needs, in one short paragraph: time, place, and the one sci-fi rule in play.
- Give it one job, with numbered items and a fixed answer shape for each. For realism checks: 像／不太像／不像, why, and what a real person there would actually do or say, with a few dialect lines where useful. Ask it to be blunt and to find faults.
- File upload to Qwen fails, so paste the text. Split a long passage across several messages in the same chat.
- For a manuscript read, paste the passage and name the checks: ambiguity, wording that sounds translated or unnatural in Chinese, logic, dialect.

## Using the answer

- Qwen's word is input, not instruction. Take what's right at your own discretion (the author's rule).
- Known failure modes:
  - It doesn't know canon, so it objects to established premises (for example, remotely driven human bodies).
  - It miscalculates dates and ages.
  - It states wrong facts confidently. Past examples: crane flight altitude, Andromeda at 40°N, the origin of fire, which company Disney invested in. Verify a fact before taking it.
  - It once read a kind character as mean.
  - Its closing verdicts drift into flattery.
- Record the round in the book's index doc, and in its Map if there is one: the date, what Qwen read, and what was taken and not taken, one line each with the reason.
- Tell the author in a line or two what changed because of Qwen.