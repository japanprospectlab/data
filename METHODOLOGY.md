# Methodology

How the data in this repository is collected, verified, converted, and labeled.

---

## 1. Source hierarchy

Sources are used in this order. A lower tier is never used to overrule a higher one.

| Tier | Source | Examples |
|---|---|---|
| 1 | **Official league data** | `npb.jp/bis/` (NPB and farm), `bc-l-data.jp` (BC League), `data.iblj.co.jp` (Shikoku Island League), university league sites |
| 2 | **Tournament records** | Koshien and prefectural tournament official records |
| 3 | **National newspapers and broadcasters** | Nikkan Sports, Sponichi, Kanaloco, NHK, Chunichi Sports |
| 4 | **Pitch-by-pitch aggregators** | Ikkyu Sokuho (omyutech) — useful for game-level detail, **not comprehensive** |
| 5 | **Secondary aggregators / draft blogs** | Used only to locate a lead. **Never the sole basis for a published figure without a `reported` tag** |

**Tier 4 is not comprehensive.** Pitch-by-pitch aggregators do not collect every game. Where a tier-1 official source and a tier-4 aggregator disagree on season totals, the official source wins and the discrepancy is noted.

---

## 2. Verification

Every game-log row is tagged.

| Tag | Rule |
|---|---|
| `verified` | Confirmed against a tier 1–2 source, or two or more independent tier-3 outlets |
| `partial` | The appearance is confirmed but some stat fields were never published anywhere. Those cells are left **empty**, never zero, never estimated |
| `reported` | A single tier 4–5 source only. Kept in the file for completeness, **excluded from every aggregate** |

### The ERA check

**Every earned run average is recomputed as `ER × 9 ÷ IP` and compared against the published figure.** If they disagree, the published innings total is usually wrong, and the official source is used instead.

This check has caught real errors. One example from the Japanese-language archive: a draft-report site listed 77 innings with 37 earned runs and a 4.16 ERA. `37 × 9 ÷ 77 = 4.33`, not 4.16. The official league total was 80 innings, which produces exactly 4.16. The site had dropped a game.

### Cross-checking biographical data

Birth years and hometowns frequently disagree between sources. When they do, the claim is checked against the **Japanese school-year cohort**: a player's high school entry year fixes his birth window to April 2 – April 1. A stated birth date that puts him in the wrong grade for a documented tournament appearance is wrong, whatever the source says.

Any date of birth that could not be confirmed against a primary source is labeled `REPORTED` in the data.

---

## 3. Unit conversion

| From | To | Constant |
|---|---|---|
| km/h | mph | **÷ 1.609** |
| cm | inches | ÷ 2.54 |
| kg | lbs | × 2.205 |
| metres (long toss) | feet | × 3.281 |
| 50 m dash | 60-yard dash | **approximate only** — 60 yards is 54.86 m, and the standing-start conventions differ. Any 60-yard figure derived this way is labeled as an estimate |

### Radar gun calibration

Japanese stadium radar guns are **not** calibrated to MLB Statcast or TrackMan and generally read optimistic. Readings are reported as published, converted honestly, and flagged. A Koshien velocity record should be read as a *Koshien-gun* record.

---

## 4. Estimated values

Estimates always carry an `_est` suffix and an explanation in the file.

### Batters faced

**Batters faced is not published for Japanese amateur baseball.** K% and BB% therefore cannot be computed exactly. Where they appear, BF is approximated as:

```
BF ≈ (IP × 3) + H + BB
```

This ignores hit batsmen and reached-on-error, so true rates are marginally lower than the estimates shown. **Ratios per nine innings (K/9, BB/9, H/9, WHIP, ERA) are exact** and should be preferred when precision matters.

---

## 5. Measurement methods that do not transfer

Some Japanese figures look like familiar MLB metrics but are not measured the same way. **Do not compare them directly.**

| Japanese figure | Looks like | Why it is not |
|---|---|---|
| 二塁送球タイム (throw-to-second time) | MLB **pop time** | Japanese timing is frequently measured **from release**, not from the catcher receiving the pitch. A reported 1.75 would beat the MLB record if it were a true pop time — it is not |
| 一塁到達タイム (time to first) | MLB home-to-first | Usually comparable, but the start point is not always documented |
| 遠投 (long toss distance) | — | No MLB equivalent. Reported in metres and feet, not converted to arm strength |

Where these appear in the data, the measurement caveat travels with them.

---

## 6. Scouting grades

Grades use the standard **20-80 scale**, present/future.

| Grade | Meaning | Starter fastball velocity |
|---|---|---|
| 80 | Elite | 99+ mph |
| 70 | Plus-plus | 96–98 |
| 60 | Plus | 94–95 |
| 55 | Above average | 93 |
| 50 | **MLB average** | 91–92 |
| 45 | Below average | 89–90 |
| 40 | Well below | 87–88 |

**Future Value (FV):** 35+ / 40 / 40+ / 45 / 45+ / 50 / 55 / 60 / 70.
50 FV is an average MLB regular or a number 3 starter. 45 FV is a number 4–5 starter, a reliever, or a second-division regular.

### The distance discount

A Japanese amateur is typically **a decade from MLB relevance** — NPB draft, several years of development, then posting or free agency. FV grades here are discounted one step relative to an equivalent US prospect to reflect that gap and the attrition that comes with it. A player who signs directly with an MLB organization is graded without the discount, because the path shortens dramatically.

**These grades are Japan Prospect Lab's own evaluation and are not sourced from any MLB or NPB organization.**

---

## 7. Level equivalencies

The values in [`reference/league-levels.csv`](reference/league-levels.csv) are **judgment calls, not measurements.** No public translation study exists for most of these leagues, and the ones that do exist cover NPB's top division only.

Each row carries a `confidence` rating (`high` / `medium` / `low`) and a `basis` note explaining what the estimate rests on. Treat `low` confidence rows as starting points for argument, not as facts.

---

## 8. Corrections

Every correction is committed **separately** from new data, with the source in the commit message, so the revision history shows what changed and why.

Open an issue with a source if you find an error. A documented correction is worth more here than a new row.
