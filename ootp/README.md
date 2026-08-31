# Out of the Park Baseball — Japanese amateur prospects

Real Japanese amateur players, converted to OOTP attributes. **Free, always.**

OOTP ships with NPB but not with Japanese amateurs. If you want the actual 2026 and 2027 NPB draft classes — high school, university, corporate, and independent league players — in your save, this is where they are.

---

## Files

| File | Contents |
|---|---|
| [`2026/japan-amateur-2026.csv`](2026/japan-amateur-2026.csv) | The 2026 NPB draft class, one row per player |

Per-player detail with sourcing lives in [`../players/`](../players/).

---

## Columns

| Column | Meaning |
|---|---|
| `name`, `position`, `throws`, `bats` | Identity |
| `height_in`, `weight_lb`, `dob` | Physical. `dob_verified` flags whether the birth date is primary-source confirmed |
| `velo_low_mph`, `velo_high_mph`, `velo_peak_mph` | Velocity band and peak |
| `stuff`, `movement`, `control`, `stamina` | Core pitcher ratings, current / potential, 20-80 |
| `fastball`, `slider`, `curveball`, `changeup`, `forkball` | Individual pitch ratings, 20-80 |
| `contact`, `gap`, `power`, `eye`, `avoid_k`, `speed`, `arm`, `field` | Hitter ratings, 20-80 (blank for pitchers) |
| `injury_risk` | Our read, not an OOTP field. Raise proneness manually where flagged |
| `fv` | Our overall Future Value grade |
| `evidence` | **Why the ratings are what they are** |
| `source_league` | Where the statistics came from |

---

## How the ratings are set

Ratings are derived from published statistics and velocity, not from vibes. The `evidence` column shows the reasoning for every player so you can override anything you disagree with.

Three rules we follow:

**1. Rate the arm, not the radar gun.** A pitcher touching 97 with a 7.71 K/9 does not get elite Stuff. Velocity sets the ceiling; the strikeout rate sets the current grade.

**2. Japanese radar guns run optimistic.** They are not calibrated to Statcast or TrackMan. Velocity bands here are already shaded, but consider trimming another mph if your league uses MLB-calibrated norms.

**3. Workload is a real injury signal.** Japanese high school pitchers throw complete games on short rest, in tournaments, routinely. Where a player has a documented heavy-usage pattern, `injury_risk` says so. OOTP has no import field for this — set it by hand.

---

## What is missing, and why

**No spin rates, no release points, no batted-ball profiles.** None of that exists publicly for Japanese amateur baseball, so Groundball/Flyball tendency is left Neutral rather than guessed. Personality and work-ethic ratings are left at default for the same reason.

---

## Importing

OOTP's import paths change between versions, so this is distributed as plain CSV rather than a version-locked file. Two common approaches:

- Create the players manually in the in-game editor using these values (reliable, slow)
- Use a community import tool for your OOTP version, mapping the columns above

If you build a converter for a specific OOTP version, open an issue — we will link it here.

---

## License and etiquette

[CC BY 4.0](../LICENSE). Use it in your league, stream it, build on it, sell nothing that is just this file re-hosted. Credit *Japan Prospect Lab* and link back.

**This will never be paywalled.** Roster files are shared freely in this community and that is how it should stay. If the data is useful, the way to support it is to subscribe to the (free) publication and tell someone.

Corrections welcome — open an issue with a source.
