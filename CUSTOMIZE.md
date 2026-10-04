# Customizing Closet

Everything lives in **one file: `index.html`**. Open it in a plain text editor (VS Code is free and great). Use **Find** (Cmd+F or Ctrl+F) to jump to the text in **bold** below. The line numbers are approximate and shift as you edit.

After any edit: **save, then refresh** the page in your browser to see it. When it looks right, upload `index.html` to GitHub again (see README).

> Tip: keep a copy of the working file before big edits, so you can always go back.

---

## 1. Colors and the wallpaper

Find **`1. THEME`** near the top. Each color is one line: a name and a hex code like `#9E4527`. Change the hex code and that color changes everywhere. Pick new colors at https://coolors.co.

| Name | What it colors |
|---|---|
| `--bg` | The base color under the wallpaper |
| `--surface` | Pop-ups, inputs and solid cards |
| `--glass` | The frosted panels that float over the wallpaper (the last number is how see-through they are, from 0 to 1) |
| `--tile` / `--tile-hi` | The sand-colored arch frames behind your clothes (edge and center) |
| `--ink` | Main text (espresso brown) |
| `--muted` | Secondary text |
| `--line` / `--line-strong` | Hairlines and outlines |
| `--accent` | Deep burnt terracotta: buttons, selected chips |
| `--accent-2` | Slightly lighter terracotta |
| `--accent-deep` | Darkest terracotta: page titles, hover on buttons |
| `--accent-soft` | Pale clay: the selected menu item, tips |
| `--gold` | Gold details: piece counts, sparkles, frame lines |
| `--ok` | Sage green for the "Wear" stamp |

**For an even darker terracotta,** try `--accent:#8A3B21` and `--accent-deep:#5F2615`.

**The wallpaper** is a light stone-grey marble with white clouding and soft grey veins, built from three layers on the line that starts with **`body{height:100%`**:

- `--stone` is the marble veins. Change `center/1600px` to a bigger number (like `2400px`) for larger, calmer veins, or a smaller one for more detail. To remove the marble, delete `var(--stone) center/1600px,` from the body line.
- `--base` is the stone-grey gradient under the marble. Change its two hex codes to make it lighter (for example `#F2F0EE` and `#E6E3DF`) or darker.

**How much the white boxes stand out** is set by `--glass` (the last number, `.95`, is how solid the boxes are) and `--shadow` (the lift under each box). Find **`white boxes lift off the marble`** for the outline and shadow rules.
- `--glow` is the very soft terracotta light in the top corner. Raise `.05` to make it warmer, or delete `var(--glow),` from the body line to remove it.

The blocks that start with **`@media (prefers-color-scheme: dark)`** and **`:root[data-theme="dark"]`** hold the **dark mode** colors. They use the same names, so edit them the same way.

**Shapes:** `--arch` is the arch shape of the clothing frames. Change it to `14px` for plain rounded rectangles. `--r` is the corner rounding of small boxes, and `--r-lg` is the rounding of cards and pop-ups.

### Color themes

Six themes come built in: Terracotta, Olive grove, Espresso, Bordeaux, Navy and brass, and Sage. Switch between them in the app under **Colors, backup and settings** at the bottom of the sidebar. The choice is remembered on that device.

To change a theme's colors, find **`COLOR THEMES`** in `index.html`. Each theme is one line, for example:

```
:root[data-palette="olive"]{--accent:#566236;--accent-2:#6B7944;--accent-deep:#3A4222;--accent-soft:#E9ECDE;...}
```

Edit the hex codes there. The lines inside the `@media (prefers-color-scheme: dark)` block just below are the same themes for dark mode.

To add your own theme:

1. Copy one of those lines and change the name in quotes (for example `"plum"`) and the colors.
2. Find **`const PALETTES=[`** in the script and add a matching line with the same key, a name, a short note, and three preview colors.

## 2. Fonts

The site uses **Cormorant Garamond** (elegant italic headlines) and **Jost** (clean, refined text).

1. Pick fonts at https://fonts.google.com, click **Get font**, then **Get embed code**, and copy the `<link href="...">` line.
2. Replace the line near the top that contains **`fonts.googleapis.com/css2`** with yours.
3. Find **`--serif:`** and **`--sans:`** and put your font names first. For example, `--sans:'Quicksand',system-ui,sans-serif;` brings back the rounder, cuter text.

**Text size:** find **`body{height:100%`** and change `15px`.

**Headline size:** find **`.title{`** and change `font-size:64px`.

**Button shape:** find **`.btn{`**. `border-radius:var(--pill)` makes them fully round. Change it to `10px` for softer rectangles.

## 3. Add a clothing style (around line 387)

Find **`2. WARDROBE CATALOG`**. Each type (Outerwear, Tops, Shoes and so on) has a list of styles, and each style is one line:

```
['puffer','Puffer jacket',1.5,5,'sporty street','waterproof'],
```

| Part | Meaning |
|---|---|
| `'puffer'` | A short unique key, lowercase with dashes, no spaces |
| `'Puffer jacket'` | The name you see |
| `1.5` | Dressiness from 1 (lounge) to 5 (black tie) |
| `5` | Warmth from 0 (none) to 5 (heavy winter) |
| `'sporty street'` | Moods, separated by spaces: minimal, classic, romantic, edgy, sporty, boho, preppy, street, glam, cozy |
| `'waterproof'` | Special flags, separated by spaces (see below), or `''` for none |

