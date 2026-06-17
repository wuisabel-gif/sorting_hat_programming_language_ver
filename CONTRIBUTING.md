# Contributing to The Hat of Many Languages

Thanks for wanting to help the hat get wiser. This is a small, single-file project, which keeps contributing pleasantly simple. This guide explains how to set up, the kinds of changes that are welcome, and how to make sure your edits don't break the ceremony.

## Setup

There's nothing to install.

1. Fork and clone the repo.
2. Open `sorting-hat-languages.html` directly in a browser, or serve it locally:
   ```bash
   python3 -m http.server 8000
   # http://localhost:8000/sorting-hat-languages.html
   ```
3. Edit the file, refresh the browser, repeat.

All the HTML, CSS, and JavaScript live in that one file. The logic worth knowing sits in the `<script>` block near the bottom.

## Ways to contribute

### Add a new language

This is the most common contribution. Two steps:

1. **Add an entry to `LANGS`.** Follow the existing shape exactly:

   ```js
   kotlin: {
     name: "Kotlin",
     title: "the Modern Smith",          // a wizard-flavored persona
     blurb: "Two or three sentences...", // friendly, in the hat's voice
     why: "One line: what kind of person lands here.",
     spell: '// your first incantation\nfun main() { println("Hello!") }'
   },
   ```

   Notes:
   - The object key (`kotlin`) is the internal id. Use lowercase, no spaces.
   - `spell` is rendered verbatim in a code block. Use `\n` for line breaks and keep it short — a few lines that actually run.
   - Keep `blurb` in the same warm, in-character tone as the others.

2. **Give it a path to victory.** A language can only win if questions award it points. Add it to the `scores` maps of a few `QUESTIONS` options so it's reachable. A language that appears in `LANGS` but never scores can never be chosen — that's the most common mistake.

### Improve or add questions

Each question in `QUESTIONS` looks like:

```js
{ q: "Your question text?", opts: [
  { t: "Option label", s: { python: 2, ruby: 1 } },
  // ...four options total
]},
```

Guidelines:
- Keep **four options** per question. The rune labels (A–D) assume four.
- Point values are relative; 1 is a light lean, 2–3 is a strong signal. Don't overthink the exact numbers.
- Aim for balance: across all questions, every language should be able to accumulate a winning total. If you add heavy weight to one language, check that the others still have routes.
- Write options as genuine, distinct choices — not obviously "right" answers.

### Tune the mumbles

The `MUMBLES` array is the typed-out deliberation. Keep them short, in the hat's theatrical voice, and the last one should feel like a moment of decision.

### Visual and accessibility work

Styling is all CSS custom properties in the `:root` block — change colors and fonts there rather than hunting through rules. Especially welcome:

- Better keyboard navigation (arrow keys between options, Enter to select).
- ARIA roles / live regions so screen readers announce questions and the verdict.
- Anything that improves the experience under `prefers-reduced-motion`.

## Testing your changes by hand

There's no test suite, so please verify in the browser before opening a PR:

- [ ] The intro screen loads and "Place the hat upon your head" starts the quiz.
- [ ] All questions render, and clicking an option advances to the next.
- [ ] The progress pips update as you go.
- [ ] The deliberation types out, then a result appears.
- [ ] **Each language you added or touched can actually be reached** — answer toward it and confirm it can win.
- [ ] Any new `spell` snippet displays correctly (no broken indentation, special characters escaped).
- [ ] "Sort me again" and "Back to the start" both work.
- [ ] Toggle reduced motion in your OS settings and confirm the flow still reaches a verdict.
- [ ] Check a narrow (mobile) width — the layout should still hold together.

## Style and conventions

- Keep it dependency-free and single-file. Please don't add a build step, framework, or external libraries — the zero-setup nature is the point.
- Match the existing code style: 2-space indentation, `const`/`let`, small focused functions.
- Keep copy in the hat's warm, slightly grand voice. Friendly, never gatekeeping — every language here is a good first choice.
- Any user-supplied or snippet text rendered into HTML should go through `escapeHtml` (as the spells already do).

## Submitting a pull request

1. Create a branch: `git checkout -b add-kotlin`.
2. Make your change in `sorting-hat-languages.html`.
3. Run through the manual checklist above.
4. Open a PR describing what you changed and why. If it's a new language, mention which questions you adjusted to make it reachable. A screenshot of the new result scroll is a nice touch.

## Questions and ideas

Open an issue to propose a language, a question rewrite, or a feature before building something large — it saves everyone time. Small, self-contained PRs are easiest to review and merge.

Happy sorting. 🎩
