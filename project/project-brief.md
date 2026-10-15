# Project 1, Part 4: Positioned Components

**Lecture 8 · Positioning + Layout Thinking**
**Lab time:** 35 minutes in class · **Due:** before Lecture 9
**You need:** your Project 1 folder with tokens in `styles.css` from Lecture 7

---

## 1. What you are doing

Add three positioned components and **name the containing block** for each one:

| Component | Where | Pattern |
|---|---|---|
| Sticky header | Your Project 1 site, every page | `position: sticky` + `top: 0` |
| Badge | A card on your Courses page, e.g. "New" | Card `relative`, badge `absolute` |
| Modal overlay | Practice page only (`modal-practice.html`) | `position: fixed` + `inset: 0` |

**The rule for today:** before you fix any positioning bug, say which element is the containing block, and check it with `$0.offsetParent` in the Console.

## 2. Where things are in this repo

```
project/
├── project-brief.md            ← this file
└── starter/
    ├── positioning-starter.css ← paste at the BOTTOM of your styles.css
    ├── modal-practice.html     ← the modal overlay, on its own page
    └── containing-blocks.md    ← homework: name each containing block
exercises/
└── broken-components/          ← 4 broken components + bug-log.md
```

Every starter value uses the Lecture 7 tokens. If your tokens have different names, rename them, don't type numbers.

## 3. Lab tasks

| Time | Step | Done when | Checkpoint |
|---|---|---|---|
| 50–55 | **Predict flow.** Inspect your Courses page. Which elements are block, which are inline? | You can say why the footer moves when a paragraph grows | |
| 55–65 | **Sticky header.** Paste `positioning-starter.css`. Add `class="site-header"` to the `<header>` on **all** pages. | The header stays at the top while you scroll, above the content | ✋ Scroll a long page |
| 65–75 | **Badge.** Add a badge inside one course card: `<span class="badge">New</span>`. Give the card `class="card"`. | The badge sits in the card's corner, not the page corner | ✋ Run `$0.offsetParent` on the badge |
| 75–80 | **Modal.** Copy `modal-practice.html` into your project and open it. | A dark layer covers the screen, with a box in the middle | |
| 80–85 | **Phone check.** DevTools → device toolbar → 375px wide. | Header, badge and modal still work | ✋ Show all three at 375px |

### The five position values

| `position` | Stays in flow? | Placed relative to |
|---|---|---|
| `static` | Yes | Nothing. Offsets are ignored. |
| `relative` | Yes | Its own normal spot. Creates a containing block. |
| `absolute` | No | Its containing block: the nearest ancestor that isn't `static` |
| `fixed` | No | The viewport (the screen) |
| `sticky` | Yes, until it sticks | Normal flow, then sticks at its `top` value |

## 4. Debugging exercise: four broken components

Each folder in `exercises/broken-components/` has one bug. Open each with Live Server. **Find why before fixing.**

| Folder | Symptom | Look at |
|---|---|---|
| `1-modal` | Appears behind the page content, whatever `z-index` you give it | Its parents |
| `2-badge` | Flies to the top-right corner of the page, not the card | Its ancestors |
| `3-navbar` | `position: sticky` is set, but it scrolls away | Its CSS and its ancestors |
| `4-floating-button` | Fine on desktop, off-screen on a phone | Device emulation at 375px |

Log each bug in `exercises/broken-components/bug-log.md`. The homework needs at least one complete entry.

## 5. Stuck? Debug positioning in this order

1. **Which element is positioned?** Computed pane → `position`.
2. **Find its containing block.** Walk up the ancestors: the first one that isn't `static`. Check with `$0.offsetParent` in the Console.
3. **Check the offsets.** `top`, `right`, `bottom`, `left` are measured from that block.
4. **Check the stacking context.** Is it in the same context as the thing it should cover? A parent with `z-index`, `opacity` below 1, or a `transform` creates a new one.
5. **Change one thing.** Then re-check at 375px.

Never fix a badge with a value like `top: -137px`. It only looks right on your screen.

## 6. Definition of done

- [ ] The header is sticky with `top: 0` on every page and stays above content while scrolling
- [ ] A badge sits in the corner of a card, with `position: relative` on the card
- [ ] `modal-practice.html` shows a full-screen overlay with a centred box
- [ ] All three still work at 375px wide
- [ ] Every value comes from a token; no magic numbers
- [ ] `containing-blocks.md` names the containing block for each component, with a reason
- [ ] At least one complete bug-log entry from the four broken components
- [ ] Every page still validates with zero errors

## 7. AI check (optional)

Ask: *"Before suggesting any fix, tell me which element is the containing block for .badge, and why."*
Then select the badge in Elements and type `$0.offsetParent` in the Console. Same answer? The reasoning holds. Different? Trust the browser.

## 8. What to submit

1. Your Project 1 folder, zipped, with the sticky header and badge
2. `containing-blocks.md`, filled in
3. `bug-log.md` with at least one complete entry

## 9. How it is marked (15 marks)

| Area | Marks | Full marks means |
|---|---|---|
| Sticky header | 3 | Sticks on every page, stays above content |
| Badge | 3 | In the card's corner; card is the containing block |
| Modal practice page | 2 | Covers the whole screen; box centred |
| Phone width | 2 | All three work at 375px |
| Containing-block explanation | 3 | Correct block named for each, with a reason |
| Bug log | 2 | Evidence column filled from DevTools, not guessed |
