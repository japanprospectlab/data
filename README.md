# Japan Prospect Lab — Open Data

Structured data on Japanese amateur baseball prospects, in English.

Japanese amateur baseball produces hundreds of professional players every year, and a handful of them eventually reach MLB — Shohei Ohtani, Yoshinobu Yamamoto, Roki Sasaki and Yusei Kikuchi were all amateurs in Japan first. Almost none of that pipeline is documented in English.

This repository is the data layer. The written analysis lives at **[Japan Prospect Lab](https://japanprospectlab.substack.com)**.

---

## What's here

| Directory | Contents |
|---|---|
| [`players/`](players/) | One directory per player: game logs, profile, OOTP conversion |
| [`ootp/`](ootp/) | Out of the Park Baseball roster data. Free, always |
| [`boards/`](boards/) | Ranked prospect boards with 20-80 grades |
| [`reference/`](reference/) | League level equivalencies, unit conversions, school name mappings |

Start with [`reference/league-levels.csv`](reference/league-levels.csv) if you have never tried to place Japanese amateur baseball on a scale you recognize.

---

## Coverage

- **High school** — Koshien and the prefectural tournaments
- **University** — Tokyo Big6, Tohto, and the regional leagues
- **Corporate leagues** (*shakaijin*) — company teams, the Intercity Tournament
- **Independent leagues** — Shikoku Island League plus, BC League, Kyushu Asia League
- **NPB farm clubs** — Oisix Niigata, Hayate Shizuoka

That last pair of categories is the part nobody else covers in English. You can watch Koshien on television. Almost no one is systematically tracking a 21-year-old right-hander in the Shikoku Island League who is throwing 94 and might be an NPB draft pick in two years.

---

## How to read the data

Every game-log row carries a `verified` column:

| Value | Meaning |
|---|---|
| `verified` | Confirmed against tournament records and/or two or more independent outlets |
| `partial` | Event confirmed, but some stat fields were never published. **Empty cells are empty, not zero** |
| `reported` | Single secondary source only, could not be corroborated. **Excluded from every aggregate** |

Velocities appear in both km/h (as published in Japan) and mph. Heights and weights appear in both metric and imperial. Anything estimated rather than published carries an `_est` suffix and an explanation.

Full rules: **[METHODOLOGY.md](METHODOLOGY.md)**

---

## What is NOT here

**No spin rates, no release points, no batted-ball data.** None of it exists publicly for Japanese amateur baseball. Anyone publishing those numbers is inventing them.

---

## Caveats

- Japanese amateur baseball has **no single official statistical database**. Coverage is incomplete by nature, and always will be.
- Japanese stadium radar guns are **not calibrated to MLB Statcast** and tend to run optimistic relative to TrackMan. Shade velocity down a mph or two when comparing to MLB data.
- **Scouting grades are Japan Prospect Lab's own evaluation.** They are not sourced from any MLB or NPB organization.
- Level equivalencies in `reference/` are **judgment calls, not measurements.** They carry an explicit confidence rating.

---

## Eligibility, in one paragraph

**Japanese amateurs are not eligible for the MLB draft.** They enter the NPB draft, held every October. Players reach MLB later through the posting system (with their club's consent) or through international free agency after nine years of NPB service. A small but growing number now skip the NPB draft entirely and sign directly with MLB organizations as international amateurs — Shotaro Morii did it out of high school in 2025.

---

## License

**[CC BY 4.0](LICENSE)** — use it for anything, including commercially. Just credit *Japan Prospect Lab* and link back.

---

## Contributing

Corrections are welcome. Open an issue **with a source**. Accuracy matters more here than volume, and a documented correction is worth more than a new row.