**Flags the stylist understands:** `waterproof`, `denim`, `knit`, `athletic`, `bare` (needs a layer when cool), `short` (short hem), `long`, `sneakers`, `heels`, `boots`, `open` (open toe), `bag`, `belt`, `scarf`, `jewelry`, `eyewear`, `sun` (good in sun), `cold` (good in cold), `warm-metal` (gold), `cool-metal` (silver).

To add a style, copy a similar line, paste it right below, and change the parts. Keep the comma at the end.

## 4. Occasions (around line 455)

Find **`const OCCASIONS`**. Each occasion is one line:

- `label` is the button text, and `p` is how it reads in a sentence ("for a networking event").
- `f` is how dressy it is, from 1 to 5.
- `vib` lists the moods that suit it (a positive number) or don't (a negative number).
- `prefer` and `avoid` are lists of style keys from section 3 that get a boost or a penalty.

To add one, copy a line, give it a new `k` (key) and `label`, and adjust the rest. It appears as a new button automatically.

**"Something else"** reads what you type. To teach it new words, find **`function resolveOcc`** and add words to the matching line. For example, add `|picnic` to the casual line.

## 5. How the stylist thinks (around line 489)

Find **`const WEIGHTS`**. Each number is how much one rule matters. Raise a number to make that rule count more, lower it to make it count less, or set it to `0` to switch the rule off.

| Weight | Controls |
|---|---|
| `formality` | Matching dressiness to the occasion |
| `weather` | Warm enough, cool enough, rain and snow |
| `color` | Color harmony between pieces |
| `pattern` | Pattern mixing rules |
| `vibe` | Pieces sharing a mood |
| `occasionVibe` | Moods that suit the occasion |
| `silhouette` | Balancing loose and fitted pieces |
| `profile` | Following your Inspiration board |
| `learned` | Following what you liked and passed on |
| `variety` | Avoiding the same pieces again and again |
| `pin` | Matching a pin's colors when you tap "Recreate this look" |
| `formulas` | The outfit formulas in section 6 |
| `randomness` | Surprise. Raise it for more variety, lower it for "best match" every time |

## 6. Outfit formulas and clashes (around line 883)

Find **`const FORMULAS`**. Each line is a combination that works, with a bonus and the reason shown on the outfit card:

```
{need:['blazer','tee|long-sleeve|turtleneck','straight|wide-jeans|skinny'],v:.6,t:'Blazer, simple top and jeans is a smart-casual classic'},
```

Each item in `need` must be in the outfit, and `|` means "any of these". `v` is the bonus. A few formulas also have a `cond` that limits them to certain weather.

Find **`const CLASHES`** right below it. These are combinations to avoid: if a piece from `a` and a piece from `b` are both in the outfit, it gets the penalty `v`.

Add your own rules the same way, using the style keys from section 3.

## 7. Color names (around line 474)

Find **`const COLORS=[`**. Each color family has a name, a hex code, and a `1` if it counts as a neutral. The scanner uses these to name the colors it finds, and the closet uses them for the color filter.

## 8. Moods that go together (around line 447)

Find **`const VIBE_PAIRS`**. Each pair has a number from 0 (they never mix) to 1 (perfect together). For example, `'sporty-glam':.1` means sporty and glam rarely work.

## 9. The mannequin

Find **`const MQ={`**. Each line says where a type of clothing sits on the mannequin, as `[left, top, width, height]` on a figure that is 240 wide and 560 tall (the head is at the top, the feet at about 520). For example, `'wool-coat':[50,84,140,392]` makes wool coats start at the shoulders and reach below the knee. Make the last number bigger for longer pieces, or the third number bigger for wider ones. You can add a line for any style key from section 3.

The figure itself is the drawing in **`const FIGURE_SVG`**. Its colors come from `--surface` (the body) and `--line-strong` (the outline and stand).

## 10. Planner, journal and closet gaps

- **How much the week avoids repeats:** find **`if(ctx.planUse)`**. The second list (`top:-2.5, dress:-2.5, bottom:-1 ...`) is for My week. More negative means less repetition.
- **How much a trip reuses pieces:** in the same line, the first list is for trips. Positive numbers (`bottom:.5, shoes:.7, outer:.7`) encourage reusing them, so you pack less.
- **How long before an outfit can repeat:** find **`S.wornKeys`**. The `10` is the number of days a worn outfit is avoided.
- **When a piece counts as forgotten:** find **`x.d>=30`** in the journal and change `30` days.
- **Closet gap rules:** find **`function closetGaps`**. Each `add(...)` line is one suggestion with its reason, written in plain words you can edit.

---

## Quick reference

| I want to change… | Find this |
|---|---|
| A color | `1. THEME` |
| A color theme | `COLOR THEMES` and `const PALETTES` |
| The wallpaper | `--stone`, `--base`, `--glow` and `body{height:100%` |
| Arch frames | `--arch` |
| Dark mode colors | `prefers-color-scheme: dark` |
| Fonts | `fonts.googleapis.com/css2`, `--serif:`, `--sans:` |
| Corner roundness | `--r:` and `--r-lg:` |
| Text size | `body{height:100%` |
| Add a style of clothing | `2. WARDROBE CATALOG` |
| Add an occasion | `const OCCASIONS` |
| How strict the stylist is | `const WEIGHTS` |
| Outfit formulas | `const FORMULAS` |
| Combinations to avoid | `const CLASHES` |
| The feedback options | `const FEEDBACK` |
| Where clothes sit on the mannequin | `const MQ={` |
| Planner repeats and trip reuse | `if(ctx.planUse)` |
| Closet gap suggestions | `function closetGaps` |
| The app name | `<title>` near the top, and `'Closet'` in `class:'brand'` |
