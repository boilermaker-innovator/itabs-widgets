# iTabs Quotes

**Config-driven interactive quote estimators for Australian trades businesses.**

One self-contained HTML file. No build step. No dependencies. Drop it anywhere.

👉 **Live demo:** [boilermaker-innovator.github.io/itabs-quotes](https://boilermaker-innovator.github.io/itabs-quotes)

---

## What It Does

Customers tap through a simple accordion estimator, learning about their options as they go — materials, site conditions, extras. By the time they hit "Get Quote", they know what they want and roughly what it costs. The tradie gets a qualified lead with a proper spec attached, not a vague "how much for a fence?"

That's the differentiator: **customers learn while they quote.** Better leads. Fewer basic questions. Less wasted time on site visits that go nowhere.

---

## How It Works

Each estimator is a single HTML file with two parts:

1. **WIDGET_CONFIG** — a JavaScript object at the top of the file. This is the only thing you edit per trade or business. It defines the business info, branding, steps, hints, and pricing rules.
2. **Engine** — the universal rendering code below the config. Reads the config and builds everything: accordion layout, input controls, educational hints, live pricing, and lead capture form. Never touch this part.

```
WIDGET_CONFIG  ──▶  Engine  ──▶  Interactive widget
```

---

## Files in This Repo

| File | What it is |
|------|------------|
| `index.html` | Hub page — links to all estimators |
| `fencing.html` | Perth fencing estimator (Colorbond, timber, aluminium) |
| `gateworld.html` | Perth gates & automation estimator |
| `painting-generic.html` | Generic Perth painting estimator |
| `builder.html` | Visual config builder — fill a form, preview live, download the HTML |

---

## Estimator Features

### Input types
- **select** — card grid (1–3 columns) with icons, descriptions, price hints
- **multi_select** — same as select, multiple choices allowed
- **slider_group** — range sliders with value mapping (e.g. fence height 0.9m–2.4m)
- **toggle_group** — on/off switches for extras and add-ons

### Educational hints (the i-button)
Every step can have a tabbed hint panel that opens when the customer taps the ⓘ button:
- **comparison_table** — side-by-side feature comparison with colour coding
- **tips** — icon + title + text cards (Perth-specific advice, seasonal warnings, regulations)
- **mixed** — paragraphs, key points, and tips combined
- **custom_html** — anything else

### Pricing engine
Calculations run in this order:

```
base → preAdjustments → multipliers → quantity → postAdjustments → extras → minimum → rounding
```

- **base** — from the primary selection (low/high range)
- **preAdjustments** — additive modifiers before multipliers (e.g. style +$200)
- **multipliers** — from sliders (value_map) or selects (select_map)
- **quantity** — metres of fencing, number of units, etc.
- **postAdjustments** — additive modifiers after multipliers (e.g. job type -$800)
- **extras** — fixed, per-unit, or percentage add-ons from toggles
- **minimum** — price floor
- **rounding** — nearest $50, $100, etc.

Live itemised breakdown shows the customer exactly what's driving the price.

### Lead capture
- Configurable form fields (name, phone, email, address, message)
- Delivered by [Web3Forms](https://web3forms.com) (free plan — no customer confirmation email)
- Full quote summary included in every submission

### Branding
- Full colour theming via CSS variables in the config
- Custom Google Fonts
- Dark mode default, light mode supported
- Configurable border radius, glow effects, social proof bar

---

## Working Examples

### Fencing — per-metre pricing
3 steps: fence type → dimensions (sliders) → extras (toggles). Height multiplier from slider value map. Colorbond, timber, aluminium, pool fencing. Perth coastal and soil condition tips.

### Gateworld — per-unit pricing
10 steps: all select-based. Pre-adjustments for style and colour. Multipliers for height, width, slope, and property type. Post-adjustments for job type (motor-only vs full supply). Social proof bar enabled.

### Painting — per-room/area pricing
5 steps: scope → home size → wall condition → paint quality → extras. Select_map multipliers for realistic price combinations. Perth-specific tips on heat, prep, and product selection.

---

## Building Your Own

### Option 1: Use the builder
Open `builder.html` in your browser. Fill in the form on the left, watch the live preview on the right. Hit "Download Widget" when you're happy.

### Option 2: Copy and edit a config
Open any `.html` file. Edit the `WIDGET_CONFIG` object at the top — business info, branding colours, steps, hints, pricing. Everything below the config is the engine — leave it alone.

### Option 3: Use the AI skill
This repo includes a `SKILL.md` file. Paste it into Claude or another AI and describe the trade you want to build. The AI will generate a complete `WIDGET_CONFIG` ready to drop into a blank engine file.

---

## Deployment

These are static HTML files. They work on:
- GitHub Pages (what this repo uses)
- Any web host
- Embedded in an iframe on an existing website
- Saved locally and opened in a browser

No server. No database. No installation.

---

## Tech Stack

- Vanilla HTML/CSS/JS — zero dependencies, zero build step
- [Web3Forms](https://web3forms.com) — lead delivery
- [GitHub Pages](https://pages.github.com) — hosting
- Australian dollar formatting via `toLocaleString('en-AU')`

---

## What's Coming

- Shareable quote output — a link or summary the customer can send to any tradie
- More trade estimators (paving, electrical, plumbing)
- Embeddable web component version

---

Built with [iTabs](https://itabs.ai) · Tools that turn browsers into buyers
