# Changelog

Corrections are committed separately from new data, with the source in the commit message, so the revision history shows what changed and why.

---

## 2026-09-04 — NPB to MLB posting board

**Added**

- `boards/posting-board.csv` — NPB players tracked by how and when they could reach MLB. 18-column schema; two completed moves included as reference rows for the likelihood scale
- `boards/POSTING-ELIGIBILITY.md` — the four routes out of NPB, the posting calendar, the marginal release fee schedule with a worked example, and how first-team service days are counted. Includes why the fee schedule, not sentiment, explains club reluctance to post players under 25

**Known gaps**

- The board carries two reference rows only. Active rows are added as the November posting window approaches.
- No MLB equivalency is applied to NPB statistics. No current, rigorous, published conversion exists that this project will stand behind.

---

## 2026-08-30 — Initial release

**Added**

- `players/shoki-oda/` — Shoki Oda (Yokohama HS, RHP). 12-row 2026 game log, profile, OOTP conversion
- `reference/league-levels.csv` — level equivalencies for 12 Japanese leagues and categories, with confidence ratings
- `reference/unit-conversions.csv` — conversion constants and the measurement caveats that go with them
- `reference/schools.csv` — school name mappings with notable MLB and NPB alumni
- `ootp/2026/japan-amateur-2026.csv` — OOTP attribute conversions for the 2026 class
- `boards/2026-npb-draft-board.csv` — ranked prospect board
- `METHODOLOGY.md` — source hierarchy, verification rules, unit conversion, grading scale

**Known gaps**

- The board and the OOTP file contain one player. Both grow as reports publish.
- Several Shoki Oda summer stat lines are `partial` — hits, walks and strikeouts were never published for those appearances. Cells are left empty rather than estimated.
- Three summer appearances are `reported` (single secondary source) and are excluded from all totals.
- Shoki Oda's date of birth is `reported`, not primary-source confirmed.

**Scheduled**

- Update within 24 hours of the NPB draft, 2026-10-22.
