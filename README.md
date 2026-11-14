# Naafiri Item Calculator

A single-page build comparison tool for Naafiri in League of Legends. Pick two builds, A and B, and see how they compare ability by ability, combo by combo, and over a sustained fight.

**Live page:** https://gedissxd.github.io/naafiri-calculator/ (works once GitHub Pages is enabled for this repo: Settings → Pages → Deploy from a branch → `main` / root)

## What it shows

- **Overall showdown** – which build leads on poke, trade, burst, sustained DPS, Q healing, durability, move speed and gold cost.
- **Build totals** – attack damage, lethality, armor penetration, ability haste, move speed, health, resistances and cost.
- **Ability comparison** – one box per ability (passive, Q, W, E, R) at the selected ranks, with bars stacked by source: base damage, AD ratio and Packmates.
- **Combos** – four combos run hit by hit against the target's health, including item procs and runes:
  - Poke: Q → Q
  - Short trade: Q → E → AA → Q
  - All-in: R → AA → Q → E → AA → Q
  - Full burst: W → R → AA → Q → E → AA → Q
- **Sustained output** – damage and healing per second on effective cooldowns.

## How to use it

1. Tick items for Build A and Build B in the item table. The champion level follows the number of completed items; drag the slider to override it.
2. Choose a target. Squishy, Bruiser and Tank are rough estimates that scale with level; typing your own armor and HP switches to Custom.
3. Set runes and item toggles per build (keystone, Sudden Impact, stat shards, Hubris stacks and so on).
4. Click the rank buttons on an ability box to change its rank. Hover any bar segment for its exact value.

All damage is shown after the target's armor, so lethality and armor penetration only show their value against the target you pick.

## Data and assumptions

Numbers are from patch 26.22 (League of Legends Wiki and Data Dragon 16.22.1). Icons load from Riot's Data Dragon CDN.

The model makes a few simplifications:

- Every skillshot hits and Packmates survive the combo.
- Packmates use Naafiri's armor penetration and land a fixed number of bites per combo.
- The Call of the Pack's bonus AD is 22% of Naafiri's total AD.
- Black Cleaver and Conqueror stacks build up hit by hit within a combo, and count as fully stacked in the sustained card.
- First Strike covers the whole combo, and Voltaic Cyclosword's bonus lethality lasts for the rest of the combo.
- Packmate bites do not count toward Electrocute.

## Updating for a new patch

Everything lives in `index.html`, with no build step. The numbers to change are near the top of the `<script>` block:

- `ITEMS` – item stats, costs and Data Dragon item ids
- `ABILITIES` – Naafiri's ability values per rank
- `NAAFIRI` – her base stats and growth
- `DDV` – the Data Dragon version used for icons

Item passives and runes are applied in the `totals` and `sim` functions.

## Running locally

Open `index.html` in a browser. No server or dependencies are needed.

## Disclaimer

This project isn't endorsed by Riot Games and doesn't reflect the views or opinions of Riot Games or anyone officially involved in producing or managing Riot Games properties. League of Legends and Riot Games are trademarks or registered trademarks of Riot Games, Inc.
