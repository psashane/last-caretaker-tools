# The Last Caretaker — Tools Project

## What This Is
A set of tools to help optimize human-growing in The Last Caretaker's Lazarus Complex system. The player (Shane) grows humans from seeds using memory items and food, then launches them into orbit. The goal is to fill committee slots with specific profession types while conserving scarce memory items.

## The Game System

### Growing Humans
Humans are grown in a Lazarus Pod using two input types:
- **Memory items** — physical objects found in the world. Each contributes specific **mental traits** (Empathy, Communication, Patience, Discipline, Leadership, Adaptability, Creativity, Focus, Logic, Wisdom). These are **finite and scarce** — they are consumed on use and cannot be farmed infinitely.
- **Food items** — crafted from farmable bio-materials. Each contributes **physical stats** (Height, Weight, Life Expectancy, Strength, Intellect). Food is **effectively unlimited** — the crafting ingredients can be farmed indefinitely, so food quantity is never a constraint.

### Professions
There are 40 professions across 10 categories (Engineering, Arts & Culture, Educators, Agriculture, Logistics, Military, Science, Healthcare, Leadership, Explorer). Each has 4 tiers (T1–T4) with increasing stat requirements.

When a human finishes growing, the game picks a profession from **all qualifying professions**, favoring the **highest tier match per category**. This means:
- You can accidentally qualify for a higher-tier profession than intended if you overshoot traits
- Each profession checks a mix of physical stats (food) and mental traits (memory items)
- The optimization goal is to hit the target profession's thresholds with minimum memory items, without triggering unwanted higher-tier professions

### Committees
Committees are groups of exactly 4 specific profession roles that must all be filled by separately grown humans. The player needs to grow one human per committee slot. Committee membership drives the late-game goal. Example: "Transit & Distribution" needs a Systems Engineer, Distributor, Growth Specialist, and Guard.

## Key Optimization Rules
1. **Minimize memory items used** — they are the scarce resource
2. **Food is free** — optimize food for the physical stat profile needed, don't worry about quantity
3. **Avoid higher-tier contamination** — don't overshoot mental traits into T3/T4 thresholds if targeting T1/T2
4. **Check side effects** — every memory item contributes traits beyond the target; verify those don't accidentally qualify for unwanted professions
5. **Cross-category contamination** — a recipe optimized for Logistics might accidentally qualify the human for a Military or Science role; check all categories

## Data Files
- `memories.json` — all 34 memory items and their per-item trait values (verified against wiki)
- `food.json` — all 13 food items and their per-item physical stat values
- `professions.json` — all 40 professions with tier and minimum stat requirements
- `committees.json` — known committee compositions (incomplete, add as discovered)
- `inventory.json` — Shane's current memory item quantities (update as items are used)

## Verified Totals (as of 2026-05-26)
With the inventory in `inventory.json`, the mental trait totals match thelastcaretaker-tools.com exactly:
- Empathy: 1309, Communication: 1376, Patience: 1321, Discipline: 1241
- Leadership: 1372, Adaptability: 1617, Creativity: 1240, Focus: 1248
- Logic: 1504, Wisdom: 1447

## Example Optimization — Distributor
Target: Height≥160, Discipline≥12, Focus≥15, Logic≥10

Memory recipe (6 items — not yet used in-game):
- 1× Sudoku Book (Logic: 10)
- 2× Plans (Discipline: 14)
- 3× Where's Tommy (Focus: 15)

Food recipe (not yet finalized):
- 3× Ultimate Genesis (Height: 150) + 1 additional item to reach ≥160
- Keep Intellect below Lab Technician threshold (80) to avoid Science contamination

## Reference
- Wiki: https://thelastcaretaker.wiki.gg (returns 403 on automated fetches — must be accessed manually)
- Community calculator: https://thelastcaretaker-tools.com/Calculator
