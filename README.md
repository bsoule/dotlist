# Dot Lists

A tiny demo of Mark Forster's [Final Version (FV)](https://markforster.squarespace.com/) todo system — in our family we call it a "dot list."

The whole app is a single `index.html`. View Source on the running page and you've read the entire codebase. Save the file, edit it, open it in a browser — that's your fork.

## Try it

Open `index.html` directly in any browser (no server needed) or serve the folder:

```
python3 -m http.server
```

…and visit `http://localhost:8000/`.

State persists in `localStorage`. Hit **Reset** to wipe and reload the demo tasks.

## The algorithm in five lines

1. The topmost active task is dotted — call it the **benchmark**.
2. Walk the list. For each task, ask: *do I want to do this more than the benchmark?* If yes, dot it — it's the new benchmark. If no, skip.
3. When you reach the bottom, work the dotted tasks **in reverse dot-order**.
4. **Done** crosses a task off. **Started, not done** crosses it off and re-adds it at the bottom.
5. When the chain is empty, the next un-actioned task becomes the new anchor. Repeat.

## Embed it

GitHub Pages serves the file directly. Drop it into a blog post with:

```html
<iframe src="https://<you>.github.io/dotlist/" width="100%" height="600" style="border:0"></iframe>
```

## Hack it

Some easy modifications, ranked roughly by effort:

- Change the demo seed (top of `<script>`, `DEMO_SEED`).
- Tweak colors (`#d4691e` is the dot color; search-and-replace).
- Change the prompt phrasing ("Do you want to do X more than Y?" lives in `renderPrompt`).
- Add a "due today" filter, multi-list support, drag-to-reorder, etc.
