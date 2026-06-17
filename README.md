# The Hat of Many Languages 🎩

Have you ever noticed that programming looks suspiciously like magic?

Ancient texts filled with cryptic symbols. Arcane rules that must be followed exactly. Apprentices studying for years under more experienced practitioners. Strange arguments over which school is superior. And, every so often, an accidental catastrophe caused by a single misplaced character.

The Hat of Many Languages was created to settle a question that has troubled young wizards for generations:

**Which language should you learn first?**

Take a seat upon the sorting stool and answer seven questions. The hat will examine your ambitions, your temperament, your preferred style of problem-solving, and the kind of wizard you might become.

> Do you delight in elegant simplicity?
> Do you seek absolute control?
> Do you build towering systems meant to last centuries?
> Do you prefer swift practical solutions over elaborate rituals?

The hat listens carefully.

Then it begins to mutter.

> “Interesting…”
> “Very interesting…”
> “A curious mind…”
> “Not afraid of complexity, I see…”
> “Difficult. Very difficult…”

At last, the verdict arrives on an unfurling parchment scroll.

Perhaps you are destined to become a **Serpent Sage of Python**, crafting powerful spells with remarkable ease. Or an **Arcane Archmage of C++**, master of ancient and dangerous forces. Or an **Iron Guardian of Rust**, sworn to eliminate entire classes of magical disasters.

Whatever the result, the hat will explain its reasoning, introduce your wizarding persona, and teach you your very first incantation.

The verdict is not law.

But the hat has been doing this for a very long time.

And hats, as it turns out, remember things.

## Demo

Open `sorting-hat-languages.html` in any modern browser. No build step, no dependencies, no internet required — that's the whole thing.

## What it does

- **A themed quiz** — 7 questions about what you want to build, how you feel about strict rules, your ideal mentor, how you face bugs, and more.
- **Weighted scoring** — each answer adds points across the eight languages, so different choices genuinely lead to different results.
- **A dramatic reveal** — the hat "deliberates" with typed-out mumbles ("Hmm… curious, very curious…") before shouting *"Better be… Python!"*
- **A result scroll** — your language, a wizard persona, why it suits you, a runnable first code snippet, and the runner-up languages the hat also considered.

## Languages it sorts into

| Language   | Persona               |
|------------|-----------------------|
| Python     | the Serpent Sage      |
| JavaScript | the Web Weaver        |
| Rust       | the Iron Guardian     |
| C++        | the Arcane Archmage   |
| Java       | the Stone Architect   |
| Go         | the Swift Courier     |
| Swift      | the Crystal Artisan   |
| Ruby       | the Joyful Bard       |

The personas are for fun. The verdict is meant as a friendly nudge, not a rule — any of these is a fine first language.

## Running it

No tooling needed:

1. Download `sorting-hat-languages.html`.
2. Double-click it, or open it in your browser.

To serve it locally (optional):

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/sorting-hat-languages.html
```

## Hosting it

Because it's one static file, you can drop it on any static host — GitHub Pages, Netlify, Cloudflare Pages, or your own server. Just upload the HTML file.

## How it works

Everything lives in one file:

- **`LANGS`** — an object describing each language: display name, persona title, blurb, a "why you" line, and a first-incantation code snippet.
- **`QUESTIONS`** — an array of questions, each with four options. Every option carries a `scores` map that adds points to one or more languages.
- **Flow** — `renderIntro()` → `renderQuestion()` (looped) → `renderThinking()` (typed mumbles) → `renderResult()` (ranks scores, highest wins, top three runners-up shown as chips).

State is a simple `scores` object and a `current` question index, both held in memory. There's no persistence by design, so every play starts fresh.

## Tech

- Plain HTML, CSS, and vanilla JavaScript — no frameworks, no bundler.
- All styling via CSS custom properties; an arcane palette of candle-gold, parchment, and midnight violet.
- Respects `prefers-reduced-motion`: drifting embers and the typewriter effect are disabled for users who ask for less motion.
- Works offline.

## Accessibility notes

- Reduced-motion users skip the animations and go straight to the verdict.
- Buttons are real `<button>` elements with visible focus and hover states.
- Known gap: full keyboard-only navigation and screen-reader labeling could be improved — see CONTRIBUTING for where to help.

## Contributing

New languages, sharper questions, and accessibility fixes are all welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

Choose a license that suits you (MIT is a common, permissive choice for projects like this) and add a `LICENSE` file. Until then, all rights reserved by the author.
